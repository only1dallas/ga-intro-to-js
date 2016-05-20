# Demo Scripts




## Set Up the Code: 5 minutes

`<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.0.0-beta1/jquery.min.js"></script>`

`<script src="js/scripts.js"></script>`




### Twitter Character Limit Demo: 5 Minutes

```
// decide on a char limit to use
// store the "characters left" element so we can add to it
// store the textarea so we can determine what's in it
// add initial character limit
// when the user types text into the box
    // subtract what's in the textarea from the char limit
    // add that nubmer to the characters left field
    // if it's over the limit
        // turn it red
    // if it's not over th elimit
        // make sure it isn't red


// var tweet = document.getElementById('tweet');
// var charLeft = document.getElementById('char-left');
// var maxChar = 100;
// var charCount = function(){
//     charLeft.innerHTML = maxChar - tweet.value.length;
//     if(tweet.value.length >= maxChar){
//         charLeft.className = 'over-limit';
//     } else {
//         charLeft.className = '';
//     }
// };
// tweet.onkeydown = charCount;
// charLeft.innerHTML = maxChar;
```




## JavaScript Student Registry: 15 Minutes

```
<article class="registry">
    <div class="registry__inner">
        <h2>Student Registry</h2>
        <input type="text" name="students" id="js-student-text" />
        <input type="submit" value="Add Student" id="js-student-submit" />
        <div class="registry__extras">
            <input type="submit" id="js-students-num" value="Number of Students" />
            <input type="submit" id="js-students-list" value="List Students" />
            <input type="submit" id="js-students-alpha" value="Alphabetical" />
            <input type="submit" id="js-students-reverse" value="Reverse Alpha" />
            <div id="js-student-output" class="registry__output"><!-- js students list --></div>
        </div>
    </div>
</article>
```

```
/*------------------------------------*\
    ::Student Registry
    ----------------------------------
    HTML:
    <article class="registry">
        <div class="registry__inner">
            <h2>Student Registry</h2>
            <input type="text" name="students" id="js-student-text" />
            <input type="submit" value="Add Student" id="js-student-submit" />
        </div>
    </article>
\*------------------------------------*/
// find the text field and store it in a variable
var text = document.getElementById('js-student-text');
// find the submit button and store it in a variable
var submit = document.getElementById('js-student-submit');
// create an empty array to store student names later
var students = [];
// if a user clicks the submit button
submit.onclick = function(){
    // get the value of the text box
    var textVal = text.value;
    // if the value is not Tomas
    if(textVal !== 'Tomas'){
        // add that value to the empty student array
        students.push(textVal);
    // if the value is Tomas
    } else {
        // open an alert that says "Tomas is an instructor"
        alert('Tomas is an instructor');
    }
    // for each name in the students array
    for(var i = 0; i < students.length; i++){
        // console.log the students name in the console
        console.log(students[i]);
    }
};
```





## Extending the Registry: 15 Minutes

```
/*------------------------------------*\
    ::Extending the Student Registry
    ----------------------------------
    Add HTML:
    <div class="registry__extras">
        <input type="submit" id="js-students-num" value="Number of Students" />
        <input type="submit" id="js-students-list" value="List Students" />
        <div id="js-student-output"><!-- js students list --></div>
    </div>
\*------------------------------------*/
// create a function named numStudents
function numStudents(){
    // alert 'there are x students in the class'
    alert('There are ' + students.length + ' students in the class');
}
// when a button of id js-students-num is clicked
document.getElementById('js-students-num').onclick = function(){
    // trigger the numStudents function
    numStudents();
};
// create a function called writeStudents
function writeStudents(){
    // store the output div
    var studentOutput = document.getElementById('js-student-output');
    // empty the output div
    studentOutput.innerHTML = '';
    // for each student in the students array
    for(var i = 0; i < students.length; i++){
        // add them to a div of id js-student-output w/o erasing previous
        studentOutput.innerHTML = studentOutput.innerHTML + ' ' + students[i];
    }
}
// when a button of id js-students-list is clicked
document.getElementById('js-students-list').onclick = function(){
    // trigger the writeStudents function
    writeStudents();
};
```

```
/*------------------------------------*\
    ::Registry: Extra Credit
    ----------------------------------
    <input type="submit" id="js-students-alpha" value="Alphabetical" />
    <input type="submit" id="js-students-reverse" value="Reverse Alpha" />
\*------------------------------------*/
// when the students-alpha button is clicked
document.getElementById('js-students-alpha').onclick = function(){
    // store the output div
    var studentOutput = document.getElementById('js-student-output');
    // empty the output div
    studentOutput.innerHTML = '';
    // sort the students array
    students.sort();
    // for each student in the students array
    for(var i = 0; i < students.length; i++){
        // add them to a div of id js-student-output w/o erasing previous
        studentOutput.innerHTML = studentOutput.innerHTML + ' ' + students[i];
    }
};
// when the students-reverse button is clicked
document.getElementById('js-students-reverse').onclick = function(){
    // store the output div
    var studentOutput = document.getElementById('js-student-output');
    // empty the output div
    studentOutput.innerHTML = '';
    // sort the students array
    students.sort().reverse();
    // for each student in the students array
    for(var i = 0; i < students.length; i++){
        // add them to a div of id js-student-output w/o erasing previous
        studentOutput.innerHTML = studentOutput.innerHTML + ' ' + students[i];
    }
};
```




