### MongoDB Query Language (MQL) 
Is the syntax used to interact with MongoDB. It is similar to JSON and JavaScript-like in its structure, which makes it straightforward for developers familiar with JSON or JavaScript.

## **1. Connect to a MongoDB Database**
### **Switch to a Database**
```javascript
use database_name
```

### **Show All Databases**
```javascript
show dbs
```

---

## **2. Basic CRUD Operations**
### **Create (Insert Data)**
Insert a document into a collection:
```javascript
db.collection_name.insertOne({ name: "Alice", age: 25 })
```

Insert multiple documents:
```javascript
db.collection_name.insertMany([
  { name: "Bob", age: 30 },
  { name: "Charlie", age: 35 }
])
```

---

### **Read (Query Data)**

#### Get All Documents
```javascript
db.collection_name.find()
```

#### Find Documents Matching a Condition
```javascript
db.collection_name.find({ age: 30 })
```

#### Find with Projection (Select Specific Fields)
```javascript
db.collection_name.find({ age: { $gte: 30 } }, { name: 1, _id: 0 })
```
- `{ $gte: 30 }`: Matches `age >= 30`.
- `{ name: 1, _id: 0 }`: Return only the `name` field (1 = include, 0 = exclude).

#### Find One Document
```javascript
db.collection_name.findOne({ name: "Alice" })
```

---

### **Update (Modify Data)**

#### Update One Document
```javascript
db.collection_name.updateOne(
  { name: "Alice" },  // Filter
  { $set: { age: 26 } }  // Update
)
```

#### Update Multiple Documents
```javascript
db.collection_name.updateMany(
  { age: { $lt: 30 } },  // Filter
  { $set: { status: "young" } }  // Update
)
```

#### Replace a Document (Overwrites Entire Document)
```javascript
db.collection_name.replaceOne(
  { name: "Alice" },  // Filter
  { name: "Alice", age: 27, city: "NYC" }  // New Document
)
```

---

### **Delete (Remove Data)**

#### Delete One Document
```javascript
db.collection_name.deleteOne({ name: "Bob" })
```

#### Delete Multiple Documents
```javascript
db.collection_name.deleteMany({ age: { $gte: 30 } })
```

---

## **3. Query Operators**
These operators are used in the query object to filter data.

| **Operator** | **Description**                     | **Example**                         |
|--------------|-------------------------------------|-------------------------------------|
| `$eq`        | Equal                               | `{ age: { $eq: 25 } }`             |
| `$ne`        | Not equal                           | `{ age: { $ne: 25 } }`             |
| `$gt`        | Greater than                       | `{ age: { $gt: 25 } }`             |
| `$gte`       | Greater than or equal              | `{ age: { $gte: 25 } }`            |
| `$lt`        | Less than                          | `{ age: { $lt: 25 } }`             |
| `$lte`       | Less than or equal                 | `{ age: { $lte: 25 } }`            |
| `$in`        | Matches any value in array         | `{ age: { $in: [25, 30, 35] } }`   |
| `$nin`       | Does not match any value in array  | `{ age: { $nin: [25, 30] } }`      |

---

## **4. Advanced Queries**

#### Logical Operators
- `$and`: Matches all conditions.
- `$or`: Matches any condition.
- `$not`: Negates a condition.

Example:
```javascript
db.collection_name.find({
  $or: [{ age: { $lt: 30 } }, { name: "Charlie" }]
})
```

---

#### Nested Documents
Query inside nested fields:
```javascript
db.collection_name.find({ "address.city": "New York" })
```

---

#### Array Queries
Find documents where an array contains a value:
```javascript
db.collection_name.find({ hobbies: "reading" })
```

Find documents where an array contains multiple values:
```javascript
db.collection_name.find({ hobbies: { $all: ["reading", "coding"] } })
```

Find documents where an array has a specific size:
```javascript
db.collection_name.find({ hobbies: { $size: 2 } })
```

---

## **5. Aggregation Framework**
Use for advanced data manipulation and analysis.

