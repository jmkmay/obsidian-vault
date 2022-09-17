# Database patterns in Rust

Rust forgoes the concept of inheritance in favor of composition. This means creating base classes such as `Identifiable`, or `Queryable` to extend from in order to make organizing code simpler, is not possible.

First approach I've considered is leaving the logic to create a storable object up to the class, and have the database client take a storable object as an argument.

For instance:

```rust
struct SomeEntity {
	field_1: u32,
	field_2: String,
	field_3: Address,
}

struct StorableItem {
	id: Uuid,
	created_datetime: u64,
}

trait Storable {
	fn get_storable_item(&self) -> StorableItem
}

impl Storable for SomeEntity {
	fn get_storable_item(&self) {
		{
			id: Uuid::new(&self::field_1, &self::field_2),
			created_datetime: datetime::now(),
		}
	}
}

trait Store {
	fn store_item(item: impl Storable) -> 
}

impl Store for DGraphClient {
	fn store_item(item: impl Storable) {
		... // database logic to store SomeEntity
	}
}
```
