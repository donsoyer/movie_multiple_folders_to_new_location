  # movie_multiple_folders_to_new_location
  movie_multiple_folders_to_new_location

import os
import shutil

def move_multiple_folders(src, dst):
    for folder in os.listdir(src):
        src_folder = os.path.join(src, folder)
        if os.path.isdir(src_folder):
            dst_folder = os.path.join(dst, folder)
            if not os.path.exists(dst_folder):
                os.makedirs(dst_folder)
            else:
                i = 1
                while os.path.exists(f"{dst_folder} ({i})"):
                    i += 1
                dst_folder = f"{dst_folder} ({i})"
                os.makedirs(dst_folder)

            for item in os.listdir(src_folder):
                s = os.path.join(src_folder, item)
                d = os.path.join(dst_folder, item)
                if os.path.isdir(s):
                    move_multiple_folders(s, d)
                else:
                    shutil.move(s, d)

def remove_empty_folders(folder):
    for root, dirs, files in os.walk(folder, topdown=False):
        for dir_name in dirs:
            folder_path = os.path.join(root, dir_name)
            if not os.listdir(folder_path):
                os.rmdir(folder_path)
                print(f"Removed empty folder: {folder_path}")

  #Usage:
source_folder = 'C:\\Users\\micha\\Downloads\\itch\\pythonKopiujDoNowychFolderów\\Stara lokacja'
destination_folder = 'C:\\Users\\micha\\Downloads\\itch\\pythonKopiujDoNowychFolderów\\Nowa lokacja'

move_multiple_folders(source_folder, destination_folder)
remove_empty_folders(source_folder)


#This script performs two main operations:

  #1.    Moving multiple folders:
  #The move_multiple_folders function moves all folders from the source location (src) to the destination location (dst).
  #If a folder with the same name already exists in the destination, it creates a new folder with a number in parentheses, e.g., folder (1).
  #It also moves all files and subfolders from the source folders to the corresponding destination folders.
  
  #2.   Removing empty folders:
  #The remove_empty_folders function scans the given location (folder) and removes all empty folders.
  #It prints a message for each empty folder that is removed.
          
          
  
  #Folder paths: Ensure that the paths to the source folder (source_folder) and the destination folder (destination_folder) are correct. Are you sure both paths exist and have the appropriate write permissions?
  
  #Escape characters in paths: In Python, you need to use double escape characters (\\) in Windows paths. For example:
  #source_folder = "C:\\Users\\micha\\Downloads\\itch\\pythonKopiujDoNowychFolderów\\Stara lokacja"
  #destination_folder = "C:\\Users\\micha\\Downloads\\itch\\pythonKopiujDoNowychFolderów\\Nowa lokacja"
  
  #Escape characters in paths for single quotes: If you use single quotes (') to define paths, remember that you need to use double escape characters inside them:
  #source_folder = 'C:\\Users\\micha\\Downloads\\itch\\pythonKopiujDoNowychFolderów\\Stara lokacja'
  #destination_folder = 'C:\\Users\\micha\\Downloads\\itch\\pythonKopiujDoNowychFolderów\\Nowa lokacja'
  
  #Check if the function is called: Ensure that you call the function move_multiple_folders(source_folder, destination_folder) in your code. Without calling the function, the code will not execute.
  
  
