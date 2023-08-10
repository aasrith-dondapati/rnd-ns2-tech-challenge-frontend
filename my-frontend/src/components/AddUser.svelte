<script>
    import { request } from 'graphql-request';  // Assuming you are using the graphql-request library
  
    let username = 'New User';
    let feedback = '';
  
    const createUser = async () => {
      const CREATE_USER_MUTATION = `
            mutation ($username: String!) {
            createUser(username: $username) {
            id
            username
            }
        }
        
      `;
  
      try {
        const variables = { username };
        const data = await request('https://rnd-ns2-tech-challenge-next-be.vercel.app/api/graphql', CREATE_USER_MUTATION, variables);
        feedback = `User created! ID: ${data.createUser.id}`;
      } catch (err) {
        feedback = `Error: ${err.message}`;
      }
    };
  </script>
  
  <style>
    /* Add your styles here */
  </style>
  
  <div>
    <h2>Create User</h2>
    
    <div>
      <label>User Name:</label>
      <input bind:value={username} placeholder="Enter user's name" />
    </div>
    
    <button on:click={createUser}>Create User</button>
    
    <p>{feedback}</p>
  </div>