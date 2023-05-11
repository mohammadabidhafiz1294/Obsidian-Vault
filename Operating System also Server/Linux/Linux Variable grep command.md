## apt list --upgradable

```
sudo apt upgrade $(apt list --upgradable | grep upgradable | cut -d '/' -f1 | tr -d ' ')
```

HERE, Description the code :
-   `apt list --upgradable` lists all the packages that have updates available.
-   `grep upgradable` filters the output of the previous command to only show the lines that contain the word "upgradable".
-   `cut -d '/' -f1` extracts the package name from each line by using the forward slash character (`/`) as the delimiter and taking the first field.
-   `tr -d ' '` removes any spaces from the package name.
-   The resulting list of package names is then passed as arguments to `sudo apt upgrade`, which upgrades those packages to their latest versions.
