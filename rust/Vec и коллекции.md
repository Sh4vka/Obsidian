`Vec<T>` — динамический массив, самая используемая коллекция в Rust. В отличие от [[Типы данных|array]], размер меняется в рантайме. Данные в куче, но управление автоматическое.

**Создание**:
```rust
let mut v: Vec<i32> = Vec::new();
let v = vec![1, 2, 3];
```

**Основные операции**:
```rust
v.push(4);          // добавить в конец
v.pop();            // убрать последний → Option<T>
v.len();            // длина
v.is_empty();       // bool
v.contains(&3);     // bool
v.remove(0);        // удалить по индексу (сдвигает остальные)
v.clear();          // очистить
```

**Доступ к элементам** — два способа:
```rust
let x = v[0];           // паникует если индекс вне границ
let x = v.get(0);       // возвращает Option<&T> — безопасно
match v.get(0) {
    Some(val) => println!("{}", val),
    None      => println!("пусто"),
}
```

**Итерация:**
```rust
for item in &v {         // по ссылкам — v остаётся живым
    println!("{}", item);
}

for item in &mut v {     // изменяемые ссылки
    *item *= 2;
}
```

**Prelude** — это список типов которые Rust подключает в каждый файл автоматически. Туда входят `Vec`, `String`, `Option`, `Result`, базовые трейты. Всё остальное — через `use`.

`HashMap<K, V>` — словарь:
```rust
use std::collections::HashMap;

let mut map: HashMap<String, i32> = HashMap::new();

map.insert(String::from("Goblin"), 30);
map.insert(String::from("Dragon"), 500);

// Чтение — возвращает Option
match map.get("Goblin") {
    Some(hp) => println!("HP: {}", hp),
    None     => println!("нет такого"),
}

// Вставить если нет
map.entry(String::from("Orc")).or_insert(80);

// Итерация
for (name, hp) in &map {
    println!("{}: {}", name, hp);
}

map.contains_key("Dragon");  // bool
map.remove("Goblin");
```