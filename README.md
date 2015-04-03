# MagicDownload
Download images with a dynamic link by utilizing Dropbox with Squarespace.

This repository allows a Squarespace Gallery Collection for the Wexley Template to automatically create a download link for each image by connecting a Dropbox account to a Squarespace site.  

Essentially you will be creating 2 folders in your dropbox account: one to display images formatted for the web in your Gallery Collections and a second which are the ones for download.  The images in both folders MUST be the same name.  If image1.jpg is in the first folder, than image1.jpg must be in the public folder so it can be linked for download correctly.

You can have multiple folders in the Squarespace Apps folder to help organize your photos by collections.

You can only have 1 public folder for download, so you will need to upload all of your downloadable images to this public folder.

##Example
Let's say you are a photographer shooting a 3 day conference.  You can organize your photos by days, so you'll want to create 3 folders for Squarespace:

Folder 1 = Day 1 (photos formatted for web go inside this folder)
Folder 2 = Day 2 (photos formatted for web go inside this folder)
Folder 3 = Day 3 (photos formatted for web go inside this folder)

You want users to be able to download them (i.e. press, magazine, etc) and you need high quality files for download.  You will then upload all of your downloadable files (from all 3 folders) in your Public/Shared folder.

All files in the shared folder must have the same name as in their respected Squarespace folders.  This is because of the way the 'Download' text is linked with JSONT.  It replaces the end of the shared folder url with the title of the image.  So if you have image1.jpg inside of Folder 1, then you need to have image1.jpg inside of the shared folder.



##What You'll Need
- Dropbox account with a Folder for your images and a public/shared folder for the images to be downloaded.
- Squarespace Account with Developer Mode Enabled
- Wexley Template installed
- SFTP Client and Program to edit html/css/json (recommend Cyberduck and Sublime text or Coda 2)


#IMPORTANT
Save/backup your template files to your computer before you make any modifications! You can use git clone or login via SFTP and save your template files by dragging and dropping them to a folder on your computer.  For more information on how to connect to your Squarespace Developer Site see here:

http://developers.squarespace.com/initial-setup


#Instructions

Part 1 - Setting up Dropbox with Squarespace
- Create a Dropbox Account
- Connect your Dropbox account to Squarespace by following this guide here:  http://help.squarespace.com/guides/using-dropbox-with-squarespace
- Create Folders for Squarespace to use (explained in the above guide) Each folder of images will show up as Gallery Pages in your 'Not Linked' section in Squarespace.
- Login to Dropbox.com and create a shared/public folder in Dropbox called 'public' -- visit this link for help https://www.dropbox.com/help/16
- Now create a sub-folder called 'pressdownload' or something relevant.  This is the folder where you will upload ALL of the images you want to share publicly with the download link.
- Once you create this subfolder, you'll need to get the static URL for that.  Hover over the folder name and click 'Share' and copy the link in 'Link to folder' as explained in this guide: https://www.dropbox.com/en/help/167 

*Save this URL! You will need it for Part 2.

Part 2 - Adding the download text to the gallery pages
- Make sure the Wexley template is installed and live for your site.
- Download the gallery.list repository and open the file in Sublime Text or another relevant program.
- Locate line 47 and replace the first # in the url for the share folder to link the download text to that folder.
*make sure you keep ?dl=0#lh:null-{@} as this links directly to your images and dynamically changes the download text link with {@}.
- Save the updated file.

Part 3 - Upload the gallery.list
- Connect to the Developer Platform via SFTP
- Open the Collections folder and replace the gallery.list file with the new gallery.list you just updated 
- Save and make sure this file is updated to SFTP.  Refresh your browser, click on an image in your gallery to display image in lightbox and you'll see 'Click to Download High-Quality Version' below the image.  This link should then link to the image placed in your Shared/Public folder.


##Troubleshooting Tips & Tricks
- If there is no Folder with your account name, you will need to create this as described when you first connect your account.  
- Each folder you create and fill with images will become it's own gallery page in Squarespace.
- Images that you use for your Dropbox folder to display and offer as a download MUST have the SAME NAME.
- If you want to modify the text, edit the CSS at the top of the gallery.list file.
