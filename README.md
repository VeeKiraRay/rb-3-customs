# rb-3-customs
Documentation on how to use RB3 custom tools and what songs to try and make

# Contents
 - [Error and how to fix](#error-and-how-to-fix) 
   - [Error 1 missing vocal note and invisible lyric](##error-1-missing-vocal-note-and-invisible-lyric)
   - [Error 2 no vocal phrases found](##error-2-no-vocal-phrases-found)
   - [Error 2.1 extends beyond phrase](##error-2.1-extends-beyond-phrase)
   - [Error 2.2 outside any phrases](##error-2.2-outside-any-phrases)
   - [Error 3 event after the end event](##error-3-event-after-the-end-event)
   - [Error 4 Missing lyrics at](##error-4-Missing-lyrics-at)
   - [Error 5 Cannot parse event](##error-5-Cannot-parse-event) 

## Error and how to fix

### Error 1 missing vocal note and invisible lyric
ERROR: MIDI Compiler: (PART VOCALS): Missing vocal note at [18:2:358] for lyric 'n'

#### Reason
Splitting, moving and gluing track while there are notes and lyrics might cause invisible duplicates. The invisible lyrics do not show up on the Reaper editor.

#### Prevent
Do not split and glue tracks. Instead zoom out and select notes with right mouse button hold if you need to move a big chunk of notes

#### Fix
Export the broken track as midi. Then use "Insert" -> "Media file" to add it to the project. This newly added copy will show the previously invisible lyrics and you can remove them. Clear out the original track by deleting the whole note highway, then copy the note highway from empty template project in its place and finally select all the notes from the re-imported mid file and paste them to the clean note highway. Finally re-add the lyrics with "Shift + L". Remember to clean the inserted media file so it doesn't bloat the project.



### Error 2 no vocal phrases found
ERROR: MIDI Compiler: (PART VOCALS): Vocal notes exist, but no vocal phrases found

#### Reason
The vocal portions need be split into sections / phrases

#### Fix
At the top of the vocal highway is phrase notes. Create long phrase notes that capsulate portions of the singing. All sung vocal notes must be inside these long phrases. The easiest grouping is to have the long notes expand and cut in every pause of the song but this can be done in shorter interval as well as long as the no sung notes goes over the phrase marker.



### Error 2.2 extends beyond phrase
ERROR: MIDI Compiler: (PART VOCALS): Vocal note at [26:4:312] extends beyond phrase

#### Reason
The sung note goes over the phrase marker

#### Fix
Extend the phrase not a little further to catch the sung note



### Error 2.2 outside any phrases
ERROR: MIDI Compiler: (PART VOCALS): Vocal note at [43:2:237] is outside any phrases

#### Reason
The sung note is not inside any of the phrase makers

#### Fix
Extend the nearest phrase marker to catch the sung note or create a new phrase marker.



### Error 3 event after the end event

#### Reason
There is an "EVENTS" highway at the bottom of the template that has markers for the song. There are some premade "Text Events" for when the song starts, when it ends where the chorus begins etc. Most of these can be omited unless your want to help the practice mode in game to piece the song in to easy to use chunks. Might also affect some default animation / camera work.
The "[music_start]", "[music_end]" are important to mark when band starts and stops playing and "[end]" needs to be in a time stamp that is after every played or sung note since that is when the game finishes the song.

### Fix
Extend or shrink the "EVENTS" highway to match the song length and move the "[music_end]" and "[end]" to at end of the song



### Error 4 Missing lyrics at
(PART VOCALS): Missing lyric at [98:3:363]

#### Reason
Either there aren't enough words / syllables in the lyrics for every note or somehow the note has moved without lyric and need to be re-aligned.

#### Fix
Adding more syllables / words to the lyrics and / or re-importing the lyrics with "shift + L" shoudld fix this issue



### Error 5 Cannot parse event
(PART VOCALS): Cannot parse event 0xc0 at [1:3:118]

#### Reason
There is an event marker on the track that the game doesn't know how to interpret. This can come when copy pasting existing tab notes on to the highway.

#### Fix
Check the marked timestamp. If there isn't anything weird on "Text Events" try and change to other types. For example "Program" event might be the culprit.
