# GraphQL - GRAPHCOOL - Relay Modern

This is a guide that help to use graph.cool with Relay

**1. Install graphcool cli**

<code>$ npm install -g graphcool</code>

<br>

**2. Init Graphcool**

<code>$ graphcool init graphcool</code>

This will put all your Graphcool files inside graphcool folder of your project.

<br>

**3. Add the schema**

    type Link @model {
      id: ID! @isUnique
      url: String!
      description: String!
      postedBy: User @relation(name: "UsersLinks")
      votes: [Vote!]! @relation(name: "VotesOnLink")
    }

    type User @model {
      id: ID! @isUnique
      name: String!
      links: [Link!]! @relation(name: "UsersLinks")
      votes: [Vote!]! @relation(name: "UsersVotes")
    }

    type Vote @model {
      id: ID! @isUnique
      user: User @relation(name: "UsersVotes")
      link: Link @relation(name: "VotesOnLink")
    }

Next copy the content of schema to the <b><em>graphcool/types.graphql</em></b> .

<br>

**4. Deploy the project to Graphcool Cloud using**

<code>$ cd graphcool</code>

to change to graphcool directory.

<code>$ graphcool deploy --new-service [put your Service name here]</code>

or

<code>$ graphcool deploy -n [put your Service name here]</code>

CLI will prompt you to select the Cluster and afterwards initialise the project.

choose:

<code>shared-eu-west-1 </code>

Leave the target name <b><em>prod</em></b>

<br>

**5. Adding a mutation**

<b>A mutation is a data insertion in the database.</b>

Note: <em>Be sure you still in the <code> graphcool</code> folder</em>

<code> graphcool playground</code>

run this cood to open the graphcool playground.

Or simply open it from the project page on the console page.

    mutation CreateGraphcoolLink {
      createLink(
        url: "http://graph.cool"
        description: "this is graph cool link"
      ) {
        id
      }
    }

This is an example of the code to write for a mutation.

    Then hit the run button.

<br>

**5. Testing the added mutation**

    {
      allLinks{
        description
        id
        url
      }
    }


.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
.  
