# Make a CLI tool in python

### 1. Structure Your Project

Organise your project directory like this:

```
your_project/
├── your_script.py
├── setup.py
├── README.md
├── LICENSE (optional)
├── requirements.txt (optional)
└── your_package/
    ├── __init__.py
    └── your_script.py
```

* your_script.py: This contains the logic of your tool.
* __init__.py: Makes your_package a Python package.

---

### 2. Add an Entry Point to Your Script

Modify your script (your_script.py) to include a function that acts as the main entry point. For example:

```python
import argparse

def main():
    parser = argparse.ArgumentParser(description="Description of your CLI tool")
    parser.add_argument('name', help="Name to greet")
    args = parser.parse_args()
    print(f"Hello, {args.name}!")

```

---

### 3. Create setup.py for Packaging

This file tells Python how to install your project. Here’s an example:

```python
from setuptools import setup, find_packages

setup(
    name='your-cli-tool',  # Replace with your tool's name
    version='1.0.0',
    packages=find_packages(),
    install_requires=[],  # Add dependencies if needed
    entry_points={
        'console_scripts': [
            'your-cli-tool=your_package.your_script:main',  # 'command=module:function'
        ],
    },
    author="Your Name",
    author_email="your.email@example.com",
    description="A brief description of your tool",
    long_description=open('README.md').read(),
    long_description_content_type='text/markdown',
    url="https://github.com/your-repo",
    classifiers=[
        'Programming Language :: Python :: 3',
        'License :: OSI Approved :: MIT License',
    ],
    python_requires='>=3.6',
)
```

---

### 4. Install the Tool Locally for Testing

From the root of your project directory, run:

`pip install -e .`

This installs the package in “editable” mode. You can now use the CLI tool as a command:

```bash
your-cli-tool Minas
# Output: Hello, Minas!
```


`pip install your-cli-tool`

and use it via the CLI command your-cli-tool.

---
5. To find the location of the installed script, run:

`which your-cli-tool`

This will show you the path to the script.

Then you can move the script to a directory in your PATH to use it from anywhere.