import os
import shutil

SOURCE_FILE = r"C:\Users\willi\Downloads\RRA.png"
BACKUP_DIR = r"C:\Users\willi\Downloads\backup"
BACKUP_FILE = os.path.join(BACKUP_DIR, "RRA.png")

def backup_file():
    # Create backup directory if it doesn't exist
    os.makedirs(BACKUP_DIR, exist_ok=True)

    # Copy the file
    shutil.copy2(SOURCE_FILE, BACKUP_FILE)
    print("Backup complete.")

if __name__ == "__main__":
    backup_file()


import easygui

easygui.msgbox("Hello William! This is your EasyGUI EXE script!", title="EasyGUI Test")
