
# Cloud Storage Workflow for Archival Packages

# Contents
* [Overview](#overview)
* [Workflow Dependencies](#workflow-dependencies)
* [Workflow Steps](#workflow-steps)
  - [Generate AIP](#generate-aip)
  - [Upload AIP](#upload-aip)
* [Download Workflow](download-workflow)
* [Backblaze B2 Information](#b2-information)

## Overview:
The current workflow for migrating/storing digital materials into offsite cloud storage utilizes Ruby Scripts to prepare and upload data to the [Backblaze B2 Storage service](https://www.backblaze.com/b2/cloud-storage.html). As of writing, scripts have been tested in a Linux environment. Individual descriptions for the scripts can be found at the following links:

* [makeaip.rb](https://github.com/WSU-CDSC/microservices/blob/master/Resources/makeaip.md)
* [aip2b2.rb](https://github.com/WSU-CDSC/microservices/blob/master/Resources/aip2b2.md)

## Workflow Dependencies

The scripts used in the workflow control several tools that must be present/installed to function.
* [Ruby](https://www.ruby-lang.org/en/documentation/installation/): As the scripts are written in Ruby, the computer must have Ruby installed.
* [Bagit Java](https://github.com/WSU-CDSC/bagit-java): Currently the scripts use the Java command line tool, which in current form must be installed to path. Bagit Java has been forked to the CDSC Github account.
* [B2 Command-Line Tool](https://www.backblaze.com/b2/docs/quick_command_line.html): This is the tool released by Backblaze to faciltate interactions with their cloud service.

## Workflow Steps:

### Generate AIP
* Use `makeaip.rb` to copy and restructure target directories onto a staging drive.
  - Optionally use the `-a` flag to automatically separate file extensions deemed access files.
  - Optionally use the `-x` flag to __not__ create a 'bag' from transferred files. Use this when any manual processing will be done to the AIP prior to upload.
* Review log(s) to make sure there were no unexpected failures during AIP creation.
* If the `-x` flag was used, perform all manual processing and then finalize the AIP by structuring it as a bag. This can be done using one of the available tools such as [Bagger](https://github.com/LibraryOfCongress/bagger) or via the [Bagit Java tool](https://github.com/LibraryOfCongress/bagit-java). If using the java tool, the command is `bagit baginplace [TARGET]`

### Upload AIP
* Use the `aip2b2.rb` script to upload the AIP to Backblaze B2.
* Check logs/Backblaze interface to verify successful upload.
* Update 'Locations' document to reflect backup status of AIP to cloud and any drives.

## Download Workflow
For basic access to files stored in B2, the web interface provides convenient browsing/download capabilitites. For most patron requests, simply navigating to the file(s) or AIP in the browser and downloading should be sufficient. If a full AIP level package is downloaded, its integrity can be validated using one of the previously mentioned Bagit tools. If the Java CLI is used, the command is `bagit verifyvalid [INPUT BAG]` for a full checksum validation or `bagit checkpayloadoxum [INPUT BAG]` for a quick validation by payload size.

When uploaded via `aip2b2.rb`, the b2 `sync` command is used which stores file metadata such as modification time is stored along side files. In the event of a download 

## B2 Information





