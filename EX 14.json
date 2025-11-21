Exp14
// ==============================
// RESTAURANTS COLLECTION QUERIES
// ==============================

//️ Restaurants except 'American' & 'Chinese' OR name begins with 'Wil'
db.restaurants.find(
  {
    $or: [
      { cuisine: { $nin: ["American", "Chinese"] } },
      { name: /^Wil/i }
    ]
  },
  { restaurant_id: 1, name: 1, borough: 1, cuisine: 1 }
);

// ️ Grade "A" and score 11 on 2014-08-11
db.restaurants.find(
  {
    grades: {
      $elemMatch: {
        grade: "A",
        score: 11,
        date: ISODate("2014-08-11T00:00:00Z")
      }
    }
  },
  { restaurant_id: 1, name: 1, grades: 1 }
);

// ️ 2nd element of grades array with grade "A" and score 9 on 2014-08-11
db.restaurants.find(
  {
    "grades.1.grade": "A",
    "grades.1.score": 9,
    "grades.1.date": ISODate("2014-08-11T00:00:00Z")
  },
  { restaurant_id: 1, name: 1, grades: 1 }
);

// ️ 2nd coord element between 42 and 52
db.restaurants.find(
  {
    "address.coord.1": { $gt: 42, $lte: 52 }
  },
  { restaurant_id: 1, name: 1, address: 1, "address.coord": 1 }
);

//️ Sort restaurant names ascending
db.restaurants.find().sort({ name: 1 });

// ️ Sort restaurant names descending
db.restaurants.find().sort({ name: -1 });

// ️ Sort cuisine ascending and borough descending
db.restaurants.find().sort({ cuisine: 1, borough: -1 });

// ️ Check whether all addresses have a street field
db.restaurants.find({ "address.street": { $exists: true } });

// ️ coord field value is Double
db.restaurants.find({ "address.coord": { $type: "double" } });

//  Restaurants with remainder 0 when score divided by 7
db.restaurants.find(
  { "grades.score": { $mod: [7, 0] } },
  { restaurant_id: 1, name: 1, grades: 1 }
);

//  Name contains 'mon'
db.restaurants.find(
  { name: /mon/i },
  { name: 1, borough: 1, "address.coord": 1, cuisine: 1 }
);

//  Name starts with 'Mad'
db.restaurants.find(
  { name: /^Mad/i },
  { name: 1, borough: 1, "address.coord": 1, cuisine: 1 }
);

//️ At least one grade < 5
db.restaurants.find({ "grades.score": { $lt: 5 } });

//  Grade < 5 and borough = Manhattan
db.restaurants.find({ "grades.score": { $lt: 5 }, borough: "Manhattan" });

//  Grade < 5 and borough = Manhattan or Brooklyn
db.restaurants.find({
  "grades.score": { $lt: 5 },
  borough: { $in: ["Manhattan", "Brooklyn"] }
});

//  Same as above but cuisine not American
db.restaurants.find({
  "grades.score": { $lt: 5 },
  borough: { $in: ["Manhattan", "Brooklyn"] },
  cuisine: { $ne: "American" }
});

//  Same as above but cuisine not American or Chinese
db.restaurants.find({
  "grades.score": { $lt: 5 },
  borough: { $in: ["Manhattan", "Brooklyn"] },
  cuisine: { $nin: ["American", "Chinese"] }
});

// ️ Has both score 2 and 6
db.restaurants.find({
  "grades.score": { $all: [2, 6] }
});

//  Has scores 2 & 6 and borough Manhattan
db.restaurants.find({
  "grades.score": { $all: [2, 6] },
  borough: "Manhattan"
});

//  Has scores 2 & 6 and borough Manhattan or Brooklyn
db.restaurants.find({
  "grades.score": { $all: [2, 6] },
  borough: { $in: ["Manhattan", "Brooklyn"] }
});

//️ Same as above but cuisine not American
db.restaurants.find({
  "grades.score": { $all: [2, 6] },
  borough: { $in: ["Manhattan", "Brooklyn"] },
  cuisine: { $ne: "American" }
});

// ️ Same as above but cuisine not American or Chinese
db.restaurants.find({
  "grades.score": { $all: [2, 6] },
  borough: { $in: ["Manhattan", "Brooklyn"] },
  cuisine: { $nin: ["American", "Chinese"] }
});

// ️ Has grade score 2 or 6
db.restaurants.find({
  $or: [
    { "grades.score": 2 },
    { "grades.score": 6 }
  ]
});


// ==============================
// MOVIES COLLECTION QUERIES
// ==============================

/️/ Movies released in 1893
db.movies.find({ year: 1893 });

/️/ Movies with runtime > 120
db.movies.find({ runtime: { $gt: 120 } });

// ️ Movies with genre "Short"
db.movies.find({ genres: "Short" });

// ️ Movies directed by "William K.L. Dickson"
db.movies.find({ directors: "William K.L. Dickson" });

// ️ Movies released in USA
db.movies.find({ countries: "USA" });

// ️ Movies rated "UNRATED"
db.movies.find({ rated: "UNRATED" });

// ️ IMDb votes > 1000
db.movies.find({ "imdb.votes": { $gt: 1000 } });

// ️ IMDb rating > 7
db.movies.find({ "imdb.rating": { $gt: 7 } });

//  Tomatoes viewer rating > 4
db.movies.find({ "tomatoes.viewer.rating": { $gt: 4 } });

// ️ Movies that received an award
db.movies.find({ "awards.wins": { $gt: 0 } });

// ️ Movies with at least one nomination
db.movies.find(
  { "awards.nominations": { $gte: 1 } },
  { title: 1, languages: 1, released: 1, directors: 1, writers: 1, awards: 1, year: 1, genres: 1, runtime: 1, cast: 1, countries: 1 }
);

// ️ Movies where cast includes "Charles Kayser"
db.movies.find(
  { cast: "Charles Kayser" },
  { title: 1, languages: 1, released: 1, directors: 1, writers: 1, awards: 1, year: 1, genres: 1, runtime: 1, cast: 1, countries: 1 }
);

// ️ Movies released on May 9, 1893
db.movies.find(
  { released: ISODate("1893-05-09T00:00:00Z") },
  { title: 1, languages: 1, released: 1, directors: 1, writers: 1, countries: 1 }
);

// ️ Movies having "scene" in the title
db.movies.find(
  { title: /scene/i },
  { title: 1, languages: 1, released: 1, directors: 1, writers: 1, countries: 1 }
);
