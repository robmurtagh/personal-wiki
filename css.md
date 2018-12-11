# CSS

## box-sizing

It's useful to be aware of [box-sizing](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing) which governs how borders are included in `div` size calculations.

## Pseudo elements

- [Pseudo elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements) are worth remembering, they let you style an element based on some property of that element (e.g. `::first-line`), or add elements to the DOM in a suitable position (e.g. `::before`, `::after`).
- Proper syntax is `::selector`, however `:selector` seems to be more universally supported

## Tachyons

[Tachyons](http://tachyons.io) is an excellent 'functional CSS' library in which each class name has one responsibility. For example the Tachyons class `.ba` stands for `border-style:solid;border-width:1px`, there would not be a Tachyons class called e.g. `.button-active` as that would encompass many different - design specific - CSS functions.

### Tachyons Media Queries

Tachyons classes have suffixes:

- `[no-suffix]` = applies for all screensizes, and hence is the 'mobile' version
- `-ns` = not-small (min-width: 30em)
- `-m` = medium (min-width: 30em) and (max-width: 60em)
- `-l` = large (min-width: 60em)

## Diagonal block colour background

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <title>Diagonal Background</title>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <style>
      #elem-container {
        height: 100%;
      }
      #elem {
        position: relative;
      }
      #elem:before {
        content: ""; /* an empty div */
        height: 120%; /* with a height settable against parent container */
        width: 135%; /* wider than the page so you can't see the edges */
        position: absolute; /* outside of the document flow */
        z-index: -1; /* and behind the #elem */
        display: block;
        background-color: lightblue; /* and behind the #elem */
        transform: rotate(12deg);
        left: -15%; /* with offsets as required */
        top: -15%;
      }
    </style>
  </head>
  <body>
    <div id="elem-container">
      <div id="elem">
        <p>
          Lorem ipsum dolor sit amet, at per iudicabit periculis, an officiis
          salutandi vel. Sit an meis adhuc.
        </p>
        <p>
          Lorem ipsum dolor sit amet, at per iudicabit periculis, an officiis
          salutandi vel. Sit an meis adhuc.
        </p>
        <p>
          Lorem ipsum dolor sit amet, at per iudicabit periculis, an officiis
          salutandi vel. Sit an meis adhuc.
        </p>
        <p>
          Lorem ipsum dolor sit amet, at per iudicabit periculis, an officiis
          salutandi vel. Sit an meis adhuc.
        </p>
      </div>
    </div>
  </body>
</html>
```

## Diagonal background with before and after

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <title>Page title</title>
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <style>
      #elem-container {
        height: 100%;
      }
      #elem {
        position: relative;
      }
      #elem:before {
        content: ""; /* an empty div */
        height: 100%; /* with a height settable against parent container */
        width: 135%; /* wider than the page so you can't see the edges */
        position: absolute; /* outside of the document flow */
        z-index: -1; /* and behind the #elem */
        display: block;
        background-color: lightblue; /* and behind the #elem */
        transform: rotate(12deg);
        left: -15%; /* with offsets as required */
        top: -35%;
      }
      #elem:after {
        content: "";
        height: 120%;
        width: 135%;
        position: absolute;
        z-index: -2;
        display: block;
        background-color: darkblue;
        transform: rotate(-12deg);
        left: -15%;
        top: -5%;
      }
    </style>
  </head>
  <body>
    <div id="elem-container">
      <div id="elem">
        <p>
          Lorem ipsum dolor sit amet, at per iudicabit periculis, an officiis
          salutandi vel. Sit an meis adhuc.
        </p>
        <p>
          Lorem ipsum dolor sit amet, at per iudicabit periculis, an officiis
          salutandi vel. Sit an meis adhuc.
        </p>
        <p>
          Lorem ipsum dolor sit amet, at per iudicabit periculis, an officiis
          salutandi vel. Sit an meis adhuc.
        </p>
        <p>
          Lorem ipsum dolor sit amet, at per iudicabit periculis, an officiis
          salutandi vel. Sit an meis adhuc.
        </p>
        <p>
          Lorem ipsum dolor sit amet, at per iudicabit periculis, an officiis
          salutandi vel. Sit an meis adhuc.
        </p>
        <p>
          Lorem ipsum dolor sit amet, at per iudicabit periculis, an officiis
          salutandi vel. Sit an meis adhuc.
        </p>
        <p>
          Lorem ipsum dolor sit amet, at per iudicabit periculis, an officiis
          salutandi vel. Sit an meis adhuc.
        </p>
        <p>
          Lorem ipsum dolor sit amet, at per iudicabit periculis, an officiis
          salutandi vel. Sit an meis adhuc.
        </p>
      </div>
    </div>
  </body>
</html>
```
