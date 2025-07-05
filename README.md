# macos_distro

## v3.0
1. Run the below to create .app with executable JAR (BUILD ON JDK 21)
```
jpackage \
--type dmg \
--input ./build \
--main-jar Cypher-Notepad-3.0-release.jar \
--dest ~/testspace/test \
--name "Cypher Notepad" \
--main-class org.eclipse.jdt.internal.jarinjarloader.JarRsrcLoader \
--description "A Java-based, plain-text editor with hybrid encryption." \
--vendor "Dong-Geon Lee" \
--app-version 3.0 \
--icon CypherNotepad.icns \
--mac-package-name "Cypher Notepad" \
--mac-app-category Utilities \
--add-modules java.base,java.desktop,java.management,jdk.crypto.ec
```

## v2.1

 not support.
