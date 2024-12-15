# Python Development

 I am sharing a program that I wrote as a project with Zero to Mastery Academy. Thuis is a Python utility designed to help users organize files within a specified directory. 
 It categorizes files into designated subdirectories based on their types, 
 making it easier to manage and locate files. This project is particularly useful for users who want to maintain a tidy file structure on their local machines.

## Getting Started

These instructions will help you set up the Clean_Sweep.py project on your local machine for development and testing purposes.

### Prerequisites

The things you need before installing the software.

* Before installing the software, ensure you have the following:
* Python 3.x installed on your machine.
* Basic understanding of Python programming.
* Access to the command line or terminal.
  
### Installation

```
$ Clone the repository or download the Clean_Sweep.py file.
$ Navigate to the directory where Clean_Sweep.py is located.
$ Run the script using Python.
```
Follow these steps to get the development environment up and running:

```
$ First step
$ Another step
$ Final step
```

## Usage

Here are a few examples of how to use the Clean_Sweep.py script:

```
$ python Clean_Sweep.py

```
When prompted, enter the full path to the target folder you want to clean up. The script will then organize the files accordingly.

# Code Explanation
## User Input for Directory

The script begins by prompting the user to enter the path of the directory they want to clean up:
```
while True:
    root_dir = Path(input('Please enter the full path to the target folder:'))

    if root_dir.exists():
        break

    print('Invalid path. Please enter the full path of a valid folder on your machine.')
```
This loop continues until the user provides a valid directory path. The Path object checks if the entered path exists.
Creating Subdirectories

### Creating Subdirectories

Once a valid directory is confirmed, the script creates a main folder called closet and three subfolders for organizing files:
```
closet_dir = root_dir / 'closet'
closet_dir.mkdir(exist_ok=True)

text_dir = closet_dir / 'text_files'
text_dir.mkdir(exist_ok=True)

csv_dir = closet_dir / 'csv_files'
csv_dir.mkdir(exist_ok=True)

folders_dir = closet_dir / 'folders'
folders_dir.mkdir(exist_ok=True)
```
These subdirectories will hold text files, CSV files, and other folders, respectively. The mkdir method creates these directories if they do not already exist.

### Organizing Files

The script then iterates through each item in the root directory and organizes them:

```
for item in root_dir.iterdir():
    if item == closet_dir:
        continue
    elif item.is_file() and item.suffix == '.txt':
        shutil.move(item, text_dir / item.name)
    elif item.is_file() and item.suffix == '.csv':
        shutil.move(item, csv_dir / item.name)
    elif item.is_dir() and 'temp' in item.name:
        shutil.rmtree(item)
    elif item.is_dir():
        shutil.move(item, folders_dir / item.name)
    else:
        shutil.move(item, closet_dir / item.name)
```
This code checks the type of each item and moves it to the appropriate subdirectory. If an item is a temporary directory (containing 'temp' in its name), it is deleted. Other files are moved to their respective folders based on their extensions.

## Completion Message

Finally, the script informs the user that the cleanup process is complete:

```
print('Folder cleanup complete!')
```
##Deployment

To deploy this script on a live or release system, ensure that the environment has Python installed and that the necessary permissions are granted for file operations.

##Server

* Live: Ensure the script runs in a controlled environment where users can input paths.
* Release: Test the script thoroughly before making it available to users.
* Development: Use a local machine for testing and debugging.

##Branches

* Master: The main branch containing the stable version of the script.
* Feature: Branches for new features or enhancements.
* Bugfix: Branches for fixing issues or bugs.

##Additional Documentation and Acknowledgments

* Project folder on server: [Link to project folder]
* Confluence link: [Link to documentation]
* Asana board: [Link to project management board]

This documentation provides a comprehensive overview of the Clean_Sweep.py project, detailing its purpose, usage, and implementation.
