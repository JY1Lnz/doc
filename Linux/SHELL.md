## 变量
变量使用等号定义，等号两边不能有空格。
## 获得shell执行的文件夹
```shell
SHELL_FOLDER=$(cd "$(dirname "$0")";pwd)


template <class T>
auto TrieNode::Insert(std::string_view key, T value) const -> TrieNode {
  char c = key[0];
  auto iter = children_.find(c);
  if (iter != children_.end()) {
    return Insert(key.substr(1), value);
  }

  {}
}
```
