Рецепт
===
git init

git hash-object -w bar.png
echo 'Contents of foo!' | git hash-object -w --stdin

git update-index --add --cacheinfo 100644 3c383d3c9dcaadfd08542cca4bb29497ffd486bc bar.png
git update-index --add --cacheinfo 100644 dbdc67472ff2dfcf872d27cb25f78fc24ff0f82b foo.txt

git write-tree

git rm --cached bar.png
git rm --cached foo.txt

git read-tree --prefix=dir1 3c78e530250bfc00efaf3401f030ecdb56238b14
git write-tree

echo 'initial commit' | git commit-tree e69d9184db71d79cc256c30de98515538970fce9

git update-ref refs/heads/master 7162ecf5936ed8f314ec96751b904eac6d46a1c6

git push origin master
