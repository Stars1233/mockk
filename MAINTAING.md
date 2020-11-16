 
## Releasing mockk
 
 Main thing before release is to test it well. There was cases when after upgrade of library Android Instrumented was not tested and half a year was not usable.
 
 So checklist:
 
 - [ ] make sure all required PRs are merged
 - [ ] run test-suite in Gradle
 - [ ] run test-suite from Android Studio or IntelliJ from emulator (Android Instrumented tests)
 - [ ] release to local maven repo
 - [ ] do quick testing with this local maven repo: basics, if documentation is laoding, if all dependencies are fine
 - [ ] change version to RELEASE version (i.e. remove -SNAPSHOT from version)
 - [ ] bump if needed major or minor (resetting everything afterwards)
 - [ ] commit it
 - [ ] tag it
 - [ ] redirect release process to oss.sonatype
 - [ ] release from Gradle
 - [ ] goto oss.sonatype
 - [ ] find io.mockk repo
 - [ ] check state of dependencies(are sizes okay), maybe download one
 - [ ] close repo
 - [ ] release repo
 - [ ] wait till it appears on Maven central
 - [ ] bump version and append -SNAPSHOT
 - [ ] commit
 - [ ] push to github
 - [ ] create github release based on tag and describe changes there
 - [ ] announce on reddit/kotlinlang/potentially at "annoncement place" on mockk.io
 