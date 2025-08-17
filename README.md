# AYA Rapihin Folder

AYA Rapihin Folder is a Python-based GUI application designed to automatically organize files and folders in a specified directory. It allows users to sort files either by **date** (Year/Month/Day) or by **file type** (e.g., Images, Documents, Videos). The application runs as a background service, continuously monitoring and organizing files in the selected folder.

## Features
- **File Organization**: Organize files and folders by:
  - **Date**: Based on the last modified date, sorted into a `Year/Month/Day` folder structure.
  - **File Type**: Grouped by file extensions (e.g., `IMAGES`, `DOCUMENTS`, `VIDEO`).
- **User-Friendly GUI**: Built with Tkinter, featuring a simple interface to select a folder and choose an organization method.
- **Background Service**: Automatically organizes files at regular intervals while the service is running.
- **Custom Icon**: Uses a custom `AYA.ico` icon for the application window and executable (Windows).
- **Cross-Platform**: Primarily designed for Windows but adaptable for other platforms with minor modifications.
  
## Download
Get the latest release: [Download Aya_Rapihin_Folder](https://www.mediafire.com/file/kwjgtdmd19usnam/AYA_Rapihin_Folder.exe/file))

## Requirements
- Python 3.6 or later
- Tkinter (included with standard Python installations; may require `python3-tk` on Linux)
- `AYA.ico` icon file (included in the project directory for the application icon)
- PyInstaller (optional, for building the executable)

## Setup Instructions

### 1. Clone or Download the Repository
Download the project files, including `file_organizer.py` and `AYA.ico`, to your local machine.

### 2. Set Up a Virtual Environment
Create and activate a virtual environment to isolate dependencies:
```bash
cd /path/to/project
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Verify Tkinter
Ensure Tkinter is available. It’s included with Python, but on Linux, you may need to install it:
- **Ubuntu/Debian**:
  ```bash
  sudo apt-get install python3-tk
  ```
- **Fedora**:
  ```bash
  sudo dnf install python3-tkinter
  ```

### 4. Run the Application
Run the script directly:
```bash
python file_organizer.py
```

### 5. Build a One-File Executable (Optional)
To create a standalone executable, use PyInstaller with the provided `file_organizer.spec`:
```bash
pip install pyinstaller
pyinstaller file_organizer.spec
```
The executable (`AYA_Rapihin_Folder.exe` on Windows) will be in the `dist` directory.

Alternatively, build directly with:
```bash
pyinstaller --onefile --add-data "AYA.ico;." --icon=AYA.ico --name=AYA_Rapihin_Folder --noconsole file_organizer.py
```
- On Linux/macOS, use `:` instead of `;` in `--add-data`, e.g., `--add-data "AYA.ico:."`.

## Usage
1. **Launch the Application**: Run `file_organizer.py` or the compiled executable.
2. **Select a Folder**: Click "Browse" to choose a directory to organize.
3. **Choose Organization Method**:
   - Select "By Date (Year/Month/Day)" to organize files into a date-based folder structure.
   - Select "By File Type" to group files by their extensions (e.g., `IMAGES`, `PDF`, `VIDEO`).
4. **Start the Service**: Click "Start Service" to begin automatic organization. The service will run in the background, checking and organizing files every 10 seconds.
5. **Stop the Service**: Click "Stop Service" to halt the background organization process.
6. **Monitor Status**: The status label at the bottom shows whether the service is "Running" (green) or "Stopped" (red).

## Project Structure
```
project_directory/
├── file_organizer.py    # Main Python script
├── AYA.ico              # Application icon
├── file_organizer.spec  # PyInstaller build specification
├── venv/                # Virtual environment directory
├── dist/                # Output directory for executable (after building)
└── README.md            # This file
```

## Notes
- **Icon**: Ensure `AYA.ico` is in the project directory. If the icon doesn’t appear, verify its path using the debug print in `_get_resource_path`.
- **Windows-Specific Features**: The application sets a custom Windows application ID for taskbar grouping. This is ignored on non-Windows platforms.
- **Cross-Platform**: For Linux/macOS, you may need to replace `.ico` with a `.png` icon and modify `_set_app_icon` to use `PhotoImage`:
  ```python
  if sys.platform.startswith('win'):
      window.iconbitmap(self._get_resource_path('AYA.ico'))
  else:
      icon = PhotoImage(file=self._get_resource_path('AYA.png'))
      window.iconphoto(True, icon)
  ```
  Update the PyInstaller `--add-data` option to include `AYA.png`.
- **Error Handling**: Errors during file organization are printed to the console. Check logs for issues with icon loading or file operations.

## Troubleshooting
- **Icon Not Displayed**: Ensure `AYA.ico` is in the project directory and included in the PyInstaller bundle. Check console logs for warnings.
- **Tkinter Not Found**: Install `python3-tk` on Linux or verify your Python installation.
- **PyInstaller Issues**: Update PyInstaller (`pip install --upgrade pyinstaller`) or check the `dist` directory for the executable.
- **File Organization Errors**: Ensure the selected folder is accessible and not locked by another process.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details (if applicable).

## Contact
For issues or suggestions, please contact the developer at [etriowidodo@mail.com].
