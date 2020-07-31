## About

I have created an accessibility audit tool with Pa11y for ShowPo which runs at 12:30pm each night. As ShowPo runs A/B tests, some checkout tests could potentially be flakey. To rectify this, they could build a parameter for Selenium to 'choose' an A/B test case so they can check pages like Checkout Shipping & Payments & Order Received. This allows them to test the accessibility of both paths. As I do not have access to these parameters, the tests with the note A/B have to be run separately until success. 

Additionally, this would be run on ShowPo's test environment, enabling them to test credit cards, and therefore the order received and returns page. 

## Setup

In order to run this Pa11y Dashboard, I recommend cloning the repository locally:

```sh
git clone https://github.com/ashleygraf101/showpo-pa11y-audit.git
```

Then installing the dependencies:

```sh
cd showpo-pa11y-audit
npm install
```

You'll also need to have [MongoDB][mongo] installed and running. For quick access, you can install via a package manager such as on Mac OS `brew install mongodb` or on Linux (Debian) it would be `apt-get install mongodb` or on Windows it would be from https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/.

This project runs in production mode. Run ```cp config/production.sample.json config/production.json``` to be able to run this application. 


There are two steps to import the data for the inital run of tests

1. Start the MongoDB server: ```mongod --dbpath /path/to/db```

2. Import data into MongoDB: Add data -> Insert Document - filename ```showpo-actions-import.json```

Final step. Change username & password to your username and password for Showpo. 

Then run the server!

```sh
NODE_ENV=production node index.js
```