#### Example: Group and Count
```javascript
db.collection_name.aggregate([
  { $group: { _id: "$age", count: { $sum: 1 } } }
])
```

#### Example: Filter, Project, and Sort
```javascript
db.collection_name.aggregate([
  { $match: { age: { $gte: 25 } } },
  { $project: { name: 1, age: 1 } },
  { $sort: { age: -1 } }
])
```

---

## **6. Indexing**
Indexes improve query performance.

#### Create an Index
```javascript
db.collection_name.createIndex({ age: 1 })  // 1 = Ascending, -1 = Descending
```

#### View Indexes
```javascript
db.collection_name.getIndexes()
```

#### Drop an Index
```javascript
db.collection_name.dropIndex({ age: 1 })
```

---

## **7. Common MongoDB Commands**
- **Show Collections**:
  ```javascript
  show collections
  ```
- **Drop a Collection**:
  ```javascript
  db.collection_name.drop()
  ```
- **Drop a Database**:
  ```javascript
  db.dropDatabase()
  ```

---

## **8. Advanced Aggregation**

### **Pipeline Stages**

1. **`$match`**: Filters data.
2. **`$group`**: Groups data by a field and applies aggregations.
3. **`$sort`**: Orders the results.
4. **`$project`**: Includes/excludes specific fields.
5. **`$lookup`**: Performs a join with another collection.

### **Code Example: Comprehensive Aggregation**
```javascript
db.orders.aggregate([
  { $match: { status: "shipped" } }, // Filter shipped orders
  { $group: { _id: "$customerId", totalSpent: { $sum: "$amount" } } }, // Group by customer and sum their spending
  { $sort: { totalSpent: -1 } }, // Sort by total spent, descending
  { $limit: 5 }, // Top 5 customers
  { $lookup: {
      from: "customers",
      localField: "_id",
      foreignField: "customerId",
      as: "customerDetails"
    }
  } // Enrich with customer details
])
```

---

## **9. Transaction Operations**

MongoDB supports multi-document ACID transactions in replica sets.

### **Code Example: Transactions**
```javascript
const session = db.getMongo().startSession();
session.startTransaction();

try {
  const ordersCollection = session.getDatabase("store").orders;
  const inventoryCollection = session.getDatabase("store").inventory;

  ordersCollection.insertOne({ orderId: 1, product: "Book", quantity: 1 });
  inventoryCollection.updateOne(
    { product: "Book" },
    { $inc: { stock: -1 } }
  );

  session.commitTransaction();
} catch (error) {
  session.abortTransaction();
  console.error("Transaction failed:", error);
} finally {
  session.endSession();
}
```

### **Key Concepts**
- Transactions ensure data consistency across collections.
- Use `startTransaction()` and `commitTransaction()` for atomic operations.

---

## **10. Advanced Indexing**

### **Compound Index**
```javascript
db.collection_name.createIndex({ age: 1, name: 1 })
```
- Combines multiple fields into a single index.

### **Text Index**
```javascript
db.collection_name.createIndex({ description: "text" })
```
- Enables full-text search.

### **Wildcard Index**
```javascript
db.collection_name.createIndex({ "$**": 1 })
```
- Indexes all fields in a document.

### **Performance Insight**
Use `explain()` to analyze query performance:
```javascript
db.collection_name.find({ age: 25 }).explain("executionStats")
```

---

## **11. Full-Text Search**

### **Search Text Fields**
```javascript
db.collection_name.find({ $text: { $search: "apple" } })
```

### **Search with Weighting**
```javascript
db.collection_name.createIndex({ title: "text", description: "text" }, { weights: { title: 10, description: 2 } })
```

### **Exclude Irrelevant Matches**
```javascript
db.collection_name.find({ $text: { $search: "apple -banana" } })
```
- Use `-` to exclude terms.

---

## **12. Geospatial Queries**

### **Create a Geospatial Index**
```javascript
db.places.createIndex({ location: "2dsphere" })
```

