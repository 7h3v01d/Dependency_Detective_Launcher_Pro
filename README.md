# Dependency Detective (Launcher Pro)

## Description
Dependency Detective is designed to bridge the gap between raw source code and a fully configured development environment. Instead of manually maintaining a requirements.txt file, this tool uses static analysis (AST) to "detect" exactly what your project needs to run. It intelligently handles the common discrepancies between import names and package names (like cv2 vs. opencv-python) and provides a safe way to run projects in isolated, temporary environments. Whether you're cleaning up an old project or setting up a new one, it ensures that "missing module" errors are a thing of the past.

⚠️ **LICENSE & USAGE NOTICE — READ FIRST**

This repository is **source-available for private technical evaluation and testing only**.

- ❌ No commercial use  
- ❌ No production use  
- ❌ No academic, institutional, or government use  
- ❌ No research, benchmarking, or publication  
- ❌ No redistribution, sublicensing, or derivative works  
- ❌ No independent development based on this code  

All rights remain exclusively with the author.  
Use of this software constitutes acceptance of the terms defined in **LICENSE.txt**.

---

## Key Features

- Static Import Analysis: Scans your project using Abstract Syntax Trees (AST) to identify external dependencies without ever needing to execute your code.
- Intelligent Package Mapping: Includes a robust dictionary that automatically maps common import aliases to their actual installable package names (e.g., bs4 → beautifulsoup4, yaml → PyYAML, PIL → Pillow).
- Virtual Environment Orchestration:
  - Persistent Venv: Create a local ./venv and install all discovered dependencies with a single command.
  - Temporary Venv: Spin up a fully isolated, temporary environment that is automatically deleted after your script finishes execution.
  - Automated Requirements Generation: Instantly generate a requirements.txt file. The tool pins versions from your local environment or queries the PyPI API to find the latest stable version for any missing packages.
- Pyproject.toml Integration: Supports custom configuration via the pyproject.toml file, allowing you to define project-specific exclusion rules and custom package mappings.
- Dry Run Mode: Preview exactly which dependencies will be detected and installed before any changes are made to your system.
- Rich CLI Experience: Built with the Rich library to provide a professional, color-coded terminal interface with clear progress logging and beautiful help menus.
- Smart Root Discovery: Automatically identifies your project root by searching upwards for .git or pyproject.toml markers to ensure accurate file scanning.

---

## Installation

****Prerequisites****
- Python 3.10+ (recommended for full standard library detection).

### Setup
Clone the repository:
```Bash
git clone https://github.com/yourusername/dependency-detective.git
cd dependency-detective
```
Install the core tool dependencies:
```Bash
pip install requests rich rich-argparse tomli
```
Usage
You can use the detective to run a specific file or manage your project's environment.

```Bash
python launcher_pro.py [PROJECT_FILE] [OPTIONS]
```
---

## Common Commands
Run and Install: Scan for missing deps, prompt for installation, and then run:
```Bash
python launcher_pro.py my_script.py
```
Generate Requirements: Create a requirements.txt based on static analysis:
```Bash
python launcher_pro.py --generate-requirements
```
Isolated Execution: Run a script in a temporary environment without cluttering your system:

```Bash
python launcher_pro.py my_script.py --temp-venv
```
Setup Local Venv: Build a persistent ./venv for the current project:

```Bash
python launcher_pro.py --venv
```
---

## Project Structure
launcher_pro.py: The main executable containing the AST scanner, PyPI resolver, and environment management logic.

## Contribution Policy

Feedback, bug reports, and suggestions are welcome.

You may submit:

- Issues
- Design feedback
- Pull requests for review

However:

- Contributions do not grant any license or ownership rights
- The author retains full discretion over acceptance and future use
- Contributors receive no rights to reuse, redistribute, or derive from this code

---

## License
This project is not open-source.

It is licensed under a private evaluation-only license.
See LICENSE.txt for full terms.
