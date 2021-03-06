# Download-files-in-Google-Drive-with-WGET-command-line

The command line below describes how to download any large file or data from Google Drive with a command line in terminal.
It is a bit tricky since large files need confirmation when downloading.

### Step 1. Get link and FILEID of the file in Google Drive
Skip if you already know the link.  
Right click the file and select "get sharable link". (The link will be copied to the clipboard automatically.)  
FILEID can be found in the link following ``drive.google.com/open?id=``.  

### Step 2. Open terminal and run the command using WGET
``wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=FILEID' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=FILEID" -O FILENAME && rm -rf /tmp/cookies.txt``  
ㄴ This line is originally from Alexander B (@beliys).

### Step 3. Exercise
Let's say you want to download a file named "img_align_celeba.zip" from the celebA dataset (Large-scale CelebFaces Attributes Dataset)  
Step 1. Get the link: ``https://drive.google.com/open?id=0B7EVK8r0v71pZjFTYXZWM3FlRnM``  
Step 2. Run this: ``wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=0B7EVK8r0v71pZjFTYXZWM3FlRnM' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=0B7EVK8r0v71pZjFTYXZWM3FlRnM" -O img_align_celeba.zip && rm -rf /tmp/cookies.txt``  
