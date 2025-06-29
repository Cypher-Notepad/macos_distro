# macos_distro

## v3.0
1. Run the below to create .app with executable JAR
```
javapackager -deploy -native image -srcdir ./ -srcfiles Cypher-Notepad-3.0-release.jar -outdir ./ -outfile cypher-notepad-3.0-macos.app -appclass org.eclipse.jdt.internal.jarinjarloader.JarRsrcLoader -description "The Text Editor that provides hybrid encryption" -name "Cypher Notepad" -description "A Java-based, plain-text editor with hybrid encryption." -vendor "Dong-Geon Lee" -BappVersion=3.0 -Bicon="CypherNotepad.icns" -Bmac.category=Utilities -BlicenseType="Free"
```

2. Minimize bundled JRE. (Use the Python script below.)
   - Java 8 does not support `jlink`.

4. Make .dmg file using the command below.
```
create-dmg \
  --volname "Application Installer" \
  --volicon "CypherNotepad.icns" \
  --background "dmg_backgroud.png" \
  --window-pos 200 120 \
  --window-size 570 390 \
  --icon-size 100 \
  --icon "Cypher Notepad.app" 145 200 \
  --hide-extension "Cypher Notepad.app" \
  --app-drop-link 430 200 \
  --no-internet-enable \
  "test_cypher-notepad-3.0-apple-silicon.dmg" \
  "./intel/Cypher Notepad.app"
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
