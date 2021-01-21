+++
title = "Fenced code tab usage example"
+++

# A first bloc of code
{% fenced_code_tab(tabs=["rust", "C", "java"]) %}
```rust
prinln!("Hello World!");
```
---
```C
prinf("Hello World!\n");
```
---
```java
system.out.println("Hello World!");
```
{% end %}

Some text here

# A second bloc of code

more text right here

{% fenced_code_tab(tabs=["bash", "ruby", "python", "lua", "nodejs"]) %}
```bash
echo "Hello World!"
```
---
```ruby
puts "Hello World!"
```
---
```python
print("Hello World!")
```
---
```lua
print("Hello World!")
```
---
```js
console.log("Hello World!")
```
{% end %}

one final little text right here to end this example
