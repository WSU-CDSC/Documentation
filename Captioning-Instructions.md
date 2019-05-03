# Captioning Workflow Instructions

### Introduction

These instructions are for the caption creation process for the SHN Vimeo collection. In order to generate subtitles, each video will be initially processed with speech to text software. This output will then be assembled into `.vtt` subtitle files with all content divided into four second segments. While this software does a good job of creating a rough transcript,it is far from perfect, and all `.vtt` files must be proofread and corrected for accuracy. The following are the instructions for this proofreading process.

__Note__: Scripts and documentation for initial `.vtt` generation can be found in the WSU [microservices repository](https://github.com/WSU-CDSC/microservices/blob/master/Resources/transcription-scripts.md).

### Workflow

#### Step 1: Open spreadsheet

The SHN Transcription Spreadsheet is color coded to the represent status of each video regarding transcripts. Pick one of the files that is marked as `Transcript Generated` (Yellow) and find this file in the `Unedited Transcripts` folder.

![Spreadsheet example](/Resources/transcript1.png)

#### Step 2: Find and open file in [SHN Vimeo](https://vimeo.com/sustainableheritage)

The file name of the `.vtt` transcript file will contain the title for the corresponding video in the [SHN Vimeo page](https://vimeo.com/sustainableheritage). It will be necessary to have this video open in your browser in order to compare the computer generated transcription against the original audio while you edit the computer generated transcript.

#### Step 3: Open file in text editor

Since the `.vtt` files are just text documents, you can edit them in a standard text editor. Open the transcript in an editor and look at it for any obvious mistakes. As necessary, compare the transcription against the actual video file in Vimeo. Use the timestamps in the transcript to find the relative segments of speech in the video. The goal is to correct mistakes made by the transcription software so that the transcription as closely resembles the actual audio as possible.

#### Step 4: Save file and move to 'Edited Transcripts' folder

Once you are finished editing the transcript, save it as you would a normal text file.  Make sure that your editor is using UTF-8 character encoding to save the file! Then move it into the `Edited Transcripts` folder.
#### Step 5: Update spreadsheet

In the SHN Transcription Spreadsheet, change the fill color for the transcript you completed to blue to signify that the transcript has been edited and is ready for upload to Vimeo.

### Considerations/Things to watch out for

* Many of the SHN Videos contain elements of people speaking in languages besides English. The auto-transcription software will attempt to create an English transcript based off of these sounds, resulting in nonsensical portions of text. If you see any portions of a transcript that make no sense in context, it is very possible that the speaker is using a non-English language. Using parenthesis, replace the text with a note to that effect, and when possible attempt to identify and include what language the is being spoken. An example would be `(Speaker talking in Japanese)`.

* The auto-transcription software will often confuse homophones (words with the same pronunciation but different spellings/meanings) such as `our` and `are`. When reading the transcript, pay particular attention to context to catch these mistakes.

* Often you can use context to correct mistakes without needing to verify against the original audio. An example is the following where the word `war` is a mistake for the word `work`:

> 00:00:35.13 --> 00:00:39.27

> not my work but the collective war of
>
> 00:00:39.27 --> 00:00:42.15

> librarians in the state of New Mexico

* If a sentence or line would be made more clear by adding punctuation (such as a comma) feel free to add punctuation.
