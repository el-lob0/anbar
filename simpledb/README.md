
# simpleDB | key value database file store

Checkout colondb crate for multiple column support.


> [!NOTE]
> The simple_db struct is not the database itself, 
> its just a way to apply changes to the .txt where the database is saved

---
### usage

<p>
add to Cargo.toml

```sh
cargo add simple_db
```
</p>

<p>
use in main.rs

```rust
use simple_db::SimpleDB;
```
</p>


#### Methods:
find save file, or create one
```rust
let mut database = SimpleDB::find_database("db3.txt");
let mut db = database.unwrap(); // this or handle the error with a match/if
```

Keys and values are of type `String`
```rust
db.insert_into_db(key, value);
// Adds key value pair or modifies value of key if it already exists
```

Get value by id (key)
```rust
db.get_value_from_db(key)
// returns and option, so None if the key doesnt exist.
```

Delete value by key
```rust
db.delete_from_db(key)
// returns and option, so None if the key doesnt exist.
```

Sort the database
```rust
db.sort_by_key();
db.sort_by_value();
```

To access the Indexmap yourself:
```rust
db.data... // the data here is an indexmap of string: string
```

Display db in the terminal 
```rust
db.print_db()
```
