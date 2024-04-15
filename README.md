# gitlab-ci
Collection of generic useful gitlab-ci stages

Uses `alpine/git:latest` container. 

* .gitlab-ci-conflicts.yml
  * Really just checking for `<<<<<<<` in any of the files.
  * Upon failure check logs to see all files with the string/a conflict.
  * Excluding `.gitlab-ci.yml` for obvious reasons. Change accordingly.
* .gitlab-ci-duplicates.yml
  * Finds duplicate files(based on file contents)
  * Duplicate files are logged.
  * `exit 1` if it finds any duplictes
  * Example set to `allow_failure`.
  * Remove `| grep -v -e '[Directory/Path/To/Ignore]' -e '[File/Path/To/Ignore.txt]' if you don't want to exclude certain directories/files. Or add using `-e '[path]'`
  * using `AWK` because busybox `uniq` doesn't support `-D`. In case you're wondering.
