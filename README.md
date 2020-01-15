# Note Taker with Node.js and Heroku

Created an application that can be used to write, save, and delete notes. This application use an express backend and save and retrieve note data from a JSON file.

- [Applied to Heroku](https://polar-anchorage-14528.herokuapp.com/)

- [Applied to My Reponsive Portfolio](https://eunsoojung.github.io/Responsive-Portfolio/portfolio.html)

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

```bash
# Install puppeteer
npm i express

# Run
node server.js
```

## Preview

[![Note-Taker](https://github.com/EunsooJung/Developer-Profile-Generator/blob/master/assets/09-Dev-Profile-Gen-Preview.gif)](https://github.com/EunsooJung/Developer-Profile-Generator/blob/master/assets/09-Dev-Profile-Gen-Preview.gif)

## Usage

### Basic Usage

To get Note Taker, after downloading, you need to make sure Git Bash terminal open and looking at the correct folder. When you are within the correct location, you may type the following commands to ask her for information:

- node server.js

[![Start-Note-Taker-Server](https://github.com/EunsooJung/Developer-Profile-Generator/blob/master/assets/09-Dev-Profile-Gen-Preview.gif)](https://github.com/EunsooJung/Developer-Profile-Generator/blob/master/assets/09-Dev-Profile-Gen-Preview.gif)

### Guidelines:

- Proceeds as follows:

The user will be use to write, save, and delete notes.

1. Open Note Taker landing page
2. Click "Get Started" button
3. Click "New" button

- Input Note Title
- Input Note Text

4. Click "Save" button
5. Click "Delete Button"

### Code Snippet

- Project structure
  [![Start-Note-Taker-Server](https://github.com/EunsooJung/Developer-Profile-Generator/blob/master/assets/09-Dev-Profile-Gen-Preview.gif)](https://github.com/EunsooJung/Developer-Profile-Generator/blob/master/assets/09-Dev-Profile-Gen-Preview.gif)

- Routes:
  1. public/assets/js/index.js: UI logic controller
  1. routes/apiRoute.js: Implements Notes API to get, save and delete notes.
  1. routes/htmlRoute.js: Implements html rendering API
  1. db/notes.js: Inplements class to read, save, and delete notes data in to the db.json

```javascript
...
// setup id constructor in notes.js
  constructor() {
    this.idDum = 0;
  }
// setu to read and write notes data file into the db.json file
  read() {
    return readFileAsyn('db/db.json', 'utf8');
  }

  write(note) {
    return writeFileAsync('db/db.json', JSON.stringify(note));
  }
...
// index.js check point
// getNotes to get all notes from the db
var getNotes = function() {
  return $.ajax({
    url: "/api/notes",
    method: "GET"
  });
};
...
// Control to activeNote, display or render empty inputs
var renderActiveNote = function() {
  $saveNoteBtn.hide();

  if (activeNote.id) {
    $noteTitle.attr("readonly", true);
    $noteText.attr("readonly", true);
    $noteTitle.val(activeNote.title);
    $noteText.val(activeNote.text);
  } else {
    $noteTitle.attr("readonly", false);
    $noteText.attr("readonly", false);
    $noteTitle.val("");
    $noteText.val("");
  }
};
...
// Delete Note
var handleNoteDelete = function(event) {
  // prevents click listener
  event.stopPropagation();

  var note = $(this)
    .parent(".list-group-item")
    .data();

  if (activeNote.id === note.id) {
    activeNote = {};
  }

  deleteNote(note.id).then(function() {
    getAndRenderNotes();
    renderActiveNote();
  });
};

```

## Built With

- [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [Javascript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [Node.js](https://nodejs.org/en/)
- [express.js](http://expressjs.com/)
- [heroku-cloud](https://www.heroku.com/home)

## Authors

- **Michael(Eunsoo)Jung**

* [Note Taker: Demo](https://polar-anchorage-14528.herokuapp.com/notes)
* [My Portfolio](https://eunsoojung.github.io/Responsive-Portfolio/portfolio.html)
* [Link to Github](https://github.com/)
* [Link to LinkedIn](www.linkedin.com/in/eun-soo-jung/)

## License

This project is licensed under the MIT License
