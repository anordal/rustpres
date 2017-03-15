TODO: Forside

---

# Language design (according to some)

---

# Language design
# :boom:
## The correct thing to do must also be the simplest.

— Jussi Pakkanen

<sup><sub>http://voices.canonical.com/jussi.pakkanen/2014/07/22/the-two-ways-of-doing-something/</sub></sup>

---

Often:
1. The **easy** way
2. The **correct** way
  2a. for **safety** reasons
  2b. for **performance** reasons

## The correct thing to do must also be the simplest:

* People will always do the easy thing <sup>[Pakkanen]</sup>
* I don't want the dilemma (and subsequent critique) <sup>[Nordal]</sup>

---

## Example: easy vs correct

… and how it can be fixed with a new language:

<sup><sub>https://en.wikipedia.org/wiki/Friendly_interactive_shell#bash.2Ffish_Translation_table</sub></sup>

---

# Language design
# :camel:
## Zero cost abstractions

— Bjarne Stroustrup <sup>[citation needed]</sup>

---

## is `std::string` a zero cost abstraction?
(for parameter passing, let's say)

```c++
void f(const std::string& s) {
	write(0, s.data(), s.size());
}
```

---

## is `std::string` a zero cost abstraction?

```c++
void f(const std::string& s) {
	write(0, s.data(), s.size());
}
```
What if we don't have a string at the callsite:
```c++
f(line.substr(…))

f("string literal")
```
FAIL: The function's API *needlessly* forces us to create a string.

---

# Language design
# :sparkles:

— Matsumoto