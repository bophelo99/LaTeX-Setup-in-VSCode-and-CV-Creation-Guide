# LaTeX Setup and CV Creation Guide

This guide walks you through the process of setting up **LaTeX** in **Visual Studio Code (VS Code)**, fixing common errors, and creating a **CV** using LaTeX.

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

---

## ⚙️ Fixing LaTeX Workshop Errors

### **Error: "spawn latexmk ENOENT"**
This error means LaTeX Workshop can't find `latexmk`. Follow these steps to resolve:

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
Disable Docker in LaTeX Workshop:

1. Go to **VS Code Settings** (`Ctrl + ,`).
2. Search for `latex-workshop.docker.enabled` and set it to **false**.

---

## 📝 Creating a CV Using LaTeX

### 1. Create a New LaTeX File
- Open **VS Code**.
- Create a new `.tex` file (e.g., `cv.tex`).

### 2. Add LaTeX Code for CV

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
