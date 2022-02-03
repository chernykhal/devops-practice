## Решение задания к занятию «2.4. Инструменты Git»
1. aefead2207ef7e2aa5dc81a34aedf0cad4c32545 Update CHANGELOG.md(git log aefea);
2. v0.12.23(git log 85024d3)
3. 56cd7859e05c36c06b56d013b55a252d0bb7e158(git show b8d720^)
4. git log v0.12.23..v0.12.24 --oneline

![image](https://user-images.githubusercontent.com/42215603/152379912-88acd18f-809d-440f-b305-beca84e5b331.png)

5.8c928e835(git log -S'func providerSource' --oneline, git show 8c928e835)
6. 78b122055, 52dbf9483, 41ab0aef7, 66ebff90c, 8364383c3 (git grep -n globalPluginDirs, git log -L :globalPluginDirs:plugins.go --oneline)
7. Martin Atkins <mart@degeneration.co.uk>(git log -S'synchronizedWriters' --oneline, git show 5ac311e2a)
