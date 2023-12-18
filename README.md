# Rotate-the-var-log-directory-periodically

Step 1: Create Configuration File for /var/log

    sudo nano /etc/logrotate.d/varlog


Step 2: Add the Following Content to the File

    /var/log/* {
    weekly
    missingok
    rotate 4
    compress
    delaycompress
    notifempty
    create 640 root adm
    sharedscripts
    postrotate
        /bin/systemctl restart rsyslog
    endscript
    }

Step 3: Check the Logrotate Configuration

    sudo logrotate -d /etc/logrotate.conf

Step 4: Verify the Results

Check the 

    /var/log/syslog 
    
or 

    /var/log/messages
    
        
logs to ensure that logrotate is functioning correctly. If there are any errors, error messages will be recorded in these log files.

          


