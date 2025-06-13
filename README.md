# Odesli Song Link Fetcher 🎵

A Python command-line tool to fetch song links from various music streaming platforms using the Odesli (Song.link) API. This tool allows users to retrieve platform-specific links for songs or albums, filter services, and save results to a file with colorful console output.

## Table of Contents

- [Features](##-Features-)
- [Requirements](##-Requirements-)
- [Installation](##-Installation-)
- [Usage](##-Usage-)
  - [Command-Line Arguments](###Command-Line-Arguments-)
  - [Examples](###-Examples-)
- [Output Format](##-Output-Format-)
- [Error Handling](##-Error-Handling-)
- [Dependencies](##Dependencies-)

## Features ✨

- **Fetch Links**: Retrieve song or album links from multiple platforms (Spotify, Apple Music, YouTube, etc.) using a single URL.
- **Service Filtering**: Select specific platforms or use a fallback service if a preferred one is unavailable.
- **Colorful Output**: Console output with color-coded service names for better readability.
- **File Input/Output**: Process multiple URLs from a file and save results to an output file.
- **Country Support**: Specify a user country code to fetch region-specific links.
- **Error Handling**: Robust handling of API errors and invalid inputs.

## Requirements 📋

- Python 3.6 or higher
- Internet connection to access the Odesli API
- Required Python packages (see [Dependencies](#dependencies-))

## Installation 🛠️

1. Clone or download this repository:

   ```bash
   git clone https://github.com/mqinlwll/OdesliPy/.git
   cd OdesliPy
   ```

2. Install dependencies using pip:

   ```bash
   pip install -r requirements.txt
   ```

   Or directly install the required packages:

   ```bash
   pip install requests colorama
   ```

## Usage 🚀

Run the script using the `python odesli.py` command with appropriate arguments. You can provide a single URL or a file containing multiple URLs.

### Command-Line Arguments 🖥️

| Argument         | Description                                                  | Required?                  |
| ---------------- | ------------------------------------------------------------ | -------------------------- |
| `--url`          | Single song or album URL (e.g., Spotify or Apple Music link) | Yes (if `--file` not used) |
| `--file`         | Text file containing URLs (one per line)                     | Yes (if `--url` not used)  |
| `--country`      | User country code (e.g., `US`, `UK`) for region-specific links | No                         |
| `--songIfSingle` | Treat singles as songs (boolean, e.g., `True` or `False`)    | No                         |
| `--select`, `-s` | Space-separated list of services to fetch (e.g., `spotify tidal`) | No                         |
| `--fallback`     | Fallback service if a selected service is unavailable (e.g., `spotify`) | No                         |
| `--output`, `-o` | Output file to save links                                    | No                         |

### Examples 📚

1. **Fetch links for a single URL**:

   ```bash
   python odesli.py --url "https://open.spotify.com/track/4cOdK2wGLETKBW3PvgPWqT" --country US
   ```

   Output: Links for available platforms (e.g., Spotify, Apple Music, YouTube).

2. **Fetch specific services with a fallback**:

   ```bash
   python odesli.py --url "https://music.apple.com/us/album/1440903200" -s tidal deezer --fallback spotify
   ```

   Output: Links for Tidal and Deezer, or Spotify if unavailable.

3. **Process multiple URLs from a file and save to output**:

   ```bash
   python odesli.py --file urls.txt --output links.txt
   ```

   Input file (`urls.txt`):

   ```
   https://open.spotify.com/track/4cOdK2wGLETKBW3PvgPWqT
   https://music.apple.com/us/album/1440903200
   ```

   Output: Saves links to `links.txt`.

## Output Format 🖨️

- **Console Output**: Displays the URL being processed, followed by a list of platform-specific links with color-coded service names (e.g., Spotify in green, Apple Music in red).

- File Output

  : If 

  ```
  --output
  ```

   is specified, saves each link (one per line) to the specified file.

  Example console output:

  ```
  Results for URL: https://open.spotify.com/track/4cOdK2wGLETKBW3PvgPWqT
  Available Links:
  ----------------------------------------
  Spotify: https://open.spotify.com/track/4cOdK2wGLETKBW3PvgPWqT
  Apple Music: https://music.apple.com/us/song/1440903200
  YouTube: https://www.youtube.com/watch?v=example
  ----------------------------------------
  ```

## Error Handling ⚠️

- **Invalid URLs**: Skips URLs that return no links and prints a warning.
- **API Errors**: Catches HTTP or JSON decode errors and displays them in red.
- **File Errors**: Properly closes output files and handles file read errors gracefully.

## Dependencies 🧩

- `requests`: For making HTTP requests to the Odesli API.
- `colorama`: For colored console output.
- `argparse`: For parsing command-line arguments (built-in).
- `json`: For parsing API responses (built-in).

Install dependencies:

```bash
pip install requests colorama
```

