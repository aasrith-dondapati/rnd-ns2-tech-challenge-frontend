<script>
    import { onMount } from 'svelte';
    import { ApolloClient, InMemoryCache, gql, HttpLink } from '@apollo/client/core';
    import AddUser from './AddUser.svelte';
    
  
    const client = new ApolloClient({
      link: new HttpLink({
        uri: 'https://rnd-ns2-tech-challenge-next-be.vercel.app/api/graphql', // Your GraphQL server URL
      }),
      cache: new InMemoryCache(),
    });
  
    const GET_USERS = gql`
      query GetUsers($page: Int, $pageSize: Int, $username: String) {
        Users(pagination: { page: $page, pageSize: $pageSize }, filter: { username: $username }) {
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
  
    let page = 2;
    let pageSize = 20; // Adjust the page size as needed
    let username = '';
  
    let loading = false;
    let error = null;
    let users = [];
  
    async function fetchUsers() {
      loading = true;
      try {
        const { data } = await client.query({
          query: GET_USERS,
          variables: {
            page,
            pageSize,
            username,
          },
        });
        users = data.Users.data;
      } catch (e) {
        error = e;
      } finally {
        loading = false;
      }
    }
  
    onMount(fetchUsers);
  </script>
  
  {#if loading}
    <p>Loading...</p>
  {:else if error}
    <p>Error: {error.message}</p>
  {:else}
    <div>
      <h2>Users List</h2>
      <ul>
        {#each users as user (user.id)}
          <li>
            <h3>{user.username}</h3>
            <h4>username</h4>
            <ul>
              <!-- {#each user.companies as company (company.id)}
                <li>
                  {company.name}
                  <h4>Rooms:</h4>
                  <ul>
                    {#each company.rooms as room (room.id)}
                      <li>{room.name}</li>
                    {/each}
                  </ul>
                </li>
              {/each} -->
            </ul>
          </li>
        {/each}
      </ul>
    </div>
  {/if}
  