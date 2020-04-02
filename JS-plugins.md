# JS Plugin

## **noUiSlider**

[Plugin documentation](https://refreshless.com/nouislider/)


## **Installation**

1. `Yarn add nouislider` (be careful that students don't npm install)
2. Add js to */application.js* or on top of your *plugins/slider.js* `'import noUiSlider from 'nouislider';`
3. Add CSS to */application.scss* `@import nouislider/distribute/nouislider';`

## **Insert**
1. Add a element to the html with a precise id `<div id="slider"></div>`
2. Select the element in js and create a slider 

const slider = document.getElementById('slider');
noUiSlider.create(slider, {
    start: [20, 80],
    connect: true,
    range: {
        'min': 0,
        'max': 100
    }
});

## **Get the value on submitting the form**
1. Add 2 hidden input fields in your form
2. Listen to the change on the slider
2. Get the value on change => you get a [ "min", "max"] if it is a range
3 Set the value of the two hidden inputs 

