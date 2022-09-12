# Cloud Resume Challenge

This code is part of the Cloud Resume Challenge put forth by Forrest Brazeal. Check out the original challenge <a href="https://cloudresumechallenge.dev/docs/the-challenge/">here</a>.  

### Prerequisites

What you need before starting the challenge.

* An Azure account;
* Node.js;
* Custom domain name;

## My Steps
### 1: Host Static Website in Azure Storage

The first step was to set up a static website in Azure. I followed the Azure documentation page found <a href="https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website">here</a>. 

### 2: Make the website secure

The second step was to make the website use HTTPS for security. I ran into an issue here. I could not use Azure CDN since it was unavailable in my Azure student subscription. As an alternative solution, I decided to use Cloudflare for my security needs and connect the two services.

```
1. Purchase custom domain and add to Cloudflare
2. Set up Cloudflare DNS by adding an "as-verify" CNAME and a custom domain CNAME pointing to the Azure website URL
3. Add custom domain to Azure website
```
These steps ensured that when the user accessed the custom domain it would be routed through the Cloudflare server before reaching the Azure webserver.

### 3: Create CosmosDB database

The third step was to set up the CosmosDB database in Azure. I followed the Azure documentation page found <a href="https://docs.microsoft.com/en-us/azure/cosmos-db/sql/create-sql-api-nodejs">here</a>. I chose to use the core (SQL) API because I wanted to learn more SQL. This allowed my data to be queried with SQL despite CosmosDB being a NoSQL database. 

### 4. Write a script to count the number of visits to my site

I originally tried to write the visitor counter in my frontend JavaScript file but soon realized that I would run into issues connecting it with the Azure database. Instead, I decided to integrate the script into my API using Azure functions. See next step.

### 5. Create API to connect CosmosDB and web application

This was by far the most challenging part of the project. I knew nothing about Azure functions and struggled in implementing them. After multiple tries, many YouTube videos watched, and documentation read, I was finally able to create the API by using a lot of the information found in the Azure pages <a href="https://docs.microsoft.com/en-us/azure/cosmos-db/sql/create-sql-api-nodejs">here</a> and <a href="https://docs.microsoft.com/en-us/azure/azure-functions/create-first-function-vs-code-node">here</a>

```
1. Create a new function app in Azure. I set Node.js as my language here.
2. Download Azure tools extension in VS Code.
3. Create local function using the Azure function extension in VS Code. I used the HTTP trigger template here because it was the trigger I needed for this project.
4. Initialize CosmosClient in local function to connect to CosmosDB. This requires using the endpoint and key found in the CosmosDB resource in Azure.
5. 
```

# TO BE CONTINUED... STILL WRITING
