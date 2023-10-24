# Git Bash

* Setting MSYS_NO_PATHCONV to a non-empty value (e.g., 1 or true) disables automatic path conversion. This means that if you enter a Windows-style path, it won't be automatically converted to a Unix-style path. Instead, it will be treated as-is.

* Delete multiple git local branches: ``` git branch -d `git branch --list 'feature/*'` ```
