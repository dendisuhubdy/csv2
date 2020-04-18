# csv2
`csv2` is a fast, single-threaded CSV Parser written in `C++17`

```cpp
#include <csv2/reader.hpp>
using namespace csv2;

int main() {

  Reader csv{
    option::Filename{std::string("foo.csv")},
    option::Delimiter{','},
    option::SkipInitialSpace{true},
    option::TrimCharacters{std::vector<char>{'\n', '\r'}},
    option::TrimPolicy{Trim::trailing}
    // ...
  };
  
  Row next;
  while (csv.read_row(next)) {
    // Do something with `row`
    // for (auto& [key, value]: row) {
    //   std::cout << key << ": " << value << "\n";
    // }
  }
}
```

## Highlights
* Blazing fast - Fast line reader coupled with generous use of `std::string_view` to minimize allocations/copies.
* Single-threaded - No additional worker threads.
* Lazy evaluated - Tokenization is not performed until `read_row()` is called.
* Configurable - Set your dialect with `csv2::option`.
* MIT License.
