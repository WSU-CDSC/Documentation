
# Cloud Storage Workflow for Archival Packages

# Contents
* [Overview](#overview)
  - [Core Scripts](#core-scripts)
* [Workflow Dependencies](#workflow-dependencies)
* [Workflow Steps and Scripts](#workflow-steps-and-scripts)
  - [Usage Workflow](#usage-workflow)
* [Download Workflow](#download-workflow)
  - [Using Cyberduck](#using-cyberduck)
  - [Other Methods](#other-methods)
* [Backblaze B2 Information](#b2-information)

## Overview:
The current workflow for migrating/storing digital materials into off-site cloud storage utilizes Ruby Scripts to prepare and upload data to the [Backblaze B2 Storage service](https://www.backblaze.com/b2/cloud-storage.html). As of writing, scripts have been tested in a Linux environment. Individual descriptions for the scripts can be found at the following links:

### Core scripts:
* [makemeta.rb](https://github.com/WSU-CDSC/microservices/blob/master/Resources/makemeta.md)
* [uploadaip.rb](https://github.com/WSU-CDSC/microservices/blob/master/Resources/uploadaip.md)
* [checkmeta.rb](https://github.com/WSU-CDSC/microservices/blob/master/Resources/checkmeta.md)

## Workflow Dependencies

Installation of dependencies can be completed with the following commands:
* `sudo apt install ruby-all-dev`
* `sudo apt install python`
* `sudo apt install python-pip`
* `sudo apt install mediainfo`
* `sudo apt install hashdeep`
* `sudo apt install exiftool`
* `sudo pip install b2`
* `sudo gem install mail`

Then the repository can be downloaded with the command:

`git clone https://github.com/WSU-CDSC/microservices`

The scripts rely on a central file containing methods etc, and will look for this script in their same directory, so make sure that the `wsu-functions.rb` file is always present along side of the scripts.

There is a conig file (`wsu-microservices.config`) that also must be present in the script directory. This file can be opened using a text editor, and is used to set options such as email reporting and logfile location.

## Workflow Steps and Scripts:

These are the scripts that are used to generate/maintain/validate metadata across WSU Libraries' (on site) Digital Storage. This metadata consists of sidecar files containing preservation, file integrity (fixity) and technical metadata. This metadata consists of a checksum/file manifest created by [Hashdeep](http://md5deep.sourceforge.net/start-hashdeep.html), an [ExifTool](https://www.sno.phy.queensu.ca/~phil/exiftool/) output in JSON, and a [MediaInfo](https://mediaarea.net/en/MediaInfo) output in JSON when A/V files are detected. Additionally, preservation actions such as metadata generation/verification and cloud migration are logged in a JSON file and mapped to [PREMIS vocabulary](http://id.loc.gov/vocabulary/preservation/eventType.html).

### Usage workflow:
* Generate Metadata for collections using `makemeta.rb`
* Upload collections to Backblaze B2 Storage using `uploadaip.rb`
* Perform ongoing monitoring of metadata via `checkmeta.rb`
* After any manual intervention necessitated by results of `checkmeta.rb` update metadata/modification time logs with `makemeta.rb` and (as necessary) resync to cloud with `uploadaip.rb`.

## Download Workflow

### Using Cyberduck
The [Cyberduck app](https://cyberduck.io/) provides a relatively easy and intuitive way to interface with collections stored in B2. To configure an installation of Cyberduck, please talk to Libraries Systems. Once Cyberduck is installed, you will be able to log in and view/download items stored in B2. Files and directories can be downloaded by clicking on the 'Action' tab and then selecting 'Download.' Downloading via this method will keep original file properties such as creation time.

__Note: ALL Packages downloaded for archival needs should have AIP Bag integrity validated. If files are downloaded separate from a bag, they should have their checksums generated and compared to the checksums housed in their bag.__

### Other Methods

#### Basic Access Needs
For basic access to files stored in B2, the web interface provides convenient browsing/download capabilities (the caveat being that the browser has limitations on folder download sizes). For most patron requests, simply navigating to the file(s) or AIP in the browser and downloading should be sufficient. If a large folder needs to be downloaded, files can be downloaded in smaller chunks, or the command line method discussed below can be used.

If a full AIP level package is downloaded, its integrity can be validated using one of the previously mentioned Bagit tools. If the Java CLI is used, the command is `bagit verifyvalid [INPUT BAG]` for a full checksum validation or `bagit checkpayloadoxum [INPUT BAG]` for a quick validation by payload size.

#### Archival Access Needs
When uploaded via `aip2b2.rb`, the b2 `sync` command is used which stores file metadata such as modification time is stored along side files. In the event of a download for Archival purposes (such as migration of data out of B2), it is important to use the reverse of this process to maintain this metadata. This can be done again using the `sync` command in reverse. It is suggested to do a 'dry run' download first to make sure you are using desired paths etc. An example command is:

`b2 sync --dryRun 'b2://BUCKET-NAME/PATH-TO-TARGET' '/home/myuser/Desktop/TEST'`. To execute the download simply remove the `--dryRun` flag.

__Note: ALL Packages downloaded for archival needs should have AIP fixity integrity validated__

More information about the `sync` command is available from Backblaze in [this how to article](https://help.backblaze.com/hc/en-us/articles/226937867-How-do-I-use-the-b2-sync-command-)

## B2 Information
__Pricing (As of writing):__
* Storage: $0.005 per GB per month
* Download: $0.01 per GB
* For downloads up to 3.5 TB, a physical drive can be used with Backblaze offering a service to refund cost of drive upon return.

__File Integrity:__ SHA-1 Checksums generated and verified on upload using `sync` command.

__Data Location:__ [Sacramento Area](https://help.backblaze.com/hc/en-us/articles/217667468-B2-Security-and-Redundancy).





