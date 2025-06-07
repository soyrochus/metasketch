# Metasketch 

Metasketch is a collaborative web application that enables non-developers to design, organize, and export living functional documents with the help of AI, using an intuitive, project-based interface.

## CHANGE HERE ....

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/soyrochus/metasketch
   cd petit
   ```
2. **Install dependencies using [uv](https://github.com/astral-sh/uv):**
   ```bash
   uv sync
   ```

3. **Activating the virt environment:**
   
   - **Linux/Mac:**
     ```bash
     source .venv/bin/activate
     ```
   - **Windows (cmd):**
     ```cmd
     .venv\Scripts\activate.bat
     ```
   - **Windows (PowerShell):**
     ```powershell
     .venv\Scripts\Activate.ps1
     ```

4. **Run the application:**
   ```bash
   uvicorn matasketch.web:app --reload
   ```
   or 
   ```bash
   python -m metasketch
   ```

## Configuration

1. Create a `.env` file in the project root containing your OpenAI API key:

   ```dotenv
   OPENAI_API_KEY=your_key_here
   ```

2. Alternatively, set the `OPENAI_API_KEY` environment variable:

   ```bash
   export OPENAI_API_KEY=your_key_here
   ```


## License and Copyright

Copyright © 2025, Iwan van der Kleijn

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.