# piskel-clone

</br>
</br>

## Functional requirements
You need to create a simplified clone of the https://www.piskelapp.com/, a web-based tool for Spriting and Pixel art.
An overview of the features can be found in this playlist: https://www.youtube.com/playlist?list=PLO3K3VFvlU6Akj3W29_nMLZFnwNOVbAzI

### Required functionality
#### Minimal scope
- Canvas sizes: 32x32 / 64x64 / 128x128 user-defined units
- Tools
    - Pen. Required size is 1 unit. Other unit sizes (2, 3, 4) are optional.
    - Color select (Primary/Secondary)
    - Paint bucket 
    - Eraser
- Preview
    - Small animation preview window in the top right corner 
    - Full screen mode
- Frames
    - Ability to add/delete a frame
    - Ability to reorder a frame via Drag and Drop
    - Ability to duplicate a frame
- Export the final result 
    - to local file system in any format (own format / .piskel / .gif / .apng)
- User session 
  - Current session should be saved and be accessible when user opens up the page again.

### Full scope
- Tools
  - Canvas sizes: 32x32 units / 64x64 units / 128x128 units
  - Paint all pixels of the same color
  - Stroke (to draw straight lines)
  - Rectangle
  - Circle
  - Move
  - Shape selection
  - Lighten
  - Dithering
- Layers
  - Ability to add/delete a layer
  - Ability to move the layer up/down
- Export the final result 
  - Upload the GIF to giphy.com using upload API https://developers.giphy.com/docs/
  - As a custom .piskel
  - As an own format to filesystem with ability to open it later
  - As a .apng
  - As a .gif
- Keyboard shortcuts 
  - All actions should be available via keyboard shortcuts
  - Modal window to change keyboard shortcuts
- Landing page. This page should include the following information:
   - Screenshots
   - Animation examples
   - Implemented functionality overview
   - Link to the editor itself
   - Information about the author

#### Tools

If modifier (Ctrl, Shift) changes the behaviour significantly, it should count as separate tool.

## Technical requirements:
1) Browser support: latest version of Google **Chrome**.
2) Usage of **JS/ES2015+** or **TypeScript**.
3) You can use libraries and frameworks like React / Angular / Vue / jQuery /Bootstrap / Lodash / wrapper for file formats / API utilisation.
4) Final version of the editor should be **available via a link**. The easiest way to do so is to host your project on GitHub pages / Google Firebase / Heroku / Netlify / any other hosting.
5) Usage of Jest / any other tool for writing tests. You also need to setup test coverage output in the package.json. Your tests need cover the following code:
   1) Utilities, pure functions
   2) UI components
   3) Tools functionality (i.e. adding pixels, changing pixels, adding rectangle / circle)
6) Have to use browser's Canvas API to draw frames.

### Requirements to the commits, PR, repository
* [stage2-tasks-requirements](https://github.com/rolling-scopes-school/docs/blob/master/ru/stage2-tasks-requirements.md)
* worklog of the project

#### worklog

To show process of development it needs to describe small amount of time and what work was accomplish during that time.

##### Example

You need to provide high level, feature base (what need to score) description. 


| Start time  | End time | time spent | feature |
|-----------|-------------|-------------|-------------|
| May 27 | Jun 6 | 30h | base structure of the project |
| Jun 7 | Jun 7 | 10h | frame management implementation |
| Jun 8 | Jun 10 | 8h | Lighten, Dithering tools implementation |
| Jun 11 | Jun 12 | 5h | layers implementation |
| Jun 12 | Jun 12 | 10h | bug fixing in canvas implementation  


Total: 63h

### Requirements to the quality of code
- Don't use nested SetTimeout, synchronization of code using timeouts etc. Use promises/async/await where it's possible.
- Don't use magic number instead of named constants.  
  For example, instead of  
  `if (event.keyCode === 32 || event.keyCode === 13) {….}`  
  use  
  `if (event.keyCode === KeyboardEvent.SPACE || key === KeyboardEvent.ENTER ) {….}` etc.
- Don't use functions that have more than 40 lines of code (excluding variable declarations).
- Minimal use of ternary operators.
- Use pure functions where it's possible. If you haven't heard this term before, you can start your acquaintance [here](https://medium.com/@jamesjefferyuk/javascript-what-are-pure-functions-4d4d5392d49c) or [here](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976) 
- Use meaningful names for variables. Avoid single characters for variable names (i, n, j, d, etc.), abstract or common names (obj, arr, num, item1, etc.)
- Use the eslint with airbnb for all js code 


### Work in team
It is possible to work together in 2-3 person team. To work together and get additional score points a student needs:

* to work in one repository
  * correctly merge PR to observe everyone commit
  * person should implement one feature
  * the student need to list all feature which was implemented by him personally
* to create PR in the private repo in rs (as usial task)
  * in result it will be 
    * one repo for 2 students common work
    * 2 pr in private student repos

The presentation should be done by student who has the lower score by time of presentation.

If all requirements to team work are met, the students will recieve their implemented score points + 30% of score of student who has the less points 

Example 1:

Student1 and student2 work together.
Student1 implements 300 score points.
Student2 implements 150 score points.

If students create common repo, correctly merge / commit features with good commit messages, they will recieve additional 50 points.

So, their score will be 

* Student1 = 300 + 50 = 350
* Student2 = 150 + 50 = 200

Example 2: 

Student1, student2, student3 work together.
Student1 implements 190 score points.
Student2 implements 100 score points.
Student3 implements 60 score points.

If students create common repo, correctly merge / commit features with good commit messages, they will recieve additional 20 points.

So, their score will be 

* Student1 = 190 + 20 = 210
* Student2 = 100 + 20 = 120
* Student3 = 60 + 20 = 80

Example 3: 
Student1 and student2 work together.
Student1 implements 200 score points.
Student2 implements 250 score points.

The students dont separate their features and dont have worklog. 

They will recieve - 30 fine for absent worklog and near -20 fine for incorrect commit messages:
* Student1 = 200 - 50 = 150
* Student2 = 250 - 50 = 200

### Project structure. Organization of files and folders (example):
Usage of webpack is mandatory! Components directories should include all the needed resources and styles. For example, by removing folder `modal-dialog` all styles related to this dialog will be removed as well.
    
    dist
    src
    ├── components                
    │   ├── loading
    │   ├── modal-dialog
    │   ├── frames-list
    │   ├── layers-list
    ├── screens
    │   ├── canvas
    │   │   ├── images
    │   │   ├── index.html       # template
    │   │   ├── index.scss       # styles
    │   │   ├── index.js         # logic
    │   ├── preview
    │   ├── export
    ├── app.js                   # main entry point.
    webpack.config.js
    README.md

Notes for Webpack usage: 
- There is no point in putting your code inside an Immediately-invoked Function Expression.
- There is no point in applying 'use strict' mode.

## Delivery process and score criteria
### Delivery process:
- You'll have up to **15 minutes** to present your project.
- Other students may attend / ask you questions.
- Presentation can be done offline or online depending on the location/opportunities of the reviewers.
- The final scoring and reviewing will be performed by a select reviewer, **NOT** by your mentor from stage#2. The list "*student - reviewer*" will be published after the deadline.

