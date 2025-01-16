# LaTeX Setup and CV Creation Guide

## 📌 Introduction
This guide will help you:
- Set up LaTeX in VS Code
- Fix common errors (like latexmk not found, Docker issues, etc.)
- Create a professional CV using LaTeX

This guide walks you through the process of setting up **LaTeX** in **Visual Studio Code (VS Code)**, fixing common errors, and creating a **CV** using LaTeX.

---

## 🚀 Prerequisites

Before starting, ensure you have the following installed:

1. **MiKTeX**: LaTeX distribution for Windows.
2. **Strawberry Perl**: A Perl distribution required for some LaTeX commands.
3. **Visual Studio Code (VS Code)**: Code editor.
4. **LaTeX Workshop Extension**: VS Code extension for LaTeX editing.

## 🔧 Installation Steps

### 1. Install MiKTeX
- Download and install **[MiKTeX](https://miktex.org/download)**.
- After installation, make sure `latexmk` is in your system PATH.

### 2. Install Strawberry Perl
- Download and install **[Strawberry Perl](https://strawberryperl.com/)**.
- This is required for some LaTeX tools to function correctly.

### 3. Install Visual Studio Code
- Download **[VS Code](https://code.visualstudio.com/)** and install it.

### 4. Install LaTeX Workshop Extension for VS Code
- Open **VS Code** and go to the Extensions tab (left sidebar).
- Search for **LaTeX Workshop** and click **Install**.

### 5. Uodate Miktek or it will give errors
- Open **MiKTeX Console on Windows** → Go to **Updates** → Install all updates.
- Next, Open **Command Prompt (cmd)** and verify installation:
   ```sh
   where latexmk
   ```
   It should return a path like:
   
   C:\Users\YourName\AppData\Local\Programs\MiKTeX\miktex\bin\x64\latexmk.exe

---
## 🔧 Setting Up VS Code

### Configure `latexmk` in VS Code
1. Open VS Code **Settings** (`Ctrl + ,`)
2. Search for `latex-workshop.latex.tools`
3. Click **Edit in settings.json** and add:
   ```json
   "latex-workshop.latex.tools": [
      {
         "name": "latexmk",
         "command": "C:/Users/YourName/AppData/Local/Programs/MiKTeX/miktex/bin/x64/latexmk.exe",
         "args": [
            "-synctex=1",
            "-interaction=nonstopmode",
            "-file-line-error",
            "-pdf",
            "%DOC%"
         ]
      }
   ]
   ```
   Here replace path with your own path from when you run "where latexmk" command

## ⚙️ Fixing LaTeX Workshop Errors

### **Error: "spawn latexmk ENOENT"**
If this error occurs when you r\run your .tex file, it means LaTeX Workshop can't find `latexmk`. Follow these steps to resolve:

1. **Verify `latexmk` Installation**:
   - Open Command Prompt and run:
     ```bash
     latexmk --version
     ```
   - If it's not found, reinstall MiKTeX and ensure `latexmk` is added to your system PATH.

2. **Add MiKTeX Path to System PATH**:
   - Go to **Control Panel > System and Security > System > Advanced System Settings > Environment Variables**.
   - Under **System Variables**, edit the `Path` variable and add:
     ```
     C:\Users\Wits-user\AppData\Local\Programs\MiKTeX\miktex\bin\x64\
     ```

3. **Restart Your Computer** after making changes.


### **Error: "docker' is not recognized as an internal or external command"**
If the this error occurs, you need to Disable Docker in LaTeX Workshop:

1. Go to **VS Code Settings** (`Ctrl + ,`).
2. Search for `latex-workshop.docker.enabled` and set it to **false**.

---

## 📝 Creating a CV Using LaTeX

### 1. Create a New LaTeX File
- Open **VS Code**.
- Create a new `.tex` file (e.g., `cv.tex`).

### 2. Add LaTeX Code for CV
- Copy and paste contents of my repo file `CV.tex` into your `.tex` file  and edit with your information\
                  `or`\
Here is an example LaTeX code for creating a simple CV:

```latex
\documentclass[a4paper,10pt]{article}
\usepackage{geometry}
\geometry{left=1in,right=1in,top=1in,bottom=1in}

\begin{document}

\title{Curriculum Vitae}
\author{Your Name}
\date{}
\maketitle

\section*{Personal Information}
\begin{tabbing}
\hspace{3in} \= \hspace{2in} \= \kill
\textbf{Name:} \> Your Name \> \textbf{Date of Birth:} 01/01/1990 \\
\textbf{Email:} \> your.email@example.com \> \textbf{Phone:} (123) 456-7890 \\
\end{tabbing}

\section*{Education}
\textbf{University Name}, Bachelor of Science in Computer Science, 2010 - 2014

\section*{Experience}
\textbf{Company Name} - Software Engineer, 2016 - Present
\begin{itemize}
  \item Developed new features for the product.
  \item Collaborated with a team of 5 engineers.
\end{itemize}

\section*{Skills}
\begin{itemize}
  \item Programming Languages: Python, Java, LaTeX
  \item Tools: VS Code, Git, Docker
\end{itemize}

\end{document}
```
## 🔄 3. Compiling LaTeX Documents

To compile a `.tex` file:

1. Open your `.tex` file in VS Code
2. Press **`Ctrl + Shift + P`** and search:    
```
LaTeX Workshop: Build LaTeX Project
```
3. Select it and wait for the PDF to be generated.

If there are errors, check the **OUTPUT** panel (`Ctrl + Shift + U`) for logs.

  `OR`
Try running:
```sh
latexmk -pdf cv.tex
```
