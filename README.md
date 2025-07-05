# macos_distro

## v3.0
1. Run the below to create .app with executable JAR (BUILD ON JDK 21)
```
jpackage \
--type app-image \
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

2. Make .dmg file using the command below.
```
create-dmg \
  --volname "Cypher Notepad" \
  --volicon "CypherNotepad.icns" \
  --background "dmg_backgroud.png" \
  --window-pos 200 120 \
  --window-size 570 390 \
  --icon-size 100 \
  --icon "Cypher Notepad.app" 145 195 \
  --hide-extension "Cypher Notepad.app" \
  --app-drop-link 430 195 \
  --no-internet-enable \
  "cypher-notepad-3.0-apple-silicon.dmg" \
  "./bundles/silicon/Cypher Notepad.app"
``` 

## v2.1

 not support.


```python
import os

def get_all_files(directory):
    """Recursively collect all files in a directory."""
    files_set = set()
    for root, _, files in os.walk(directory):
        for file in files:
            # Store relative path for comparison
            rel_dir = os.path.relpath(root, directory)
            rel_file = os.path.join(rel_dir, file) if rel_dir != '.' else file
            files_set.add(rel_file)
    return files_set

def delete_unmatched_files(folder_a, folder_b):
    """Delete files in folder_b that are not in folder_a."""
    files_in_a = get_all_files(folder_a)
    files_in_b = get_all_files(folder_b)
    
    # Find files in B not in A
    files_to_delete = files_in_b - files_in_a
    
    for file in files_to_delete:
        file_path = os.path.join(folder_b, file)
        if os.path.exists(file_path):
            print(f"Deleting file: {file_path}")
            os.remove(file_path)

# Example usage
folder_a = 'path/to/folder/A'
folder_b = 'path/to/folder/B'

delete_unmatched_files(folder_a, folder_b)

```
