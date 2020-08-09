# gradle-sync-task
Documenting some inconsistency between Gradle's Copy and Sync tasks

See the build.gradle and run `./gradlew myCopy mySync` to test locally.

Bonus bug: Compare the results of running `./gradlew copyDupes1` (fails as intended) and `./gradlew copyDupes2` (should
fail but doesn't).

Both these bugs are due to Gradle's RelativePath class treating `.` (and `..`) entries as parts of paths when checking
them for equality, rather than canonicalizing them. Reported as: https://github.com/gradle/gradle/issues/5748
