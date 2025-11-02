
# colonDB | simpleDB with multiple columns support (database file store)

Checkout main folder for simple key value store.
Make sure you clone this repo inside the directory you write in the cargo.toml's ``[dependencies]  simple_db = ...``
May still contain issues, havent tested enough.

---
### usage



</br>

```sh
cargo add colon_db
```
</p>

<p>
use in main.rs

```rust
use colon_db::ColonDB;
```
</p>


#### Methods:
Find save file, or create one
```rust
let mut database = ColonDB::find_database("db.txt");
```

You can `echo` in the first row in the .txt file (`echo "id:h1,h2,h3..." >>> db.txt`)
Or set the header:
```rust 
db.set_header("key", vec!["value1", "value2"]);
```



Add item or row
```rust
database.append_row_to_db("23".to_string(),vec!["a".to_string(),"12".to_string(),"3000".to_string()]);

database.insert_item_into_db("21".to_string(),"name".to_string(), "kak".to_string());
database.insert_item_into_db("21".to_string(),"age".to_string(), "18".to_string());
```

Append a column
```rust
db.append_column("status".to_string(), "citizen".to_string());
```

Select a range from the db (0 to total number of rows, vector with column names)
```rust
let newdb = database.select_data(Some(4..17), vec!["name".to_string(), "salary".to_string()].into());
```

Get item by key, column
```rust
println!("{}",database.select_item("01", "age").unwrap())
```


Delete a row
```rust
database.delete_row("09");
```

Display database in terminal
```rust
newdb.print_database();
```
