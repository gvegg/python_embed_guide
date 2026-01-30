# Python Embeddable Package Setup Guide for Windows

Follow these steps to set up the Python embeddable package with `pip` and `virtualenv` on Windows.

### 1. Download Python
Go to the official Python releases page and download the **Windows embeddable package** (zip file) suitable for your architecture (x86 or x64).
*   **Link:** [https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/)

Extract the downloaded zip file to your desired folder (this will be referred to as the **root folder**).

### 2. Download pip
Go to the PyPI pip project page and download the `.whl` file (Wheel) from the "Download files" section.
*   **Link:** [https://pypi.org/project/pip/#files](https://pypi.org/project/pip/#files)

### 3. Extract pip manually
1.  Navigate to your Python **root folder** (where `python.exe` is located).
2.  Create a new folder named `Lib`. Inside that, create a folder named `site-packages`.
    *   *Path structure:* `\YourPythonFolder\Lib\site-packages`
3.  Open the pip `.whl` file you downloaded in Step 2 (use an archive manager like 7-Zip or WinRAR).
4.  Extract all files from the `.whl` archive into the `Lib\site-packages` directory.

### 4. Configure the `._pth` file
Before running python, you must enable site-packages.

1.  Find the configuration file in your root folder. It is named `pythonXX._pth` (e.g., `python311._pth` or `python310._pth`).
2.  Open it with a text editor (Notepad).
3.  Add `Lib\site-packages` to the list of paths.
4.  Uncomment (remove `#`) the line `import site`.

The file should look something like this:
```text
python311.zip
.
Lib\site-packages
# ... other lines ...
import site
```

### 5. Install setuptools and virtualenv
Open your command prompt (cmd) inside the Python root folder and run the following command:

```powershell
.\python.exe -m pip install setuptools virtualenv
```

### 6. Finalize pip installation
To properly register `pip` in the path and ensure scripts (executables) are generated correctly, perform a forced reinstall:

```powershell
.\python.exe -m pip install --force-reinstall pip
```
