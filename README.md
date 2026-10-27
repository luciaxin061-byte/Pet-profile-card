# Pet profile card - Meet Mochi 🐱

## Our project and group members

We are **Luxian Xin and Kate Osorio**. Our project is a pet adoption profile card made with HTML, CSS, and JavaScript for a fictional cat named Mochi. We want visitors who are interested in adopting a pet to quickly understand her basic information and personality, then see a clear next step. Our card is a class prototype, and Mochi’s profile details are fictional.

## Our project links

- [🐾 Try our live website](https://luciaxin061-byte.github.io/Pet-profile-card/)
- [Explore our source repository](https://github.com/luciaxin061-byte/Pet-profile-card)

We can also open `index.html` locally with `style.css` and `mochi.jpg` in the same folder. Our JavaScript is inside `index.html`; we do not have a separate JavaScript file or a build step.

## Our design intentions and rationale

We used a simple vertical card so visitors can read one pet’s story in a clear order: photo, name, age, gender, location, introduction, personality tags, and the final “Meet Mochi” button. Our photo and name introduce Mochi first, while the aligned information labels help visitors find basic details quickly. Our introduction adds her interests, including sunny windows, soft blankets, and feather toys. Our “Gentle,” “Curious,” and “Playful” tags make her personality easy to scan.

We kept the warm cream and brown palette and the “Meet Your New Friend” heading suggested by ChatGPT because we felt they looked harmonious and welcoming. Our yellow, oval “Meet Mochi” button follows our sketch and stands out as the intended next step. It is currently a placeholder, as we explain below.

We chose a real cat photo instead of the AI-provided cartoon illustration because we wanted visitors to feel more connected to Mochi. We changed “Intro” to “Introduction” for clarity and increased the Name, Age, Gender, Location, and Introduction labels from 14px to 17px for readability. We also chose Caveat at weight 600 for Mochi’s name to give it a more personal, handwritten feeling. Our photo-click interaction is intended to help visitors learn about her beyond a still image, although our current version needs a video selected from the visitor’s device.

### Our original sketch

[Our original sketch showing a centered pet picture, labeled profile information, an introduction, and a large oval Meet button.](sketch.jpg)

We included the sketch already supplied during our project, rather than creating a new image as evidence. Our finished card keeps its main order and adds a status line, location, personality tags, and a video dialog.

## Our AI learning and human decisions

We used ChatGPT as a thinking partner to adapt our webpage assignment into a pet profile card. ChatGPT suggested the initial layout and starter HTML/CSS, and helped translate our later requests into code. Our decisions were to keep the warm palette and heading, use our sketch for the layout, replace the cartoon with a real photo, clarify the wording, enlarge the labels, and request the photo-click video interaction. We evaluated the suggestions against our goal of making Mochi easy to understand rather than accepting every initial choice.

Our iterations helped us connect design decisions with code. Replacing the illustration showed us how an HTML image changes the feeling of the card. Adjusting CSS font sizes helped us think about readability, while changing “Intro” showed us that wording is also part of the interface. We removed “Choose a video of Mochi from your device to watch it here.” because we thought it sounded like a developer instruction rather than visitor-facing content. Our dialog still keeps the file chooser’s label and the explanation that a selected video stays on the device.

We also learned to distinguish a coded interaction from a fully tested experience. We reviewed the dialog, but we did not have a suitable Mochi video to test the intended viewing experience completely. We cannot claim that video playback succeeded just because the event handlers exist. Our recorded history supports these specific revisions; we have not documented additional experiments, failed prompts, or measured usability results.

| Our choice | How our actual code expresses it |
| --- | --- |
| A clearly organized pet profile | We use `<main>` and `<article class="pet-card" aria-labelledby="pet-name">` for the card, an `<h1>` for Mochi’s name, a `<dl>` with `<dt>`/`<dd>` pairs for age, gender, and location, and labeled sections for the introduction and personality. |
| A photo that also opens an interaction | We place `<img src="mochi.jpg">` inside `<button class="pet-avatar">`. Our image has descriptive alt text, and our button has an accessible name, `aria-haspopup="dialog"`, and a connection to the dialog through `aria-controls`. Our `.pet-avatar img` rule uses `width: 100%` and `height: auto` to preserve the photo’s proportions. |
| Aligned labels and scannable tags | We use CSS Grid for `.name-row`, `.pet-details > div`, and `.intro`. Our `.traits` list uses wrapping Flexbox and rounded borders so the personality words appear as separate tags. Our CSS `::after` rules add the label colons. |
| Our colors and typography | We use `#fffdf7` for the card, brown text, and `#ffd348` for the meeting button. Our label selector sets `font-size: 17px`; our `h1` uses `"Caveat", cursive` and `font-weight: 600`. We load Caveat through Google Fonts. |
| A layout intended for smaller screens | We set a 560px maximum card container width and use `@media (max-width: 480px)` to reduce padding, photo width, label-column width, and the name size. These rules express our responsive intent; their presence alone does not prove the layout works on every device. |
| Opening and closing our video dialog | Our photo button’s `click` handler calls `videoDialog.showModal()`. Our close-button handler calls `.close()`, and our dialog click handler closes it when a click is outside its bounds. Our native `<dialog>` also supports Escape. In our `close` handler, we pause the video, reset its time when media is ready, and return focus to the photo button. |
| Selecting a local video | Our file input uses `accept="video/*"`. In its `change` handler, we inspect the selected file’s type, with an extension fallback when its type is empty, then use `URL.createObjectURL(file)` as the video source. We revoke the previous object URL when replacing a video, show the player, and attempt playback. Our controls remain available when automatic playback is blocked, and our video `error` handler displays a message if playback fails. |
| Visible keyboard focus | We include `:focus-visible` outlines for buttons and the file input. Our video has native playback controls and `playsinline`. We still need broader keyboard and assistive-technology testing before making accessibility claims. |

