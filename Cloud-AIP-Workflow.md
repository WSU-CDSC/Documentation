
# Cloud Storage Workflow for Archival Packages

# Contents
* [Overview](#overview)
* [Workflow Dependencies](#workflow-dependencies)

## Overview:
The current workflow for migrating/storing digital materials into offsite cloud storage utilizes Ruby Scripts to prepare and upload data to the [Backblaze B2 Storage service](https://www.backblaze.com/b2/cloud-storage.html).

* [makeaip.rb](https://github.com/WSU-CDSC/microservices/blob/master/Resources/makeaip.md)
* [aip2b2.rb](https://github.com/WSU-CDSC/microservices/blob/master/Resources/aip2b2.md)

## Workflow Dependencies
* [Ruby](https://www.ruby-lang.org/en/documentation/installation/)
* [Bagit Java](https://github.com/LibraryOfCongress/bagit-java)
* [B2 Command-Line Tool](https://www.backblaze.com/b2/docs/quick_command_line.html)



## Steps:
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





