<p align="center"><strong>NDSA Levels of Digital Preservation Survey of WSU Libraries</strong></p>
<p align="center">January, 2018</p>
<p align="center">Prepared by Andrew Weaver</p>

# Introduction and Background

The National Digital Stewardship Alliance (NDSA) Levels of Digital Preservation consist of a matrix of criteria for digital preservation organized in five categories: Storage and Geographic Location, File Fixity and Data Integrity, Information Security, Metadata, and File Formats. The NDSA Levels differ from other more comprehensive standards, such as those codified in [ISO 16363](https://www.crl.edu/archiving-preservation/digital-archives/metrics-assessing-and-certifying/iso16363) , in that they are intended to provide institutions with an immediately accessible tool for evaluating current conformance with Digital Preservation best practices (Phillips et al., 2013).  As such, they are particularly useful to quickly establish concrete steps for improvement.


In 2017 an Orbis Cascade Alliance-wide NDSA assessment was conducted by providing institutions a questionnaire with questions corresponding to NDSA criteria. Members of the Alliance Digital Preservation Working Group then evaluated those responses and assigned institutions point scores across the five NDSA categories. Their findings for the WSU Libraries were as follows (courtesy of the Orbis Cascade Alliance Digital Preservation Working Group).

| NDSA Category    | Storage/Geographic Location | File Fixity/Data Integrity | Information Security | Metadata | File Formats | Average |
|------------------|-----------------------------|----------------------------|----------------------|----------|--------------|---------|
| WSU              | 2                           | 2                          | 2                    | 4        | 3            | 2.6     |
| Alliance Average | 1.167                       | 0.542                      | 1.292                | 1.792    | 2.042        | 1.37    |
| Alliance Median  | 1                           | 0                          | 1                    | 2        | 2            | 1.2     |

The Alliance’s scores place the University Libraries in the mid-range of the NDSA levels, indicating that we are currently doing an above average job of adhering to Digital Preservation standards compared with other Alliance institutions. This positions us well as having a solid baseline that can be refined towards more maximal compliance.

While participating in the Alliance survey provided us with a good overarching metric of our progress, I have been undertaking a follow up NDSA levels survey in order to provide a more granular analysis of individual workflows. Due to the diversity of preserved digital materials in the Library, both in terms of source and storage, this more specific approach is necessary to create more actionable recommendations tailored to context.

The Alliance Digital Preservation Working Group has created a web resource built around providing interpretations of the documentation surrounding the NDSA levels as well as concrete steps to increase compliance . In the interest of supporting standardization of efforts across our local community, I have made use of these specific interpretations in creating this report. (Cross links have also been provided). I also have taken a more holistic approach in analyzing our compliance with NDSA recommendations rather than focusing purely on a points based progression of levels.

# Storage and Geographic Location

|[Level 1](https://orbiscascadeccd.github.io/digprezsteps/storage.html#step1)|[Level 2](https://orbiscascadeccd.github.io/digprezsteps/storage.html#step2)|[Level 3](https://orbiscascadeccd.github.io/digprezsteps/storage.html#step3)|[Level 4](https://orbiscascadeccd.github.io/digprezsteps/storage.html#step4)|
|---|---|---|---|
|Two complete copies that are not collocated|At least three complete copies - At least one copy in a different geographic location|At least one copy in a geographic location with a different disaster threat|At least three copies in geographic locations with different disaster threats|
|For data on heterogeneous media (optical discs, hard drives, etc.) get the content off the medium and into your storage system|Document your storage system(s) and storage media and what you need to use them|Obsolescence monitoring process for your storage system(s) and media|Have a comprehensive plan in place that will keep files and metadata on currently accessible media or systems|
|__Analysis__|---|---|---|
|We are definitely compliant with this. All data that is stored in archival storage is also backed up on a separate drive in Systems|For data stored in the Repository, we maintain master copies, locally backed up copies and copies on LTO tape that are stored off site|We do not have a backup of archival materials located in a region with a different disaster threat. We are engaged in ongoing monitoring of our storage systems and are capable of making upgrades/repairs as needed.|We do not have backups in three separate regions with different disaster threats.|

 __Recommendations__: In order to become more compliant in this area it is recommended to introduce more geographic separation into our backup process. Since we have a tape based backup system in place, this could take the form of sending tape copies to other WSU campuses (this is already being investigated). Depending on interpretations of disaster threats, sending tapes to both Vancouver and Spokane could potentially count as maximum compliance. If this system of LTO tapes is to be our long term solution for geographical separation, it is essential that we develop plans and documentation for migration/obsolescence monitoring of our LTO systems. An additional option for compliance (and for enhanced storage capacity in general) could be a cloud based service.

---

 # File Fixity and Data Integrity
 
 |[Level 1](https://orbiscascadeccd.github.io/digprezsteps/fixity-deep.html#step1)|[Level 2](https://orbiscascadeccd.github.io/digprezsteps/fixity-deep.html#step2)|[Level 3](https://orbiscascadeccd.github.io/digprezsteps/fixity-deep.html#step3)|[Level 4](https://orbiscascadeccd.github.io/digprezsteps/fixity-deep.html#step4)|
|---|---|---|---|
|Check file fixity on ingest if it has been provided with the content|Check fixity on all ingests|Check fixity of content at fixed intervals|Check fixity of all content in response to specific events or activities|
|Create fixity info if it wasn’t provided with the content|Use write-blockers when working with original media|Maintain logs of fixity info; supply audit on demand|Ability to replace/repair corrupted data|
||Virus-check high risk content|Ability to detect corrupt data - Virus-check all content|Ensure no one person has write access to all copies|
|__Analysis__|---|---|---|
|Currently file fixity data in the form of sidecar files or embedded metadata is not being created. When files are added into archival storage, fixity metadata is not immediately created, but rather is created through the process of ongoing scheduled monitoring. Newly added files will have their checksums generated and stored at the time the next fixity process is run.|We currently do not process an extensive amount of born digital content. The holdings that we do have have been accessed through a data accessioner.|We engage in ongoing scheduled fixity tests of archived content. These logs are stored in a dedicated location as well as emailed to systems staff.|In current digitization workflows there are several points where files are copied or transferred. Currently we do not generate or verify fixity information during these events. Current system of ongoing fixity checks of archival storage would enable detection of corrupted files. These files could then be repaired or restored from backups.|

__Recommendations:__

Just as a matter of security, it is recommended that any drives we receive from external sources (such as oral history producers or vendors) be scanned for viruses when they are connected to University computers for the first time.

It is recommended that both the amount of fixity information generated and the timing of fixity metadata generation be increased for all files that will be stored in the repository.

Since it is impossible to establish with certainty the provenance of a digital file without having a baseline to compare it to, ideally at least an initial form of fixity metadata would be generated early on in the creation of any new digital content. This could take several forms, and for some stages of workflows could be as simple as transferring files using tools known to generate and compare fixity (such as rsync), however at the point of ingest into the repository it is recommended that all files already be associated with 'sidecar' metadata files containing fixity information.

It is recommended that some form of structure built around the concept of SIPs and AIPs (Submission Information Packages and Archival Information Packages) be implemented that would enable the tracking and comparison of fixity information both on ingest and during following events (such as access). Options include the [BagIt](https://en.wikipedia.org/wiki/BagIt) standard, DSpace's [Simple Archive Format](https://wiki.duraspace.org/display/DSDOC5x/Importing+and+Exporting+Items+via+Simple+Archive+Format#ImportingandExportingItemsviaSimpleArchiveFormat-DSpaceSimpleArchiveFormat), a homegrown approach, etc. Combinations of these formats could also be used for different stages of the creation -> ingest -> archive -> access process. Additionally, moving to an AIP based archival workflow could simplify the process of an ultimate move towards a full digital asset management system.

---

# Information Security

|[Level 1](https://orbiscascadeccd.github.io/digprezsteps/security.html#step1)|[Level 2](https://orbiscascadeccd.github.io/digprezsteps/security.html#step2)|[Level 3](https://orbiscascadeccd.github.io/digprezsteps/security.html#step3)|[Level 4](https://orbiscascadeccd.github.io/digprezsteps/security.html#step4)|
|---|---|---|---|
|Identify who has read, write, move and delete authorization to individual files|Document access restrictions for content |Maintain logs of who performed what actions on files, including deletions and preservation actions|Perform audit of logs|
|Restrict who has those authorizations to individual files||||
|__Analysis__|---|---|---|
|We are clearly compliant with this. We have a system of permissions in place restricting file write access to archival materials.|We do not have a centrally maintained document listing users/access levels to the repository. Additionally, Due to the nature of some of our content, we have the need to document access restrictions related to ethical issues.|As our repository is currently a Windows based server, we log events to the extent that Windows inherently supports. If a file is deleted we can see which user performed the action. We are not logging any actions beyond those logged by the Windows system.|We do not currently have any active monitoring of action logs.|

__Recommendations:__ In order to conform with NDSA recommendations we should establish some centralized documentation about access levels to digital repositories. For any files stored in the repository for which there are any cultural or ethical access restrictions it is recommended that metadata documenting this be stored in a manner that is clearly associated with those files. We currently are able to log actions at least on the level of file deletion. It is recommended that we investigate a way to parse and store actions into a more centralized log/report and establish guidelines for monitoring, however, this would likely necessitate the implementation of a DAM.

---

# Metadata

|[Level 1](https://orbiscascadeccd.github.io/digprezsteps/metadata.html#step1)|[Level 2](https://orbiscascadeccd.github.io/digprezsteps/metadata.html#step2)|[Level 3](https://orbiscascadeccd.github.io/digprezsteps/metadata.html#step3)|[Level 4](https://orbiscascadeccd.github.io/digprezsteps/metadata.html#step4)|
|---|---|---|---|
|Inventory of content and its storage location|Store administrative metadata|Store standard technical and descriptive metadata|Store standard preservation metadata|
|Ensure backup and non-collocation of inventory|Store transformative metadata and log events|||
|__Analysis__|---|---|---|
|Full inventory?|A variety of administrative and some transformative metadata is being captured, however it is (for the most part) not being stored within the repository alongside associated data, but rather within access points.|Similar to level 2, descriptive and technical metadata is created at various stages but is not stored within the repository.|We currently are not collecting standardized preservation metadata (i.e. PREMIS)|

__Recommendations:__ In order to ensure that important metadata for digital archival materials are not only stored in access focused systems, it is recommended that clear associations for all metadata categories be maintained for all materials in digital repositories. This could include starting to preserve some of this metadata in sidecar files within the repository (such as in README files as recommended by the Alliance), recording digital file locations along with respective metadata within physical archives management systems (e.g. ArchivesSpace) or storing this information in any future Digital Asset Management system. In terms of a worklow, this would probably mean keeping spreadsheets generated during digitization associated with files to facilitate further digital processing. If Level 4 compliance is desired (creation of PREMIS metadata) almost any kind of practical plan would involve the use of a Digital Asset Management system.

# Formats

|[Level 1](https://orbiscascadeccd.github.io/digprezsteps/formats.html#step1)|[Level 2](https://orbiscascadeccd.github.io/digprezsteps/formats.html#step2)|[Level 3](https://orbiscascadeccd.github.io/digprezsteps/formats.html#step3)|[Level 4](https://orbiscascadeccd.github.io/digprezsteps/formats.html#step4)|
|---|---|---|---|
|When you can give input into the creation of digital files encourage use of a limited set of known open formats and codecs|Inventory of file formats in use|Monitor file format obsolescence issues|Perform format migrations, emulation and similar activities as needed|
|__Analysis__|---|---|---|
|We currently have a certain amount of documentation in this respect, and are producing educational content via the Sustainable Heritage Network.|We have reports for all file formats (by extension) of files contained in the repository.|Monitoring of file issues has been and continues to be active.|As we currently do not have vast amounts of born digital data, emulation has not yet been an issue for us. Currently legacy data is being investigated for any migration needs.|

__Recommendations:__
We could benefit from having public facing documentation about preferred sustainable formats for digital archiving, both for our outreach efforts and as a means of controlling what makes its way into the digital repositories. Adding a 'Digital Preservation' section to the Libraries' website that laid out preferred file formats, commitment levels for long term access to digital formats and basic tenets of Digital Preservation could help as a significant tool with outreach in the University community. Additionally, in order to foster trust within potential users, it is crucial to clearly enumerate and explain the Libraries' commitments to maintaining specific formats.

Within the Research Exchange Institutional Repository there is a list of levels of support by MIME type available at [https://research.libraries.wsu.edu/xmlui/admin/format-registry](https://research.libraries.wsu.edu/xmlui/admin/format-registry), but this is more of an internal document, is not easy for non-specialists to interpret and is limited in scope to the IR. I suggest that we review our preservation commitments and establish a more comprehensive and less technical document. Some examples of documentation at other institutions are included below. These are not all necessarily intended as guides, but rather as examples of decisions made by other institutions.

* UM Deep Blue Repository documentation [documentation](https://deepblue.lib.umich.edu/static/about/deepbluepreservation.html)

* UW's preferred format [matrix](http://www.lib.washington.edu/preservation/preservation_services/preferred-file-formats)

* UI's format [page](https://www.lib.uidaho.edu/services/data/data-management/#formats)

* U Oregon's best practices [page](https://library.uoregon.edu/research-data-management/best-practices)

# Sources
Phillips, M., Bailey, J., Goethals, A., & Owens, T. (2013, January). The NDSA levels of digital preservation: 	Explanation and uses. Retrieved from 	http://www.digitalpreservation.gov/documents/NDSA_Levels_Archiving_2013.pdf
