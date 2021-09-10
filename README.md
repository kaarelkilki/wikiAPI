# wikiAPI
With this project I learned creating RESTful API.

Everything below are done in app.js 

1. Setup of project

```node.js
//jshint esversion:6

const express = require("express");
const bodyParser = require("body-parser");
const ejs = require("ejs");
const mongoose = require("mongoose");

const app = express();

app.set("view engine", "ejs");

app.use(
  bodyParser.urlencoded({
    extended: true,
  })
);

app.use(express.static("public"));

// TODO

app.listen(3000, function () {
  console.log("Server started on port 3000");
});
```

2. Connect to database

```node.js
mongoose.connect("mongodb://localhost:27017/wikiDB", { useNewUrlParser: true });
```

3. Create schema and model

```node.js
const articleSchema = {
  title: String,
  content: String,
};

const Article = mongoose.model("Article", articleSchema);
```

4. GET articles from database

```node.js
app.get("/articles", function (req, res) {
  Article.find({}, function (err, foundArticles) {
    if (!err) {
      res.send(foundArticles);
    } else {
      res.send(err);
    }
  });
});
```

...to be continued.
