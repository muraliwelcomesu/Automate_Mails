# Automate_Mails
Sending email instructions to perform desktop operations like fetching a file , downloading files, Retreiving passwords.

Main.py 
	job that executes schedule_tasks every one minute to call ReadMails.get_mail and SendMails.pending_items

ReadMails.get_mail:
	Check the unread mails with specific subject and save the message (received in specific format ) in an excel
	at a predefined location. Save the attachments if any in specific folder.

SendMails.pending_items
	Open the excel which was updated through ReadMails.get_mail program.
	Get the unprocessed records.
	The messages received will be in specific formats:
	1) GET <Filename> <order>  < Get the file name from te local machine and sent it back to the sender > 
	2) DOWNLOAD <url separated by ,> << Download the videos from the url sent > 
	3) FIND <name>   << Fetch from the password files the value for the key sent > 
Password_Retreive.py:
	An excel at a predefined location contains the key and values . Whenever any request is received with FIND key, 
	the corresponding value is fetched and sent back as result. The results can be sent as mails or sms.
way2sms.py
	For sending the results as sms this program is used.

Task_Schedular_svc
	The job that exceutes schedule_tasks in main.py is defined as a windows service which can be invoked/start as per 
	convenience.
Mail_Utils.py 
	This has programs for creating zip files, creating html file from a dictionary, 
        sending zip file as attachment to mail, searching for a file in local system, converting file to dictionary.
	
