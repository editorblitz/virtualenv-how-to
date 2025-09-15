# Setting up a Virtual Environment in Python using VSCode's Terminal

This guide will walk you through the process of setting up a virtual environment for your Python project using Visual Studio Code's integrated terminal.

## Steps:

1. Open your project folder in VSCode.

2. Open the terminal in VSCode (you can use the keyboard shortcut `Ctrl+`` or go to View > Terminal).

3. Navigate to your project directory if you're not already there.

5. Create a new virtual environment:
   ```
   python -m venv newenv
   ```
   Replace "newenv" with whatever name you want to give your virtual environment.

6. Activate the virtual environment:
   - On Windows:
     ```
     newenv\Scripts\activate
     ```
   - On macOS and Linux:
     ```
     source newenv/bin/activate
     ```

7. You should now see the name of your virtual environment in parentheses at the beginning of your terminal prompt, indicating it's active.

8. Install your required packages:
   ```
   pip install package_name
   ```

9. Or install via requirements.txt:
      ```
   python -m pip install -r requirements.txt
   ```

#### To see just the path
  (Get-Command python).Source
  (Get-Command pip).Source

8. When you're done working in the virtual environment, you can deactivate it:
   ```
   deactivate
   ```

## Troubleshooting
1. If you installed modules and it cannot find them, it may have installed for a different python install.
2. Always check which pip/python you're using
   ```
   python --version
   ```
   Check version and location
    ```
   gcm python
    ```
   Also check pip:
   ```
   gcm pip
   ``` 
4. To see just the path:
```
  (Get-Command python).Source
  (Get-Command pip).Source
   ```
5. Sometimes you need to back up completely to get it working right
   Update Python and recreate virtual environment
 ### Remove old virtual environment
   ```
   Remove-Item -Recurse -Force newenv
   ``` 
  ### Download and install version of Python you need, or check what versions are available
   ```
   py -0
   ``` 
  For example it will show:
   -V:3.11 *        Python 3.11 (64-bit)
   -V:3.10          Python 3.10 (64-bit)
   -V:3.7-32        Python 3.7 (32-bit)
   -V:2.7           Python 2.7
   
  ### Then use the specific version of Python to crease the environment 
   ```
   py -3.11 -m venv newenv311
   newenv311\Scripts\Activate.ps1
   newenv\Scripts\Activate.ps1
   pip install -r requirements.txt
   ``` 
  ### Always Use Absolute Paths (Most Reliable)
   ```
   newenv\Scripts\pip.exe install pandas
   newenv\Scripts\python.exe script.py
   ``` 

6. Better Virtual Environment Workflow

### After Activate, immediately verify
  newenv\Scripts\Activate.ps1
  where python  # Should show newenv path
  where pip     # Should show newenv path

### If paths are wrong, deactivate and use absolute paths
Use python -m pip Instead of pip
### This ensures you're using the Python you think you are

  python -m pip install pandas
  # vs just
  pip install pandas  # Could go anywhere


## Other Tips

- Remember to add your virtual environment folder (myenv in this case) to your .gitignore file if you're using version control.

- After creating the virtual environment, you might want to select it as the Python interpreter for your VSCode workspace. You can do this by:
  1. Opening the Command Palette (Ctrl+Shift+P)
  2. Typing "Python: Select Interpreter"
  3. Choosing the interpreter path that includes your virtual environment name

This ensures that VSCode uses your virtual environment when running Python code in the editor.

## Why Use a Virtual Environment?

Virtual environments are isolated Python environments that allow you to install packages and dependencies specific to a project without affecting your system-wide Python installation. This helps in managing dependencies across different projects and ensures reproducibility.

## Troubleshooting

If you encounter any issues while setting up your virtual environment, consider the following:

- Ensure you have Python installed and added to your system PATH.
- Check that you're in the correct directory when creating and activating the virtual environment.
- If activation doesn't work, try using the full path to the activate script.


Python Version/Environment Differences

  What you experienced:

  - System terminal: Uses system-wide Python (wrong version)
  - IDE terminal: Uses your selected Python environment (correct version)

  Why this happens:

  1. PATH priority: System terminal uses whatever python is first in your PATH
  2. IDE integration: Your IDE (VS Code, PyCharm, etc.) activates the correct environment automatically
  3. Virtual environments: The (newenv311) prefix shows you're in a Python 3.11 virtual environment

  Solutions:

  Option 1: Use the IDE terminal (what you're doing)

  ✅ Recommended - Keep using the terminal that opened from your IDE

  Option 2: Manually activate environment in any terminal

  # Find your environment path first
  where python  # or which python on Mac/Linux

  # Then activate it
  # On Windows:
  C:\path\to\your\newenv311\Scripts\activate

  # On Mac/Linux:
  source /path/to/your/newenv311/bin/activate

  Option 3: Use full path to correct Python

  # Instead of: python import_data.py
  # Use: /full/path/to/newenv311/python import_data.py










For more detailed information, refer to the [official Python documentation on virtual environments](https://docs.python.org/3/tutorial/venv.html).
