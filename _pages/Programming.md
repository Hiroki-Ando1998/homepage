---
permalink: /Programming/
title: "Programming"
---

Programming enables faster and more efficient creation of slides and data analysis compared with interface-based operations (e.g., Excel and PowerPoint). 
The key advantages of programming can be summarized as follows:
- Efficiency: Automates repetitive tasks and reduces processing time
- Accuracy: Minimizes human error through standardized procedures
- Scalability: Handles large datasets with consistent performance
- Flexibility: Enables customized analyses and complex model implementation
- Reproducibility: Facilitates transparent and repeatable workflows
- Adaptability: Allows easy modification and rapid reanalysis under new conditions.

On the other hand, as a beginner in programming, I initially struggled to understand what software was available and which tools were suitable for specific purposes, encountering difficulties from the very first stages of adoption. 
I also found that installing the necessary tools and learning their basic usage required considerable time. 
Therefore, in this article, I aim to organize and summarize these aspects both as a personal reference and as a guide for other programming beginners facing similar challenges.


# GitHub
[GitHub](https://github.co.jp/) is a web-based platform for version control and collaboration that allows users to store, manage, and share code. It is built on [Git](https://git-scm.com/), a distributed version control system that tracks changes in files over time. By using GitHub, individuals and teams can keep a complete history of their projects, revert to previous versions if needed, and work on the same codebase simultaneously without conflicts.

- **Managing and version-controlling** analysis code and research projects
- **Sharing code and data** to ensure reproducibility and transparency
- Collaborating with other researchers across institutions
- Hosting documentation and research-related resources (e.g., project websites)
- Distributing software tools, models, and computational methods
- **Creating and sharing URLs** for PDFs (e.g., slides, CVs) and webpages, enabling easy and accessible dissemination of research outputs

GitHub is an useful tool to manage and organize code and files for tools such as R, LaTeX, and reveal.js.

- [Install_Video](https://www.youtube.com/watch?v=wDRoduig_98) & [install (Japanese)](https://www.kagoya.jp/howto/it-glossary/develop/howtousegithub/)
- [Making a webpage_Video](https://www.youtube.com/watch?v=Pof342wGt78)

# Visual Studio (VS) code
[VS Code](https://code.visualstudio.com/download) is a lightweight yet powerful source code editor that supports a wide range of programming languages and tools. Through its rich ecosystem of extensions, VS Code can be customized to provide language-specific features such as syntax highlighting, code completion, debugging, and integrated execution environments, making it suitable for both beginners and advanced users.

The key advantages of VS Code include:
- **Multi-language support**: Enables seamless use of **R, Python, LaTeX, reveal.js**, and many other languages within a single environment
- **Extensibility**: Offers a wide range of extensions to customize functionality for specific workflows
- **Integrated version control**: Provides built-in support for Git and seamless integration with GitHub
- **GUI-based Git operations**: Allows users to commit, push, pull, and manage changes without relying on command-line operations
- **AI-assisted coding**: Supports tools such as GitHub Copilot, which can suggest code completions, generate functions, and help debug or refactor code, thereby improving productivity and reducing development time
- **Workspace management**: Enables efficient handling of multiple files and projects in a unified interface
- **Preview and execution**: Supports real-time preview of outputs such as LaTeX documents and reveal.js presentations
- **User-friendly interface**: Lowers the barrier to entry for beginners while maintaining powerful features for advanced users
These features make VS Code a versatile and efficient tool for programming, data analysis, document preparation, and presentation development.

Although there are several ways to edit files (e.g., R file) from GitHub using VS Code, the most fundamental approach is to [create a local clone of the repository](https://www.youtube.com/watch?v=N7UT6nvCqoI).
- [Integration with GitHub]()
- [R in VS code]()
- [LaTex in VS code]()


# R and Rstudio
[R](https://www.r-project.org/) is a programming language and software environment specifically designed for statistical computing and data analysis. [RStudio](https://posit.co/download/rstudio-desktop/) is an integrated development environment (IDE) for R that enhances usability by providing a user-friendly interface, script editor, workspace management, and tools for visualization and package management. While Visual Studio Code can be used for R programming, making RStudio not strictly necessary, RStudio remains highly convenient as it is specifically designed for use with R.
From a research perspective, the key advantages of R include:
- **Advanced statistical capabilities**: Supports a wide range of statistical methods, from basic analyses to complex models (e.g., Bayesian inference, time-series analysis, and state-space models)
- **High-quality visualization**: Enables flexible and publication-ready graphics through packages such as ggplot2
- Open-source and free: Freely available, making it accessible to researchers worldwide without licensing costs
- Reproducibility: Code-based workflows allow analyses to be easily reproduced and verified
- **Extensive package ecosystem**: Thousands of user-contributed packages extend functionality across diverse research fields
- **Community and knowledge sharing**: Many researchers publicly share their code and methods, making it easier to replicate existing studies and build upon prior work


# LaTex
LaTeX is a document preparation system widely used in academia for writing papers and can be edited efficiently within VS Code
From a researcher’s perspective, the advantages of LaTeX include:
- High-quality typesetting: Produces professionally formatted documents with precise control over layout and typography
- **Excellent mathematical notation**: Handles complex equations clearly and consistently, far beyond what is easily achievable in Microsoft Word
- **Separation of content and formatting**: Authors focus on writing content, while formatting is handled systematically
- Reproducibility and version control: Plain-text source files integrate well with Git, enabling transparent revision tracking
- Cross-referencing and automation: Automatically manages references, citations, figure numbers, and tables
- **Scalability**: Efficiently handles large documents such as theses, books, and multi-author manuscripts

In comparison, Microsoft Word provides a more intuitive, WYSIWYG (What You See Is What You Get) interface, which is easier for beginners and suitable for simple documents. However, as documents become more complex—particularly with many equations, references, and figures—Word can become difficult to manage consistently. In contrast, LaTeX offers greater stability, precision, and reproducibility, making it the preferred choice for many researchers despite its steeper learning curve.Other tools for writing academic papers, such as [Quarto](https://quarto.org/docs/download/), are also available. It is best to choose a tool that aligns with both your own preferences and those of your collaborators.

- [install_Japanese](https://qiita.com/alpaca-honke/items/f30a2d04eedaa3c36a21#%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB)


# Reveal.js
[reveal.js](https://revealjs.com/) is an open-source framework for creating presentations using web technologies such as HTML, CSS, and JavaScript. One major advantage of reveal.js is that it can be used within Visual Studio Code, allowing users to write and manage slides alongside analysis code (e.g., R or Python). This integration enables a unified workflow in which figures, results, and slides can be generated and updated programmatically.

From a researcher’s perspective, the key advantages of reveal.js include:
- Reproducibility: Slides can be generated directly from code, ensuring consistency between analysis and presentation
- Flexibility and customization: Full control over layout, design, and interactivity using web technologies
- Integration with code: Easily incorporates dynamic content, such as plots or results generated from R or Python
- Version control compatibility: Plain-text files integrate naturally with Git and platforms like GitHub
- **Web-based sharing**: Presentations can be hosted online and shared via a URL, making them easily accessible without requiring specific software
- **Portability**: Runs in a web browser, making it platform-independent

In comparison, Microsoft PowerPoint offers a highly intuitive, graphical user interface that is easy to use and widely adopted. It is well suited for quickly creating slides without requiring programming knowledge. However, PowerPoint relies heavily on manual editing, which can make it less efficient for updating figures or maintaining consistency across slides, especially in data-driven presentations. In contrast, reveal.js emphasizes automation, reproducibility, and integration with analytical workflows. While it requires some familiarity with coding and web technologies, it provides substantial advantages for researchers who need to create dynamic, data-driven, and easily shareable presentations.
