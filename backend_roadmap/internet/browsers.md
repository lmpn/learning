# Browsers

A browser's main function is to present a web resource you choose by requesting it from the server and displaying it in the browser window.

Components
UI Backend: used to draw basic widgets (platform dependent)
JS Interpreter: parses and executes JavaScript
Networking: manages network calls using protocols like HTTP/FTP/etc.
Data Persistence: Persistent layer used to store several types of data like cookies.
UI
Rendering Engine: Responsible for rendering a specific web page. It parses an html or xml document which may contain elements like images(and other media) styled with CSS, lays out the elements, and paints them into the UI
Browser Engine: bridge between the UI and Rendering Engine which maps user actions to queries and handles of the rendering engine

## Common rendering engines
1. Google Chrome and Opera v.15+: Blink
2. Internet Explorer: Trident
3. Mozilla Firefox: Gecko
4. Chrome for iOS and Safari: WebKit

## Rendering engine main flow
Parsing HTML to construct DOM tree
- generates the DOM tree
- parses HTML and CSS
Render tree consctruction
- generates the Render tree
- includes sytling and order of dysplay
Layout of the render tree
- process of calculating the position of each node of the render tree
Painting the render tree
- paints each node using the UI backend
