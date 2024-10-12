Here's a detailed `README.md` that describes the provided code and its functionality:

---

# Video Transcript Summarizer with Image References

## Overview

This project is designed to extract transcripts from YouTube videos, identify visual references (e.g., images, diagrams, slides) within the transcripts using an AI language model, and generate HTML reports with structured summaries and clickable links to specific parts of the video. The tool aims to preserve detailed information, ensuring that no critical content is lost during the summarization process.

## Features

- **Transcript Extraction**: Retrieves video transcripts from YouTube using the `youtube_transcript_api`.
- **Video Information Retrieval**: Fetches video details like title, thumbnail, likes, description, duration, and statistics using the YouTube Data API.
- **Image Reference Detection**: Uses OpenAI's language model to identify references to images, graphs, and diagrams within the transcript.
- **Detailed Summarization**: Summarizes video content in detail while retaining all relevant information and visual references.
- **Report Generation**: Creates structured reports with figures and clickable links to specific timestamps in the video.
- **HTML Report Export**: Saves the report as an HTML file, including video information and referenced figures.
- **File Versioning**: Automatically creates a versioned filename to avoid overwriting existing files.

## Prerequisites

- Python 3.x
- OpenAI Python SDK (`openai`)
- Google API Client for YouTube (`googleapiclient`)
- YouTube Transcript API (`youtube_transcript_api`)
- `pytube` for video details
- `fpdf2` for PDF generation (if needed)
- `tqdm` for progress visualization

## Installation

1. **Clone the repository**:

   ```bash
   git clone https://github.com/yourusername/your-repository.git
   cd your-repository
   ```
2. **Install required packages**:

   ```bash
   pip install openai google-auth google-auth-oauthlib google-auth-httplib2 google-api-python-client youtube-transcript-api pytube fpdf2 tqdm
   ```
3. **Setup API keys**:

   - Store your OpenAI API key and YouTube Data API key in `.key` files:
     - `openai.key` in the `key_path` directory for the OpenAI API.
     - `youtube.key` in the `key_path` directory for the YouTube Data API.

## Usage

### Step 1: Configure and Run the Script

- Update the `youtube_urls` list with the URLs of the YouTube videos you want to process.
- Set the `playlist_name` and `summary_folder` variables to specify where the reports will be saved.
- Run the colab notebook (can also be copied as video_summary_generator.py):
  ```bash
  python video_summary_generator.py
  ```

### Step 2: What the Script Does

1. **Video Information Extraction**:

   - Extracts video ID from each YouTube URL.
   - Fetches video title, description, and thumbnail using `pytube`.
   - Uses the YouTube Data API to gather video statistics (likes, duration) and channel details.
2. **Transcript Retrieval and Processing**:

   - Retrieves the video transcript using `youtube_transcript_api`.
   - Uses OpenAI's GPT models to identify references to images or diagrams in the transcript, specifying the time and description.
3. **Chunking and Summarizing**:

   - Divides long transcripts into manageable chunks to avoid exceeding the model's token limits.
   - Summarizes each chunk, preserving detailed information and references.
   - Combines the chunked summaries into a coherent final report.
4. **Report Generation**:

   - Enhances the transcript with video descriptions and figures.
   - Inserts figure references as clickable links with timestamps.
   - Structures the report into sections with descriptive headings.
5. **HTML Export**:

   - Saves the final report as an HTML file, displaying the video's title, thumbnail, and summarized content.
   - If the file already exists, it increments the version number to avoid overwriting.

### Step 3: Output

The script generates a structured HTML report for each video, including:

- Video title and thumbnail.
- Detailed summary of the transcript.
- Hyperlinks to referenced images or diagrams within the transcript.
- Summarized comments for context.
- The report is saved in the `summary_folder` with a versioned filename, e.g., `playlist_name.1.html`.

### Example Output

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Video Summaries</title>
    <style>
        /* Styles for the HTML report */
    </style>
</head>
<body>
    <div class="report">
        <h1>1. Understanding Quantum Physics</h1>
        <img src="https://example.com/thumbnail.jpg" alt="Thumbnail" />
        <p>The video covers the basics of quantum physics, including wave-particle duality...</p>
        <div class="figures">Referenced Figures:</div>
        <p><a href="https://youtube.com/watch?v=example&t=120">[FIGURE 1: Diagram of wave-particle duality]</a></p>
    </div>
    <!-- More reports... -->
</body>
</html>
```

## Notes

- Ensure that your API keys are correctly set up in the specified `.key` files.
- Adjust the `max_words_per_chunk` and `overlap_words` parameters if the transcript size causes issues.
- If running in Google Colab, the script supports automatic mounting of Google Drive for file access.

## Author

- **Shashwat Gupta** - [Shashwat Gupta](https://github.com/ShashwatGupta2001/)

## Contributing

Feel free to submit pull requests for improvements or open issues for bug reports and feature requests.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

This `README.md` provides a clear and detailed overview of your code, guiding users on how to set it up and run it. If you have any more details you'd like to include or modifications, let me know!
