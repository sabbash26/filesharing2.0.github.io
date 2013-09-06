filesharing2.0.github.io
========================

A File Sharing Service Based Upon BTSync

________________________________________________________________________________


Installation and Implementation of BTSync on Ubuntu server:

Step 1: Installation
	cd /tmp
	mkdir btsync
	cd btsync
	wget http://btsync.s3-website-us-east-1.amazonaws.com/	btsync_x64.tar.gz .
	tar -xvzf btsync_x64.tar.gz

Once you have extracted the executable then you can move the exe file anywhere you would like. 

Step 2: Setup Password Access
In order to do so you must make a .config file in the btsync folder. Here is a sample of a btsync.config file.


{ 
  "device_name": "My Sync Device",
  "listening_port" : 0,                       // 0 - randomize port
  
/* storage_path dir contains auxilliary app files
   if no storage_path field: .sync dir created in the directory 
   where binary is located.
   otherwise user-defined directory will be used 
*/
  "storage_path" : "/home/user/.sync",

// uncomment next line if you want to set location of pid file
// "pid_file" : "/var/run/syncapp/syncapp.pid",


  "check_for_updates" : true, 
  "use_upnp" : true,                              // use UPnP for port mapping


/* limits in kB/s
   0 - no limit
*/
  "download_limit" : 0,                       
  "upload_limit" : 0, 

/* remove "listen" field to disable WebUI
   remove "login" and "password" fields to disable credentials check
*/
  "webui" :
  {
    "listen" : "0.0.0.0:8888",
    "login" : "admin",
    "password" : "password"
  }

/* !!! if you set shared folders in config file WebUI will be DISABLED !!!
   shared directories specified in config file
   override the folders previously added from WebUI.
*/
/*
  ,
  "shared_folders" :
  [
    {
//  use --generate-secret in command line to create new secret
      "secret" : "MY_SECRET_1",                   // * required field
      "dir" : "/home/user/bittorrent/sync_test", // * required field

//  use relay server when direct connection fails
      "use_relay_server" : true,
      "use_tracker" : true, 
      "use_dht" : false,
      "search_lan" : true,
//  enable sync trash to store files deleted on remote devices
      "use_sync_trash" : true,
//  specify hosts to attempt connection without additional search     
      "known_hosts" :
      [
        "192.168.1.2:44444",
        "myhost.com:6881"
      ]
    }
  ]
*/

// Advanced preferences can be added to config file.
// Info is available in BitTorrent Sync User Guide.

}


In this file you simply have to change the "login" and "password."  It is currently set to its default which is admin and password. 

Step 3: RUN

youripaddress:8888/gui





IMPORTANT FACETS OF BTSYNC

Versioning

By default it creates and stores all the old copies of edited ﬁles for the period of 30 days (this period can be changed in General advanced preferences - sync_trash_ttl). All the versions are stored in the hidden .SyncArchive directory within your sync folder that you can open by right click on the sync folder and choosing ‘Open SyncArchive’.

If you have any other question you can find the BTSync Users Guide online.
