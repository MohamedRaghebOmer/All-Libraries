# All Libraries

> A centralized collection of small, focused C++ libraries (header-only classes) I wrote to reuse across projects.

---

## Table of Contents

1. [About this repository](#about-this-repository)
2. [Libraries included](#libraries-included)
3. [Quick examples](#quick-examples)
4. [How to open & run (Visual Studio Community 2022)](#how-to-open--run-visual-studio-community-2022)
5. [Repository structure](#repository-structure)
6. [Design & coding notes](#design--coding-notes)
7. [Contributing & updates](#contributing--updates)
8. [Tech stack & tools](#tech-stack--tools)
9. [License](#license)

---

## About this repository

**All Libraries** is a single repository that groups small, well-scoped C++ utility libraries (implemented as classes or header-only components). Each library focuses on a single responsibility (e.g., date utilities, string helpers, input validation, periods). The goal is to provide reusable building blocks that are easy to add to any console application or small project.

This repository is intended for learning, quick reuse, and small-scale projects built using Visual Studio Community 2022.

---

## Libraries included

Each library is delivered as a C++ header (`.h` / `.hpp`) plus any lightweight implementation. The main libraries in this repo are:

* **Date Library** (`clsDate`) — full-featured date utilities: parse/format dates, arithmetic (add/subtract days, months, years), calendar printing, comparisons, difference in days, business-day helpers, and more.

* **String Library** (`clsString`) — common string utilities: length, case transforms (upper/lower), word counting, split/join, trimming, replace, remove punctuations, reverse words, and more.

* **Period Library** (`clsPeriod`) — utilities for working with date ranges/periods: overlap detection, period length, counting overlapped days, printing.

* **Input & Validate Library** (`clsInputValidate`) — safe input and validation helpers: read typed numbers (short/int/float/double) with bounds checks, date reading, number utilities, array helpers (shuffle, count positives/negatives), text encryption helpers, and more.

> Note: The repository contains other small helpers and a `Global.h` header for shared includes/macros used across libraries.

---

## Quick examples

Below are minimal usage examples. These snippets assume you included the headers and you are using `using namespace std;` in your `main.cpp` file.

### Example: Print today's date and time

```cpp
#include "clsDate.h"
#include <iostream>
using namespace std;

int main()
{
    clsDate today = clsDate::GetSystemDate();
    cout << "Today: " << today.DateToString() << "\n";
    cout << "Time: " << clsDate::GetSystemTime() << "\n";

    return 0;
}
```

### Example: Format and compare dates

```cpp
#include "clsDate.h"
#include <iostream>
using namespace std;

int main()
{
    clsDate d1(1, 1, 2023);
    clsDate d2("15/02/2023");

    cout << "d1: " << d1.Format("dd/mm/yyyy") << "\n";
    cout << "d2: " << d2.Format("dd-mm-yyyy") << "\n";

    if (d1.CompareDates(d1, d2) == clsDate::Before)
        cout << "d1 is before d2\n";

    cout << "Days between: " << clsDate::GetDifferenceInDays(d1, d2, true) << "\n";

    return 0;
}
```

### Example: String helpers

```cpp
#include "clsString.h"
#include <iostream>
using namespace std;

int main()
{
    string s = "hello world";
    cout << clsString::UpperFirstLetterOfEachWord(s) << "\n"; // Hello World

    vector<string> parts = clsString::Split("one,two,three", ",");
    cout << "Parts: " << parts.size() << "\n";

    return 0;
}
```

### Example: Read positive integer with validation

```cpp
#include "clsInputValidate.h"
#include <iostream>
using namespace std;

int main()
{
    int n = clsInputValidate::ReadPositiveInt(true, "Enter positive int: ");
    cout << "You entered: " << n << "\n";
    return 0;
}
```

---

## How to open & run (Visual Studio Community 2022)

These libraries are written for native C++ (MSVC). Follow these steps to use them in Visual Studio 2022:

1. **Clone the repository**

   ```bash
   git clone https://github.com/<your-username>/All-Libraries.git
   ```

2. **Create a new Visual Studio solution or project**

   * Open Visual Studio Community 2022 -> Create a new project -> Console App (C++).
   * Or open an existing solution you want to add utilities to.

3. **Add headers to your project**

   * Copy the desired header files (e.g. `clsDate.h`, `clsString.h`, `clsInputValidate.h`) into your project folder or add them as links.
   * In Visual Studio: Right-click project -> Add -> Existing Item -> select the header/source files.

4. **Include and build**

   * In your `.cpp` files, `#include` the headers you need.
   * Build the solution (Ctrl+Shift+B) and run.

5. **Compiler settings**

   * Use default MSVC settings. These libraries are header-based and do not require special flags.

---

## Repository structure

```
All-Libraries/
├─ README.md
├─ LICENSE
├─ include/
│  ├─ clsInputValidate.h
│  ├─ clsDate.h
│  ├─ clsString.h
|  ├─ clsUtil.h
│  └─ Global.h
└─ samples/
   ├─ example_date.cpp
   ├─ example_string.cpp
   └─ example_input.cpp
```

> Tips: Keep headers in `include/` and sample / test programs in `samples/`. This keeps the repo tidy and makes reusing headers simple.

---

## Design & coding notes

* Libraries are **small, single-responsibility** classes intended for console apps.
* Avoid heavy third-party dependencies; prefer standard library and small utilities.
* Prefer clear, simple APIs so beginners can reuse them easily.
* All dates are treated in the Gregorian calendar (utilities like `isLeapYear`, `DayOfWeekOrder`, etc.).
* `Global.h` is intentionally lightweight (shared typedefs, common includes, macros). Keep it minimal.

---

## Contributing & updates

Contributions are welcome. Suggested workflow:

1. Fork the repo.
2. Create a branch: `feature/<short-desc>`.
3. Add tests or sample usage demonstrating your change in `samples/`.
4. Create a PR describing the change and the rationale.

When updating libraries, keep backward compatibility in mind. Add new helpers as new functions rather than changing established signatures unless necessary.

---

## Tech stack & tools

* Language: C++ (compatible with MSVC / Visual Studio Community 2022)
* Primary dev environment: Visual Studio Community 2022 (Windows)
* Version control: Git & GitHub

---

## License

This repository uses the **MIT License** by default. If you want a different license, update the `LICENSE` file accordingly.

---

## Final notes

* The code samples shown in this README are minimal; full implementations live inside their respective header files. You mentioned some files were trimmed when sending — make sure to copy the full, tested headers into `include/` before use.

---

## 📫 Contact
- **Telegram**: [@Mohamed_Ragheb0](https://t.me/Mohamed_Ragheb0)

- **Email**: mohamedraghebomer@gmail.com
------------------------------------------------------------------------
