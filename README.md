# maven.grimoid.com

The Maven repository for the Assorted mods, served as a static site by GitHub Pages from this
repository. Nothing runs here: a Maven repository is files at predictable paths, and Gradle needs
no server to read them.

Repository URL, for a build script:

```groovy
maven {
    name = 'AssortedMods'
    url = 'https://maven.grimoid.com/mods'
}
```

What is in it: [Assorted Lib](https://github.com/grim3212/AssortedLib), which every Assorted mod
builds against, and [Assorted Build](https://github.com/grim3212/AssortedBuild), the shared build
plugins and version catalog. The mods themselves ship on Modrinth and CurseForge.

## Publishing

Nobody pushes here by hand. The `publish` job of a publishing repository's Build workflow checks
this repository out with its deploy key, runs Gradle's `maven-publish` into `mods/` - which also
keeps every `maven-metadata.xml` current - and pushes the result. One commit per release, named
after it.

GitHub Pages caches responses for up to ten minutes, so a version can take that long to become
resolvable after its commit lands.