### **Find Places Near a Point**
```javascript
db.places.find({
  location: {
    $near: {
      $geometry: { type: "Point", coordinates: [longitude, latitude] },
      $maxDistance: 1000 // Meters
    }
  }
})
```

### **Find Places Within a Polygon**
```javascript
db.places.find({
  location: {
    $geoWithin: {
      $geometry: {
        type: "Polygon",
        coordinates: [[[lng1, lat1], [lng2, lat2], [lng3, lat3], [lng1, lat1]]]
      }
    }
  }
})
```

---

## **13. Array Operations**

### **Update Specific Array Elements**
```javascript
db.collection_name.updateOne(
  { _id: 1, "items.name": "apple" },
  { $set: { "items.$.quantity": 5 } }
)
```

### **Add Elements to an Array**
```javascript
db.collection_name.updateOne(
  { _id: 1 },
  { $push: { tags: "newTag" } }
)
```

### **Remove Specific Array Elements**
```javascript
db.collection_name.updateOne(
  { _id: 1 },
  { $pull: { tags: "obsoleteTag" } }
)
```

---

## **14. Data Validation**

### **Define a Validation Schema**
```javascript
db.createCollection("products", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["name", "price"],
      properties: {
        name: {
          bsonType: "string",
          description: "must be a string and is required"
        },
        price: {
          bsonType: "double",
          minimum: 0,
          description: "must be a double and is required"
        }
      }
    }
  }
})
```

---

## **15. Change Streams**

Track real-time changes to your collections.

### **Code Example: Watch Changes**
```javascript
const changeStream = db.collection_name.watch();

changeStream.on("change", (change) => {
  console.log("Change detected:", change);
});
```

### **Key Concepts**
- Use for real-time applications like notifications.

---

## **16. Backups and Restores**

### **Backup Database**
```bash
mongodump --db database_name --out /backup/directory
```

### **Restore Database**
```bash
mongorestore --db database_name /backup/directory/database_name
```

---

## **17. Security Best Practices**

1. **Enable Authentication**:
   ```bash
   mongod --auth
   ```
2. **Create Users with Roles**:
   ```javascript
   db.createUser({
     user: "admin",
     pwd: "password",
     roles: [{ role: "userAdminAnyDatabase", db: "admin" }]
   });
   ```

3. **Limit Network Exposure**:
   - Bind MongoDB to specific IPs using `bindIp` in `mongod.conf`.

---

## **18. Best Practices**

1. **Use Proper Indexing**:
   - Analyze slow queries with `db.currentOp()` and create indexes accordingly.

2. **Sharding for Scalability**:
   - Split data across multiple shards for large datasets.

3. **Avoid Large Documents**:
   - MongoDB has a 16MB document size limit.

4. **Enable Write Concern**:
   - Ensure data integrity with write acknowledgment:
     ```javascript
     db.collection_name.insertOne({ key: "value" }, { writeConcern: { w: 1 } });
     ```

---

## **Resources**

