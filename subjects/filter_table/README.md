## filter_table

### Instructions

- Define the functions:

  - new: creates a new empty table.

  - add_rows: adds a new row to the table from a slice of strings.
  
  - filter_cols: that receives a closure that receives a `&str` and returns a `bool` value:

	- filter_cols returns a table with all the columns that yielded true when applied to the header.
  
  - filter_rows: that receives a closure that receives a `&str` and returns a `bool` value

	- filter_rows returns a table with all the columns that yielded true when applied to the elements of the selected column.

### Expected function

```rust
pub struct Table {
	pub headers: Vec<String>,
	pub body: Vec<Vec<String>>,
}

impl Table {
	pub fn new() -> Table {
	}

	pub fn add_row(&mut self, row: &[String]) {
	}

	pub fn filter_col(&self, filter: ) -> Option<Self> {

	}

	pub fn filter_row(&self, col_name: &str, filter: ) -> Option<Self> {
	}
}
```

### Usage

Here is a possible test for your function:

```rust
fn main() {
	let mut table = Table::new();
	table.headers = vec![
		"Name".to_string(),
		"Last Name".to_string(),
		"ID Number".to_string(),
	];
	table.add_row(&[
		"Adam".to_string(),
		"Philips".to_string(),
		"123456789".to_string(),
	]);
	table.add_row(&[
		"Adamaris".to_string(),
		"Shelby".to_string(),
		"1111123456789".to_string(),
	]);
	table.add_row(&[
		"Ackerley".to_string(),
		"Philips".to_string(),
		"123456789".to_string(),
	]);
	let filter_names = |col: &str| col == "Name";
	println!("{:?}", table.filter_col(filter_names));

	let filter_philips = |lastname: &str| lastname == "Philips";
	println!("{:?}", table.filter_row("Last Name", filter_philips));
}
```

And its output:

```console
student@ubuntu:~/[[ROOT]]/test$ cargo run
Some(Table { headers: ["Name"], body: [["Adam"], ["Adamaris"], ["Ackerley"]] })
Some(Table { headers: ["Name", "Last Name", "ID Number"], body: [["Adam", "Philips", "123456789"], ["Ackerley", "Philips", "123456789"]] })
student@ubuntu:~/[[ROOT]]/test$
```