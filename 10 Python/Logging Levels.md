#Debugging 
_Logging levels_ provide a way to categorize your log messages by importance. There are five logging levels, described in [Table 11-1](http://automatetheboringstuff.com/2e/chapter11/#calibre_link-1193) from least to most important. Messages can be logged at each level using a different logging function.

**Table 11-1:** Logging Levels in Python

  
|**Level**|**Logging function**|**Description**|
|---|---|---|
|DEBUG|logging.debug()|The lowest level. Used for small details. Usually you care about these messages only when diagnosing problems.|
|INFO|logging.info()|Used to record information on general events in your program or confirm that things are working at their point in the program.|
|WARNING|logging.warning()|Used to indicate a potential problem that doesn’t prevent the program from working but might do so in the future.|
|ERROR|logging.error()|Used to record an error that caused the program to fail to do something.|
|CRITICAL|logging.critical()|The highest level. Used to indicate a fatal error that has caused or is about to cause the program to stop running entirely.|

Your logging message is passed as a string to these functions. The logging levels are suggestions. Ultimately, it is up to you to decide which category your log message falls into. Enter the following into the interactive shell:

>>> import logging  
>>> logging.basicConfig(level=logging.DEBUG, format=' %(asctime)s -  
%(levelname)s -  %(message)s')  
>>> logging.debug('Some debugging details.')  
2019-05-18 19:04:26,901 - DEBUG - Some debugging details.  
>>> logging.info('The logging module is working.')  
2019-05-18 19:04:35,569 - INFO - The logging module is working.  
>>> logging.warning('An error message is about to be logged.')  
2019-05-18 19:04:56,843 - WARNING - An error message is about to be logged.  
>>> logging.error('An error has occurred.')  
2019-05-18 19:05:07,737 - ERROR - An error has occurred.  
>>> logging.critical('The program is unable to recover!')  
2019-05-18 19:05:45,794 - CRITICAL - The program is unable to recover!

The benefit of logging levels is that you can change what priority of logging message you want to see. Passing logging.DEBUG to the basicConfig() function’s level keyword argument will show messages from all the logging levels (DEBUG being the lowest level). But after developing your program some more, you may be interested only in errors. In that case, you can set basicConfig()’s level argument to logging.ERROR. This will show only ERROR and CRITICAL messages and skip the DEBUG, INFO, and WARNING messages.