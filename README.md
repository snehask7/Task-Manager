# Task-Manager  
  
alias mongod="/c/Program\ files/MongoDB/Server/4.4/bin/mongod.exe"
alias mongo="/c/Program\ Files/MongoDB/Server/4.4/bin/mongo.exe"  
  
Unlike other answers this will ..

START THE SERVICE AUTOMATICALLY ON SYSTEM REBOOT / RESTART

MongoDB Install
Windows
(1) Install MongoDB

(2) Add bin to path

(3) Create c:\data\db

(4) Create c:\data\log

(5) Create c:\data\mongod.cfg with contents ..

systemLog:
    destination: file
    path: c:\data\log\mongod.log
storage:
    dbPath: c:\data\db
(6) To create service that will auto start on reboot .. RUN AS ADMIN ..

sc.exe create MongoDB binPath= "\"C:\Program Files\MongoDB\Server\3.4\bin\mongod.exe\" --service --config=\"C:\data\mongod.cfg\"" DisplayName= "MongoDB" start= "auto"
(7) Start the service .. RUN AS ADMIN ..

net start MongoDB
IMPORTANT: Even if this says 'The MongoDB service was started successfully' it can fail

To double check open Control Panel > Services, ensure the status of the MongoDB service is 'Running'  
  
