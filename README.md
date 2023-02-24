
# Scrapper

This is a product price comparsion web app, that fetches the prices of a product from different websites like amazon, flipkart. 


## Tech Stack

**Client:** HTML, CSS, EJS

**Server:** Node, Express, K8s, Docker.


## Run Locally

Clone the project

```bash
  git clone https://link-to-project
```

Go to the project directory

```bash
  cd my-project
```

Install dependencies

```bash
  npm install
```

Start the server

```bash
  npm run start
```
The application PORT is 4000.

## Deploy

To deploy this project on k8s run
```
  You can change image name in scraper-deployment.yml (line 18).
```

```bash
  kubectl apply -f scraper-deployment.yml
```
