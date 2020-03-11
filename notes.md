**Components I** - _the building block to modern application development_

- Components are:
  - Single modular pieces fo code
  - Usually consist of HTML, CSS, and JS
  - Reusable
  - D.R.Y.
  - Can stand alone

- When using a CSS *preprocessor* (LESS, SASS),  style your components in their own files and import them
    - ```@import custom-btn.less```
    - ```.custom-btn {// custom styles here}```

- _Almost_ a Component Example:

  - HTML:

  ```
  <div class="container>
      ...HTML Stuff...

  <button class="button large-button">THIS IS A BUTTON </button>
      ...HTML Stuff...

  </div>
  ```

  - CSS:

  ```
  .large-button {...styles...}
  ```

  - JS:

  ```
  let button = document.querySelectorAll('.button')
  button.forEach(b => {
      b.addEventListener('click', (event) => {
          alert("The button clicked says: ${event.target.textContent}")
      })
  })

  ```

  - *Component Example*:

    - HTML:

    ```
    <div class="container>
    ...HTML Stuff...
    </div>
    ```

    - CSS:

    ```
      .large-button {...styles...}
    ```

    - JS:

    ```
         //make it a function so it's D.R.Y.
    function buttonCreator(text) {

            //create button element
        let button = document.createElement('button'); 

            //give text to the button
        button.textContent = text; //give text to the button

            //adding the CSS classes to button
        button.classList.add('button'); //adding teh CSS class to button
        button.classList.add('large-button');

            //adding the event listener back in
        button.addEventListener('click', (event) => {
            alert("The button clicked says: ${event.target.textContent}")
        });

            //get the button out of the function
        return button;
    }
        //creating button by calling our new function
    const button1 = buttonCreator("This is a button1 component!");
    const button2 = buttonCreator("This is a button2 component!");

    console.log("The product of the buttonCreator function:, button1);

        //setting JS variable equal to a div-class from the HTML
    let container = document.querySelector('.container');

        //adding the button to the end of the container (could prepend for the begining)
    container.prepend(button1);
    container.appendChild(button2);
    container.appendChild(buttonCreator("Button Magic"));
    ```

- Creating Components from Array Data
 
    - HTML:

    ```
    <div class="container>
    ...HTML Stuff...
    </div>
    ```

    - CSS:

    ```
      .large-button {...styles...}
    ```

    - JS:

    ```
    const fakeData = [
        "Button ONe",
        "Button Two",
        "Button Three",
        "Button Four",
        "Button Five"
    ]

    function buttonCreator(text) {

        let button = document.createElement('button'); 

        button.textContent = text; //give text to the button

        button.classList.add('button'); //adding teh CSS class to button
        button.classList.add('large-button');

        button.addEventListener('click', (event) => {
            alert("The button clicked says: ${event.target.textContent}")
        });

        return button;
    }

    let container = document.querySelector('.container');

    
    let buttonArray = fakeData.map(item => {
        //returns a new array w/ the new item, after being manipulated by the callback
        let button = buttonCreator(item);
        return button;
    })

    buttonsArray.forEach(button => {
        container.appendChild(button);
    })

    /////Below is the fine way w/o using map /////

    fakeData.forEach(item => {
        let button = buttonCreator(fakeData[i]);
        container.appendChild(button[i]);
    });


    /////Below is the sad way w/o array methods////
    for(let i=0; i < fakeDate.length; i++) {
        let button = buttonCreator(fakeData[i]);
        container.appendChild(button[i]);
    }


    /////Below is the super sad alternative to the for loops/////

        const button1 = buttonCreator(fakeData[0]);
        const button2 = buttonCreator(fakeData[1]);
        const button3 = buttonCreator(fakeData[2]);


        let container = document.querySelector('.container');

        container.prepend(button1);
        container.appendChild(button2);
        container.appendChild(button3);
        container.appendChild(buttonCreator(fakeData[3]));
    ```
* [Lecture Notes](https://www.notion.so/Components-I-96090141608b468f94b070a78f49bbce)