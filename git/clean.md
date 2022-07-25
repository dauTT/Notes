# Clean

{% embed url="https://www.educative.io/answers/how-to-remove-untracked-files-in-git" %}

**Remove changes:**

```
git reset --hard
```



**Remove untracked files**

```
git clean -f


# Once the untracked files are deleted, they cannot be restored.
# Before running the git clean command, perform dry run to know what the are files that will be deleted.
-n flag is used to perform dry run.
-f flag is used to remove untracked files.
-fd flag is used to remove untracked files and folders.
-fx flag is used to remove untracked and ignored files.


```



