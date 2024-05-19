## Server Create Method

1. Command in bash

```bash
npm init -y
```

2. Command in bash

```bash
npm i express cors mongodb dotenv jsonwebtoken cookie-parser
```

3. Copy the code and past it index.js file

```js
const express = require('express');
const cors = require('cors');
const jwt = require("jsonwebtoken");
const cookieParser = require("cookie-parser");
const { MongoClient, ServerApiVersion } = require('mongodb');
require('dotenv').config();
const app = express();
const port = process.env.PORT || 5000;

// middleware
app.use(cors({origin: ["http://localhost:5173",],credentials: true,}));
app.use(express.json());
app.use(cookieParser());


const uri = `mongodb+srv://${process.env.DB_USER}:${process.env.DB_PASS}@cluster0.ufkobjs.mongodb.net/?retryWrites=true&w=majority&appName=Cluster0`;

const client = new MongoClient(uri, {
    serverApi: {
        version: ServerApiVersion.v1,
        strict: true,
        deprecationErrors: true,
    }
});

async function run() {
    try {
        
        const database = client.db("databaseName");
        const menuCollection = database.collection("collectionName");

        // Code hear-------------------------------





        // Code hear-------------------------------

        // await client.db("admin").command({ ping: 1 });
        console.log("Pinged your deployment. You successfully connected to MongoDB!");
    } finally {
        // await client.close();
    }
}
run().catch(console.dir);


app.get("/", (req, res) => {
    res.send("Server is running");
})

app.listen(port, () => {
    console.log(`Server is running on ${port}`);
})
```

4. Create dotenv file and past it

```
DB_USER=Username from mongoDB
DB_PASS=Password from mongoDB
SECRET_TOKEN=64bit token
```

5. Command in node for create SECRET_TOKEN

```bash
require("crypto").randomBytes(64).toString("hex")
```

## Server Setup Done
