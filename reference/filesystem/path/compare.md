# compare
* filesystem[meta header]
* std::filesystem[meta namespace]
* path[meta class]
* function[meta id-type]
* cpp17[meta cpp]

```cpp
int compare(const path& p) const noexcept;          // (1)
int compare(const string_type& s) const;            // (2)
int compare(basic_string_view<value_type> s) const; // (3)
int compare(const value_type* s) const;             // (4)
```

## 概要
他のパスと文字列レベルで比較する


## 戻り値
- (1) : `this->`[`native()`](native.md)と`p.`[`native()`](native.md)を辞書順比較し、`*this`の方が小さければ0未満の値、`*this`の方が大きければ0より大きい値、等しければ0を返す
- (2), (3), (4) : `compare(path(s))`を返す


## 例
```cpp example
#include <iostream>
#include <filesystem>

namespace fs = std::filesystem;

int main()
{
  fs::path a = "a/b/c";
  fs::path b = "a/b/d";

  std::cout << a.compare(b) << std::endl;
  std::cout << b.compare(a) << std::endl;
  std::cout << a.compare(a) << std::endl;
}
```
* compare[color ff0000]


### 出力例
```
-3
3
0
```


## バージョン
### 言語
- C++17

### 処理系
- [Clang](/implementation.md#clang):
- [GCC, C++17 mode](/implementation.md#gcc): 8.1
- [Visual C++](/implementation.md#visual_cpp):