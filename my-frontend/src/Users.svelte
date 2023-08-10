<script>
    import { onMount } from 'svelte';
    // import { request } from 'graphql-request';  // Assuming you are using graphql-request library
    import { request, gql } from 'graphql-request';
  
    let users = [];
    let error = null;
  
    // Variables for the GraphQL query
    let page = 10;  // Number of users to retrieve
    let pageSize = 0;  // Start index for retrieval
  
    const fetchUsers = async () => {
      const GET_USERS_QUERY = `
      query ($page: Int, $pageSize: Int, $username: String) {
          Users(pagination: {page: $page, pageSize: $pageSize}, filter: {username: $username}) {
            data {
                id
                username
                companies {
                    id
                    name
                    rooms {
                        id
                        name
                    }
                }
            }
                meta {
                    pagination {
                    page
                    pageSize
                    totalOfPage
                    totalOfRecord
                    }
                }
            }
        }
      `;
  
      try {
        const variables = { page, pageSize };
        const data = await request('YOUR_BACKEND_GRAPHQL_ENDPOINT', GET_USERS_QUERY, variables);
        console.log(users)
        users = data.users;
      } catch (err) {
        error = err.message;
      }
    };
  
    onMount(fetchUsers);
  </script>