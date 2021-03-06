# DISSCO-2.0.2
Computer music on HPC

DISSCO, a Digital Instrument for Sound Synthesis and Composition, offers a unified approach to music composition and sound synthesis, bringing both disciplines together in a seamless process. Presently, DISSCO consists of three modules: LASS, a Library for Additive Sound Synthesis; CMOD, a Composition Module; and LASSIE, a Graphic User Interface (GUI). A module for the production of visual events and a module for sonification experiments are under consideration for future development.

Although DISSCO can be used to generate music in any desired style, it exhibits a strong bias towards the use of controlled randomness and encourages the user to plan the composition ahead of time and in detail. DISSCO is a “black box”: once the data is fed in, the user does not intervene during the computations, and the output does not require post-processing. All three components (LASS, CMOD, and LASSIE) are written in C++; Xerces is used to read and interpret CMOD input files in XML format.
LASS

LASS (Library for Additive Sound Synthesis) can generate any number of sounds and, within each sound, any number of partials. LASS provides the user with complete control over the attributes of each partial. LASS is unique in the way it allows the user to specify the perceived loudness of a sound. Loudness is a nonlinear function of amplitude and frequency; to achieve an assigned perceived loudness, the amplitude of a sound is adjusted on the basis of the ISO equal-loudness curves and a number of critical bands. Unlike its predecessors DIASS_M4C and DISCO, LASS uses function evaluations instead of table look-ups and does not require a "score." LASS is therefore fundamentally different from a program of the MusicN type.

Three design goals have guided this project: expandability, ease of use, and efficiency. The architecture of LASS is modular; no doubt, new features will need to be added, and future developers must be able to easily expand the system. The library was designed to be user-friendly. The interfaces to classes were made as clear as possible and kept consistent across objects. Extensive use of references instead of pointers helps insure good memory management. Since sound synthesis is computationally intensive, LASS must also be efficient.

LASS is based on theoretical contributions by Hans Kaper, Senior Mathematician Emeritus at Argonne National Laboratory, and Sever Tipei, Professor of Music at the University of Illinois at Urbana-Champaign and Manager of the Computer Music Project of the UIUC Experimental Music Studios, and has benefited from their experience with two earlier additive synthesis systems, DIASS_M4C and DISCO. The general framework of the library and many of its features were written by Braden Kowitz. A number of students enrolled in the "Advanced Computer Music" seminar at UIUC have also contributed to the project.

In 2013, LASS is partly rewritten to fully utilize the power of modern multi-core personal computer. The future plan for LASS improvement include the ability of distributed computing and implementation of new modules.
CMOD

The central component of the composition module, CMOD, is the event class. An event can have children events that, in turn, can become parent events and have their own children, in an arrangement reminiscent of Russian dolls (matryoshkas). There is only one Top event, but there can be any number of High, Medium, Low, and Bottom events at the corresponding structural levels: the entire piece; sections, themes, chords or any other subdivisions of the piece; and individual sounds or notes generated by the Bottom level. Not all types of events need to be present, and the user can create new categories. This structure reflects the realization that similar tools are used at different time scales.

All events have a start time, type, and duration. (Other parameters may be added in the future.) However, the Top event and the Bottom events differ from the other events – the Top event is unique, while the Bottom event creates synthesized sounds, notes in a score, or both, and assigns to them various attributes such as vibrato, tremolo, glissando, location in space, and reverberation.

An initial version of the composition module was written by Sever Tipei, modified by students of the “Advanced Computer Music” seminar, and greatly improved by Ryan Cavis, Andrew Burnson, and Ming-ching Chiu.

In 2012-2013, CMOD underwent intensive refactoring and improving. The newest version is launched in May 2013. The improvements include:

    Integrating LASS in a tighter manner.
    Adopting XML as its input format.
    Adopting muparser as its math parser.

LASSIE

LASSIE, a graphic user interface, provides easy access to DISSCO on Linux machines. Without changing the format of the original text-based CMOD input files, LASSIE offers the user an alternative way of managing and editing the files in an integrated graphic environment. LASSIE is implemented using gtkmm, the official C++ interface for the popular GUI library GTK+.

The main window of LASSIE contains a drop-down menu and the tool bar at the top of the window, the Object List in the left half of the main window, and the attributes of the object selected in the Objects List in the right half of the main window. The Object List groups the objects (events, spectrums, notes, envelopes, etc.) in separate folders. The attributes of any object can be inspected and edited by double clicking the object in the Objects List.

An Envelope Library window is part of LASSIE and is opened by clicking the “Envelope Library” button at the bottom of the Objects List. The Envelope Library window provides the visualized representation of the original text-based envelope specification. Envelopes can be modified directly in this window.

LASSIE provides some instructions in real time as the attributes of objects are edited. It also checks the syntax of the information input and shows warnings if the input files contain illegal syntax.

LASSIE was written by Ming-ching Chiu.



DISSCO is free software; it may be redistributed it and/or modified under the terms of the GNU General Public License as published by the Free Software Foundation. See:
http://www.gnu.org/licenses/gpl.txt 
