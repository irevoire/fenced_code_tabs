{#
The aim of this file is to provide a way to create a multi-languages tabbed code block.
You'll need to separate each code-block with a --- tag.
You'll also need to provide a list of strings that'll be displayed in the tabs.

Example:


{% fenced_code_tab(tabs=["rust", "C", "java"]) %}
```rust
println!("Hello World!");
```
---
```C
prinf("Hello World!\n");
```
---
```java
system.out.println("Hello World!");
```
{% end %}") }}


===================================
        CODE STARTS BELOW
===================================
#}

{% if tabs is not defined %}
{{ throw(message="You did not provide any tab name") }}
{% endif %}

{% set body = body | markdown | split(pat="<hr />") %}

{% if tabs | length != body | length %}
{{ throw(message="You must provide as much tabs name as there is code blocks") }}
{% endif %}

{% if nth == 1 %}
<link rel="stylesheet" href="fenced_code_tab.css">
{% endif %}

<div class="md-fenced-code-tabs" id="tab-tab-group-{{ nth }}">

{%- for i in range(end=tabs | length) -%}
<input
	name="tab-group-{{ nth }}"
	type="radio"
	id="tab-group-{{ nth }}-{{ i }}_{{ tabs[i] }}"
	checked="checked"
	class="code-tab"
	data-lang="{{ tabs[i] }}"
	aria-controls="tab-group-{{ nth }}-{{ i }}_{{ tabs[i] }}-panel"
	role="tab"
>
<label
	for="tab-group-{{ nth }}-{{ i }}_{{ tabs[i] }}"
	class="code-tab-label"
	data-lang="{{ tabs[i] }}"
	id="tab-group-{{ nth }}-{{ i }}_{{ tabs[i] }}-label"
>{{ tabs[i] }}</label>
<div
	class="code-tabpanel"
	role="tabpanel"
	data-lang="{{ tabs[i] }}"
	id="tab-group-{{ nth }}-{{ i }}_{{ tabs[i] }}-panel"
	aria-labelledby="tab-group-{{ nth }}-{{ i }}_{{ tabs[i] }}-label"
> {{ body[i] | safe }} </div>

{%- endfor %}

</div>
