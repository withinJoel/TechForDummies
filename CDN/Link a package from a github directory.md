# GitHub CDN URL Explanation

## Explanation

* To include a JavaScript file hosted on GitHub using a CDN, you use a URL formatted as follows:

`/gh/username/repo-name/folder path/file name`

**Code Example:**

`<script src="https://cdn.jsdelivr.net/gh/withinJoel/mindboost/Mindboost/Mindboost-1.2.3.js"></script>`

## Explanation

* `GH` stands for GitHub.
* `username` is the GitHub username of the repository you are targeting.
* `repo-name` is the name of the repository.
* `folder path` is the path to the folder within the repository where the file is located.
* `file name` is the name of the file you want to include, including its version number.

## Note
* The version number should be included in the file name, and it must follow this format: -1.2.3. If the version number is not included or is incorrectly formatted, the file may not work as expected.
