# Permission

### Issues:

insufficient-permission-for-adding-an-object-to-repository-database

```
# https://stackoverflow.com/questions/6448242/git-push-error-insufficient-permission-for-adding-an-object-to-repository-datab
# From project root

cd .git/objects
ls -al
sudo chown -R yourname:yourgroup *

# (yourname=dau, yourgroup=dau)


```
