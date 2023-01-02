# MIT - Midi Instrument Training plugin for MuseScore

At the origine this programme was created by  
///////////////////////////////////////////// 
//  Midi Instrument Training plugin for MuseScore  
//  Copyright (C) 2014 Jean-Baptiste Delisle  
//  Based on seqdemo.c by Matthias Nagorni  
//  
//  This program is free software; you can redistribute it and/or modify  
//  it under the terms of the GNU General Public License version 2  
//  as published by the Free Software Foundation and appearing in  
//  the file LICENCE.GPL  
*******************************************************************************
The original program was a plugin for musescore 2.0

I modified files to improve program and to be compatible with musescore 3.6


This (probably linux-only) plugin (for MuseScore 2.0) takes input from a MIDI instrument and colors notes while you play from blue (note and rhythm are perfect) to red (bad note or bad rhythm).
The score must have been exported in MIDI format before.
The plugin needs aplaymidi and aconnect (alsa-utils package in ubuntu), as well as qsynth (fluid synth) in order to ear the instrument.
The plugin compares the output of aplaymidi (which reads the midi file) with the output of the instrument. For each note, it computes the delay between the beginning of the note in the midi file and the beginning of the note you played, and the same for the end of the note. Then it colors the note depending on these delays.

You must edit the "MidiInstrumentTraining.qml" file to set the default settings, especially the folder in which the plugin is installed (pluginsPath) and the folder in which midi files are stored (midiPath).

Some settings can be changed in the plugin interface (you can also permanently change the default values in the MidiInstrumentTraining.qml file):
- Score channel : if the current score as multiple parts, you can select the one you want to play (0 is the first part, 1 is the second, ...)
- Midi Instrument name: The name of the midi instrument in order to be able to connect its output to the plugin and to qsynth. You can use "aconnect -i" (with and without connecting the instrument) to find its name. If you change the name, you should click on "restart synth" to be able to ear the instrument.
- Midi Instrument channel: It's probably always 0...
- WEIGHT START: This corresponds to the weight attributed to the delay between the score and the instrument at the beginning of the note in the computation of the color.
- WEIGHT END (+): This corresponds to the weight attributed to the delay between the score and the instrument at the end of the note if the instrument is late.
- WEIGHT END (-): This corresponds to the weight attributed to the delay between the score and the instrument at the end of the note if the instrument ends in advance. For wind instruments, the player sometimes needs to breath between two notes, so there should be more tolerance for a negative delay than a positive one... For other instruments, "WEIGHT END (-)" should probably be equal to "WEIGHT END (+)".
- MAX BADNESS: This correspond to the maximum weighted delay considered for the coloration (red note). You should increase it if it is too difficult to obtain blue notes and decrease it if it is too easy...


I extended it to support MuseScore 3.6.2
Musescore 3.6.2 use  QT release 5.9.9

On github I posted a message :  
https://github.com/musescore/MuseScore/discussions/15104  
      "
      Hi everyone.
      
      ththt
      hhftghf
      I'm learning piano at this moment. I'm also a programmer and engineer.
      
      To learn piano, a tutor mode could be very fun and useful on musescore !
      I saw a repository running musescore 3.0.0 with a fork who exhibit a tutor panel : Musescoretutorpanel developped by tommaso Cucinotta.
      Watch these links :  
      https://www.linkedin.com/pulse/musescorearduinoleds-tutorial-tommaso-cucinotta  
      https://www.linkedin.com/pulse/pianotutor-news-smart-score-here-tommaso-cucinotta  

      The functions which can be developped are :

      1. a waiting mode : partition waiting midi command to go to next note (waiting for you to press each keys'piano, before moving to the next one, during playback)
      2. a mode with a synchronized playing on musescore and piano and musescore marking mistakes in red for example (simpler to develop)
      3. All features with electronic parts (arduino or other) are not needed
      4. have these features on windows/linux and android (to use on tablets)
      5. have these features running with midi usb and bluetooth (on tablets) but it's not needed because we can use usb OTG on android.

      So we can have the same features as Synthesia or Piano Master

      It's very usefull

      I understand It was on musescore 3.0.0. Why did you cancel this mode ? I think all is already developped.
      A lot of people use a teacher on learning phase. But an "electronic/informatic" tutor is so usefull. It's also very usefull when practicing piano to learn a music sheet. I think, it can also be extended to other instruments.
      To communicate you can also explain musescore do the same things as synthesia... and better as synthesia...

      I can explain with more details how it have to run. I can also be a beta tester.

      Best regards.
      "


# Reference links :
https://musescore.org/fr/handbook/developers-handbook/compilation/compile-instructions-windows-visual-studio/compile-1  
https://musescore.org/fr/handbook/developers-handbook/compilation/compile-instructions-windows-visual-studio  
https://musescore.org/en/node/269612  
https://musescore.github.io/MuseScore_PluginAPI_Docs/plugins/html/index.html  


# Building MuseScore in Qt to develop a plugin :
Download MuseScore and extract in a directory (called after root).
Download dependencies.zip and extract it at root : to obtain lame (Mp3).