## Creating an Accordion: 15 Minutes

```
/*------------------------------------*\
    ::Basic Accordion
\*------------------------------------*/
// when the page is ready
$(document).ready(function($){
    // find all the toggles
    $('.js-expand-toggle')
        // when the toggle is clicked
        .on('click', function(){
            // look for the sub containers to expand
            $(this)
                .find('.js-expand-sub')
                // toggle it up or down
                .slideToggle();
    });
});
```




## Refining the Accordion: 10 Minutes

```
/*------------------------------------*\
    ::Extra Credit Accordion
\*------------------------------------*/
// when the page is ready
$(document).ready(function($){
    // find all the expandable groups
    $('.js-expand')
        // for each of the expandable groups
        .each(function(){
            // cache this particular expandable group
            var theParent = $(this);
            // within this group
            theParent
                // find all the toggles
                .find('.js-expand-toggle')
                    // when one of the toggles is clicked
                    .on('click', function(){
                        // find all the sub containers this parent has
                        theParent
                            .find('.js-expand-sub')
                                // slide them all up
                                .slideUp();

                        // find the sub containers for just this toggle
                        $(this)
                            .find('.js-expand-sub')
                                // toggle it up or down
                                .slideToggle();
                    });
    });
});
```




## Incorporating Code: 10 Minute Individual activity

```
/*------------------------------------*\
    ::Demo Hamburger
\*------------------------------------*/
jQuery(function($){
    $('.main-nav__menu').slideUp();
    $('.hamburger-menu').on('click', function() {
        $(this).next().slideToggle();
        $(this).toggleClass('animate')
        $('.bar').toggleClass('animate');
    });
});
```

```
<div class="hamburger-menu">
      <div class="bar"></div>
</div>
```

```
/*------------------------------------*\
    ::Hamburger
\*------------------------------------*/
.hamburger-menu {
  transform: scale(.5);
  position: absolute;
  top: 30px;
  right: 0;
  bottom: 0;
  margin: auto;
  width: 80px;
  height: 60px;
  cursor: pointer;
  transition: all 600ms cubic-bezier(0.23, 1, 0.32, 1);
}
.hamburger-menu.animate {
  transform: rotate(180deg);
}

.bar,
.bar:after,
.bar:before {
  width: 80px;
  height: 10px;
}

.bar {
  position: relative;
  transform: translateY(25px) scale(.5);
  background: tomato;
}

.bar:before {
  content: "";
  position: absolute;
  right: 0;
  bottom: 25px;
  background: tomato;
  transition: all 600ms cubic-bezier(0.23, 1, 0.32, 1);
}

.bar:after {
  content: "";
  position: absolute;
  right: 0;
  top: 25px;
  background: tomato;
  transition: all 600ms cubic-bezier(0.23, 1, 0.32, 1);
}

.bar.animate:after {
  width: 50px;
  transform: rotate(-45deg) translateX(15px);
}

.bar.animate:before {
  width: 50px;
  transform: rotate(45deg) translateX(15px);
}
```




## Adding the Flexslider Plugin: 15 minute Group Activity

```
<link rel="stylesheet" href="plugins/flexslider/flexslider.css" />
<script src="plugins/flexslider/jquery.flexslider-min.js"></script>
```

```
<div class="flexslider">
    <ul class="slides">
        <li>
            <img src="https://source.unsplash.com/category/nature/600x300" alt="Uplash Image" />
        </li>
        <li>
            <img src="https://source.unsplash.com/category/nature/600x301" alt="Uplash Image" />
        </li>
        <li>
            <img src="https://source.unsplash.com/category/nature/600x302" alt="Uplash Image" />
        </li>
    </ul>
</div>
```

```
/*------------------------------------*\
    ::Slider
\*------------------------------------*/
$(window).load(function() {
    $('.flexslider').flexslider();
});
```

```
{
    slideshow: true,
    slideshowSpeed: 2000,
    end: function(){
        // alert('the end is near');
    }
}
```




## Adding a Sticky Nav: 5 minute individual Activity
`<script src="/plugins/stickup/stickup.min.js"></script>`

```
/*------------------------------------*\
    ::Sticky Nav
\*------------------------------------*/
jQuery(function($){
    $('.main-nav').stickup();
});
```