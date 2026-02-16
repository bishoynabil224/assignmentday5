1-	 Create a directory structure in your home folder named webapp-deploy :
-	mkdir -p ~/webapp-deploy/{config,bin,backup}

2-	Inside ~/webapp-deploy/config/, create a file named app_settings.conf.
-	touch ~/webapp-deploy/config/app_settings.conf
      
3-	Add the following content to it:
     DATABASE_HOST=localhost  
     DATABASE_PORT=3306

-	vim ~/webapp-deploy/config/app_settings.conf
-	cat ~/webapp-deploy/config/app_settings.conf
   
4-	Create a hard link named production_settings.conf inside the ~/webapp-deploy/backup/ directory that points to the original app_settings.conf.
-	ln ~/webapp-deploy/config/app_settings.conf ~/webapp- deploy/backup/production_settings.conf  
  
5-	Checking the inode numbers of both files. Save the output of the inode verification command to a file named hardlink_proof.txt.
-	ll ~/webapp-deploy/config/app_settings.conf ~/webapp-deploy/backup/production_settings.conf >> hardlink_proof.txt       

6-	Create a symbolic link named current_config inside ~/webapp-deploy/bin/ that points to the original ~/webapp-deploy/config/app_settings.conf file.
-	ln -s ~/webapp-deploy/config/app_settings.conf ~/webapp-deploy/bin/current_config

7-	Verify the symlink works by displaying the contents of current_config using cat. Append this verification output to a file named symlink_proof.txt.
-	cat ~/webapp-deploy/bin/current_config >> symlink_proof.txt

8-	Create a tar archive (uncompressed) named config_backup.tar containing only the contents of the ~/webapp-deploy/config/ directory.
-	tar -cvf config_backup.tar ~/webapp-deploy/config/*


9-	Store this archive in the ~/webapp-deploy/backup/ directory
-	mv config_backup.tar ~/webapp-deploy/backup/

10-	 Verify the archive contains the expected files by listing its contents without extracting. Save this listing to a file named archive_contents.txt.
-	tar -tf ~/webapp-deploy/backup/config_backup.tar >> archive_contents.txt.

11-	 Create a gzip-compressed tar archive webapp_deploy.tar.gz containing all contents of the entire ~/webapp-deploy/ directory (including config, bin, backup, and all files).
-	tar -cvzf webapp_deploy.tar.gz ~/webapp-deploy/

12-	Store this compressed archive in your home directory.
-	mv webapp_deploy.tar.gz ~/

13-	 Use a single command to display the sizes of both: o ~/webapp-deploy/backup/config_backup.tar o ~/webapp-deploy/webapp_deploy.tar.gz (after moving it) Save this size comparison output to a file named size_comparison.txt.
-	ll -h ~/webapp-deploy/backup/config_backup.tar ~/webapp-deploy/webapp_deploy.tar.gz > size_comparison.txt


