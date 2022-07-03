# Learning about Git

## Questions

Deleted files remain in the log and shit (they do)
Detached HEAD and branchless commits


## Notes

See call commits including lost ones:

```
git reflog show --dirstat

b94bc21 (HEAD -> master) HEAD@{0}: checkout: moving from 495bc0d86900d44b496c05c29b1056bf72ee102a to master
 100.0% images/
495bc0d HEAD@{1}: commit: lost commit from Detached HEAD
eaad691 (tag: V_branchless) HEAD@{2}: checkout: moving from master to V_branchless
b94bc21 (HEAD -> master) HEAD@{3}: commit: screenshot
 100.0% images/
eaad691 (tag: V_branchless) HEAD@{4}: commit: delete file
308f5f8 HEAD@{5}: commit: add lineage
01bac39 HEAD@{6}: commit: add file to be deleted
9b50ef1 HEAD@{7}: commit (initial): first commit
```

Examine a particular commit by short name:

```
git show --pretty=fuller eaad691

 commit eaad691e79a835716ed7f233b58b89421b52fbc7 (tag: V_branchless)
Author:     Gordon Guthrie <gordon@hypernumbers.com>
AuthorDate: Thu Jun 30 10:05:41 2022 +0100
Commit:     Gordon Guthrie <gordon@hypernumbers.com>
CommitDate: Thu Jun 30 10:05:41 2022 +0100

    delete file

diff --git a/deletable.txt b/deletable.txt
deleted file mode 100644
index ef2819b..0000000
--- a/deletable.txt
+++ /dev/null
@@ -1,2 +0,0 @@
-bingo bango
-slip slop slap
\ No newline at end of file
```

Get git info
```
git show --format="%H\t%h\t[%P]\t%an\t%ae\t%aD\t%cn\t%ce\t%cD" -s 616ca5e
```

Sum user contributions:

```
git log --author="gordonguthrie" --format=tformat: --numstat | q -t "select sum(c1), sum(c2) from -"
```

get stats:

```
git log --pretty=tformat=%H\t%h\t[%P]\t%an\t%ae\t%aD\t%cn\t%ce\t%cD\t%s -s 3516151c6f712cb7742b171ebfd576bae17b78f8
```