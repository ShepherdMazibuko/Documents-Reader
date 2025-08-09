A simple, user-friendly document reader that supports multiple file types and includes a text-to-speech feature.
Calm Reader is a web-based Progressive Web App (PWA) designed to provide a distraction-free reading experience. It allows you to upload and read various document formats, including .docx, .pdf, .epub, and .txt, and can even read them aloud using your device's built-in text-to-speech functionality.
Features
 * Multi-Format Support: Reads .docx, .pdf, .epub, and .txt files.
 * Text-to-Speech: Listen to your documents with customizable voice and speed settings.
 * Progressive Web App (PWA): Designed for offline use and fast loading times (though some PWA files like manifest.json and service-worker.js are referenced, the code for them is not included in the provided file).
 * Recent Documents: Keeps a list of recently opened files for easy access.
 * Simple Interface: A clean, mobile-first design focused on readability and ease of use.
How It Works
Core Technologies
The application is built using standard web technologies: HTML, CSS, and JavaScript. It leverages several external libraries to handle the parsing of different file types:
 * mammoth.js: Used to extract text from .docx files.
 * PDF.js: A powerful library for rendering and parsing .pdf files.
 * epub.js: Handles the parsing of .epub files.
Code Breakdown
index.html
This file serves as the main structure of the application. It's a single-page app with several sections (<section>) that are shown or hidden based on which tab is active.
 * Header: Contains the app title and navigation tabs (Browse, Recently Opened, Favorites, About).
 * Main Content: A container for all the different views.
   * Browse Tab: The default view where users can upload files.
   * Recent/Favorites Tabs: Display lists of documents.
   * Reader View: This is the main reading area. It shows the document title, cover, the text itself, and playback controls (play/pause, next/previous sentence) and settings (voice, speed).
 * JavaScript Logic: The <script> tag at the end of the <body> contains all the application's logic.
   * PWA Setup: Checks for serviceWorker support and registers service-worker.js.
   * DOM Caching and State: Defines variables for all the main HTML elements and key state variables (sentences, isPaused, recentDocuments, etc.).
   * File Parsing: The parseDocument() function is the heart of the app's document handling. It checks the file extension and uses the appropriate library (mammoth, pdfjsLib, ePub) to extract the text and, if possible, a cover image.
   * Text-to-Speech: Functions like speakCurrentSentence() and populateVoiceList() handle the voice synthesis. The code uses the browser's native SpeechSynthesisUtterance and speechSynthesis APIs.
   * UI Management: Functions like showTab() and showReaderView() manage which parts of the interface are visible. Event listeners are attached to buttons, sliders, and file inputs to handle all user interactions.
style.css
This stylesheet is designed with a mobile-first approach and a focus on performance.
 * Color Palette: It uses CSS variables for a consistent and easy-to-change color scheme.
 * Layout: The main layout is flexible and responsive, using flexbox to arrange elements.
 * Reader View Styling: Special styles are applied to the reader, including a background highlight for the currently spoken sentence (.highlight).
 * Performance: The CSS comments mention the removal of complex animations and shadows to ensure the app runs smoothly on lower-end mobile devices.
 * Media Queries: There are specific @media queries to adjust the layout for larger screens, ensuring a good experience on tablets and desktops.
Future Improvements
 * Implement a local storage solution for "Favorites."
 * Add more robust PWA features, such as caching for full offline access.
 * Enhance the reader view with features like font size adjustment, theme switching (dark mode), and a progress indicator.
