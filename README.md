# OpenPose-Background-Process
This is an background process based on OpenPose's example wrappers.

Please note: This wrapper was based on an August 1st, 2017 clone of the OpenPose repo. 

mywrapper.cpp is based on the OpenPose example wrapper, 1_user_asynchronous.cpp. It creates a background daemon so as to run in the background monitoring a single directory path for new images to process. These images are processed as normal and moved to the output directory. The old images are then deleted.

Notes:
- skeleton_daemon() completely wraps the background daemon functionality. Comment out the call to this function in main() if you want the wrapper to run in the foreground and print out debug info.
- UserInputClass is used to monitor for new "jpg" files. (Change to add other image types.) These files are collected for processing and the originals are deleted from the directory path so as not be processed again.
- getFilesOnDirectory() inside fileSystem.cpp was changed to not throw an error() if not files are found, but rather just return an empty vector. This allows the background daemon to continue monitoring for new images without errors.
