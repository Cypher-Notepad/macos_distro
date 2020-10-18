# macos_distro

## v3.0
1. Run the below to create .app with executable JAR
```
javapackager -deploy -native image -srcdir ./ -srcfiles Cypher-Notepad-3.0-release.jar -outdir ./ -outfile cypher-notepad-3.0-macos.app -appclass org.eclipse.jdt.internal.jarinjarloader.JarRsrcLoader -description "The Text Editor that provides hybrid encryption" -name "Cypher Notepad" -title "A Java-based, plain-text editor with hybrid encryption." -vendor "Dong-Geon Lee" -BappVersion=3.0 -Bicon="/Users/apple/Desktop/test/CypherNotepad.icns" -Bmac.category=Utilities -BlicenseType="Free"
```

2. minimize bundled JRE

3. pack into .pkg with the command below.
```
sudo pkgbuild --install-location /Applications --component /Applications/Cypher\ Notepad.app /Users/apple/Desktop/test/cypher-notepad-macosx.pkg
``` 

## v2.1

 not support.