1. [MongoDB Documentation](https://www.mongodb.com/docs/)
2. [MongoDB University](https://university.mongodb.com/)
3. [MQL Reference Guide](https://www.mongodb.com/docs/manual/reference/command/)

---
# Comparison Of SQL To MongoDB
When comparing **SQL (relational databases)** and **MongoDB (a NoSQL database)**, it largely depends on your specific use case, the type of data you're working with, and the skills of your team. Both have their strengths and weaknesses, so let's break it down to help you understand which might be better or easier for your needs.

---

### **1. What is SQL?**
SQL databases are **relational databases** that organize data into tables with rows and columns, and relationships between data are defined explicitly (e.g., foreign keys). Examples include:
- MySQL
- PostgreSQL
- Microsoft SQL Server
- SQLite

### **2. What is MongoDB?**
MongoDB is a **NoSQL database** that stores data in a flexible, JSON-like format (called BSON). It is schema-less, meaning you don't have to define a rigid structure for your data.

---

### **Key Differences:**

| **Aspect**              | **SQL (Relational Databases)**                                                                 | **MongoDB (NoSQL Database)**                                                               |
|--------------------------|-----------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| **Data Structure**       | Fixed schema with tables, rows, and columns. Relationships between tables are explicitly defined. | Flexible schema with JSON-like documents (BSON), suitable for semi-structured or unstructured data. |
| **Relationships**        | Strongly supports complex relationships using joins and foreign keys.                         | Stores data as embedded documents, reducing the need for joins but making relationships less explicit. |
| **Scalability**          | Vertically scalable (adding more power to a single server).                                   | Horizontally scalable (easily adds more servers).                                          |
| **Ease of Use**          | Requires designing and maintaining a schema, but querying with SQL is widely understood.      | Easier to start with because of its schema-less nature, but querying requires learning MongoDB syntax. |
| **Performance**          | Best for structured, predictable data and complex queries.                                    | Better for high write/read loads and large volumes of unstructured or semi-structured data. |
| **Query Language**       | Standard SQL, familiar and widely used.                                                       | MongoDB Query Language (MQL), uses JSON-like syntax, simpler for some tasks.              |
| **Flexibility**          | Less flexible because of rigid schema requirements.                                           | Highly flexible due to its schema-less design, making it ideal for rapidly evolving apps.  |
| **Transaction Support**  | Strong ACID compliance for transactional systems like banking, e-commerce, etc.               | Supports transactions but is less mature than relational databases for complex transactions. |
| **Indexing**             | Supports various indexing strategies.                                                        | Also supports indexing but shines with geospatial and other modern types of indexes.       |

---

### **When to Use SQL?**
SQL databases are better when:
1. **You Have Structured Data**:
   - Data fits neatly into tables with rows and columns.
   - Example: Customer data, order history, financial data.

2. **You Need Relationships**:
   - Data has many relationships, like between users, orders, and products.
   - Example: An e-commerce application.

3. **You Need Transactions**:
   - Use cases where data integrity is critical (e.g., banking, payment systems).

4. **You Need Complex Queries**:
   - You rely on joins, aggregations, and other advanced SQL features.

---

### **When to Use MongoDB?**
MongoDB is better when:
1. **You Have Unstructured or Semi-Structured Data**:
   - Data can change over time without requiring rigid schemas.
   - Example: Social media profiles, IoT sensor data, or dynamic forms.

2. **You Need Scalability**:
   - Applications with high traffic and large volumes of data.
   - Example: Real-time analytics, content management systems.

3. **Your Schema Evolves Frequently**:
   - MongoDB's schema-less nature is great for projects where the data model changes frequently.

4. **Speed and Simplicity**:
   - You need fast prototyping and development, especially for agile projects.

---

### **Ease of Use: SQL vs MongoDB**
- **SQL**:
  - Easier if you have structured data and are already familiar with SQL syntax.
  - Many developers already know SQL, making onboarding easier.
  - Complex queries can be more straightforward with SQL.

- **MongoDB**:
  - Easier for handling dynamic or semi-structured data since you don't need to design schemas upfront.
  - The JSON-like query syntax can be more intuitive for developers used to working with JavaScript or modern web development.

---

### **Which is Better?**
- **Go with SQL if**:
  - Your data is structured and relationships are important.
  - You need ACID compliance for strict transactional requirements.
  - You're dealing with well-understood, stable datasets.

- **Go with MongoDB if**:
  - Your data is unstructured, semi-structured, or frequently changing.
  - You need high scalability and flexibility for large-scale applications.
  - You prioritize speed and simplicity over strict schema enforcement.

---

### **Real-World Example**
- **SQL Use Case**: 
  - A banking application that manages accounts, transactions, and balances. 
  - Data integrity and complex relationships are key.

- **MongoDB Use Case**: 
  - A social media platform where user profiles, posts, and interactions are highly dynamic and can change structure over time.

---

### **Final Thoughts**
Neither SQL nor MongoDB is universally "better." Each excels in specific scenarios. If you're using MongoDB already and it works well for your projects, there's no need to switch. However, if you find MongoDB's schema-less nature leading to confusion or inefficiencies, SQL may be worth considering.
