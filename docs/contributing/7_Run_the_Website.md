# How to Run the OWASP MAS Website Locally

This guide will help you set up and run the OWASP MAS website locally on your machine. Follow the steps below to get started.

## Using Docker

The easiest way to run the website is by using Docker. The following commands will clone the necessary repositories, build the Docker image, and run the website, which will be accessible at [http://localhost:8000](http://localhost:8000).

```bash
git clone https://github.com/OWASP/mastg.git
git clone https://github.com/OWASP/masvs.git
git clone https://github.com/OWASP/maswe.git
git clone https://github.com/OWASP/mas-website.git
cd mas-website
docker build . -t mas-website
docker run --rm -it \
  -p 8000:8000 \
  -u $(id -u):$(id -g) \
  -e GITHUB_TOKEN \
  -v "$PWD":/workspaces/mas-website \
  -v "$REPO_ROOT/mastg":/workspaces/mastg \
  -v "$REPO_ROOT/masvs":/workspaces/masvs \
  -v "$REPO_ROOT/maswe":/workspaces/maswe \
  mas-website
```

By default, interactions with the Github API are disabled, which means some dynamically retrieved content will not be available. If you want to enable the Github API, [create a personal access token](https://github.com/settings/personal-access-tokens) and export it as an environment variable. Make sure to export this token in your shell before running the Docker container:

```bash
export GITHUB_TOKEN=<TOKEN>
```

## Without Docker

> **TLDR for advanced users:**
>
> - Clone the `mas-website`, `mastg`, `masvs` and `maswe` repos
> - Set up a virtual environment
> - Install dependencies from `mas-website/requirements.txt`
> - Add your token as an environment variable: [`export GITHUB_TOKEN=<TOKEN>`](https://github.com/settings/personal-access-tokens)
> - Run the website using `./run_web.sh`

### Prerequisites

Before running the website, ensure you have the following installed on your system:

- Python 3.8 or higher
- pip (Python package manager)
- Git
- Visual Studio Code (vscode)

[Create a personal access token](https://github.com/settings/personal-access-tokens) on Github and export this token as environment variable (e.g. in your .zshrc file):

```bash
export GITHUB_TOKEN=<TOKEN>
```

Alternatively, you can add your token inside of the `mas-website/run_web.sh` script. Open the script in a code editor for more information.

### Step 1: Clone the OWASP MAS Repositories

Run the following commands in your terminal:

```bash
git clone https://github.com/OWASP/mas-website.git
git clone https://github.com/OWASP/mastg.git
git clone https://github.com/OWASP/masvs.git
git clone https://github.com/OWASP/maswe.git
```

### Step 2: Open the OWASP MAS Website Repository in vscode

Run the following commands in your terminal:

```bash
cd mas-website
code .
```

### Step 3: Install Python Dependencies

It is highly recommended to use a virtual environment (venv) to manage dependencies and avoid conflicts with other Python projects.

Use vscode's [`Command Palette`](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette) (Press `⌘+Shift+P` on macOS or `Ctrl+Shift+P` on Windows/Linux)

1. Create a venv:
    - Press `⌘+Shift+P` -> `Python: Create Environment`
    - Select `"Quick Create"`
2. Select the venv as the Python interpreter:
    - Press `⌘+Shift+P` -> `Python: Select Interpreter`
    - Choose the venv you just created.
3. Install the dependencies
   - Press `⌘+j` to open the terminal
   - Run `pip install -r src/scripts/requirements.txt`

### Step 4: Run the Website

Run the following command in the terminal:

```bash
./run_web.sh
```

The script simply runs `mkdocs serve` with some additional arguments. Open the script in a code editor for more information.

Access the website at [http://localhost:8000](http://localhost:8000).

### Step 5: Debugging the Website

To debug the website:

- Go to `Run and Debug` in vscode (or press `⌘+Shift+D` on macOS)
- Select `Python: MkDocs Serve`
- Click the green play button to start debugging
- Set breakpoints in the code as needed
