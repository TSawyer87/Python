Instead of displaying the log messages to the screen, you can write them to a text file. The logging.basicConfig() function takes a filename keyword argument, like so:

import logging  
logging.basicConfig(filename='myProgramLog.txt', level=logging.DEBUG, format='  
%(asctime)s -  %(levelname)s -  %(message)s')

The log messages will be saved to _myProgramLog.txt_. While logging messages are helpful, they can clutter your screen and make it hard to read the program’s output. Writing the logging messages to a file will keep your screen clear and store the messages so you can read them after running the program. You can open this text file in any text editor, such as Notepad or TextEdit.