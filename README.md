# Automated Music Track Generator

**Author:** Taka Khoo  
**Version:** 1.0  
**Date:** 2025-03-25

---

## Overview

The **Automated Music Track Generator** is a cutting-edge project that combines algorithmic composition with real-time sound synthesis. Written entirely in C, this tool dynamically generates musical scores and synthesizes them using [Csound](https://csound.com). By merging controlled randomness with user-defined parameters, the generator produces unique musical compositions that adapt to your specified tempo, scale, and section duration.

This project was developed as an experimental platform to explore the intersection of algorithmic art and digital sound synthesis. My long-term vision is to extend this work with deep learning techniques for creating adaptive, high-quality music.

---

## Mathematical Foundations

The rhythmic timing of the generated music is based on the following formulas. For instance, a quarter note is defined as:

$$
\text{Duration}_{\text{quarter}} = \frac{60}{\text{BPM}}
$$

An eighth note is then:

$$
\text{Duration}_{\text{eighth}} = \frac{60}{2 \times \text{BPM}}
$$

More generally, for a note with a division factor \( D \):

$$
\text{Duration}_{\text{note}} = \frac{60}{\text{BPM} \times D}
$$

These equations ensure that as the tempo (BPM) changes, the note durations scale proportionally, maintaining musical integrity.

---

## Features

- **Dynamic Score Generation:**  
  Automatically writes a Csound score file (`.csd`) containing instrument definitions for melody, hi-hat, bass drum, and reverb.
  
- **User-Defined Parameters:**  
  Customize musical mode (scale), BPM, section duration, number of sections, and loop count per section.
  
- **Time-Stretching Option:**  
  Generate a time-stretched version of the composition using Csound’s `sndwarp` opcode.
  
- **Modular and Extensible:**  
  Designed for future enhancements, including integration with deep learning models for improved music generation.

---

## Environment Setup

### Prerequisites

- **MinGW/MSYS2 with GCC:**  
  Verify installation by running:
  ```bash
  gcc --version

Csound:

Download and install Csound from csound.com/download.html.

Add the Csound binary directory (e.g., C:\Program Files\Csound6_x64\bin) to your PATH.
For MSYS2, add this line to your ~/.bashrc:

bash
Copy
export PATH="$PATH:/c/Program\ Files/Csound6_x64/bin"
Reload with:

bash
Copy
source ~/.bashrc
Test with:

bash
Copy
csound --version
VSCode:
Use VSCode for code editing and debugging. Configure the C/C++ extension with your include paths by editing .vscode/c_cpp_properties.json:

json
Copy
{
    "configurations": [
        {
            "name": "MinGW",
            "includePath": [
                "${workspaceFolder}/**",
                "C:/msys64/mingw64/include",
                "C:/msys64/mingw64/x86_64-w64-mingw32/include"
            ],
            "compilerPath": "C:/msys64/mingw64/bin/gcc.exe",
            "cStandard": "c11",
            "cppStandard": "c++17",
            "intelliSenseMode": "gcc-x64"
        }
    ],
    "version": 4
}
Git:
Install Git using MSYS2:

bash
Copy
pacman -S git
or via Git for Windows.

Building and Running the Code
Compilation
You can compile the code using either manual commands or a Makefile.

Manual Compilation:
Open your terminal in the project directory.

Run:

bash
Copy
gcc -o exe algo_comp_v3.c
Using a Makefile (Optional):
Create a file named Makefile with:

makefile
Copy
exe: algo_comp_v3.c
	gcc -o exe algo_comp_v3.c

clean:
	rm -f exe
Then compile with:

bash
Copy
mingw32-make
Execution
After compiling, run the executable:

bash
Copy
./exe
You will be prompted for:

Musical Mode: Choose a scale (1 for Ionian, 2 for Dorian, …, 7 for Locrian).

BPM (Tempo): Enter a value (20–200, recommended 30–100 BPM).

Section Duration: Duration in seconds for each section.

Number of Sections: Total sections in your composition (note: hi-hat and kick drum begin in later sections).

Loops per Section: How many times each section should repeat.

Render Option: Enter 0 for direct playback or 1 to render the composition to an AIFF file.

After your inputs, the program generates a Csound score file (e.g., algo_comp_v3.csd), and Csound synthesizes and plays the track. You can also opt to create a time-stretched version of the track.

Troubleshooting
Csound Not Found:
If you encounter "csound is not recognized", ensure the Csound bin directory is correctly added to your PATH and that you reloaded your shell.

Missing Include Files:
Errors such as "cannot open source file stdio.h" are usually fixed by correctly configuring include paths in c_cpp_properties.json.

Infinite Looping:
In earlier versions, the hi-hat generation loop might run indefinitely. This version includes proper termination conditions; however, if you encounter issues, verify your BPM and section duration inputs.

Git History:
If the original author still appears in commit history, remove the .git folder and reinitialize the repository to start with a clean history.

Future Enhancements
Expanded Instrumentation:
Introduce additional instruments and synthesis techniques to create more diverse soundscapes.

Deep Learning Integration:
Incorporate neural network models to analyze musical patterns and generate refined compositions.

Graphical User Interface:
Develop a GUI for real-time control over musical parameters.

Live Interaction:
Enable live performance features with dynamic parameter adjustments during playback.

