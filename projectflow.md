# Project Flow
## Intro
1. Create project template by executing `template.py` file
2. Write the code on setup.py and pyproject.toml file to import local packages
3. Create a virtual env, activate it and install the requirements from requirements.txt
#### Commands(For Windows)
   ```bash
   python -m venv venv
   venv\Scripts\activate
   //add required modules to requirements.txt
   "pip install -r requirements.txt"
   ```
4. Do a "pip list" on terminal to make sure you have local packages installed.