# How to make a tooltip

## Aria label
* Pass a 'aria-label' parameter to anchor tag or anywhere you want to add tooltip then in css add this code
```
[aria-label] {
position: relative;
}

[aria-label]::before{
  content: "";
  display: none;
  position: absolute;
  top: 100%;
  left: 50%;
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-bottom: 5px solid black;
}

[aria-label]::after {
content: attr(aria-label);
display: none;
position: absolute;
top: 110%;
left: 10px;
z-index: 5000;
pointer-events: none;
padding: 5px 10px;
line-height: 10px;
white-space: nowrap;
text-decoration: none;
text-indent: 0;
overflow: visible;
font-size: .9em;
font-weight: normal;
color: #fff;
text-shadow: 1px 0 1px #888;
background-color: #412917;
-webkit-border-radius: 2px;
border-radius: 2px;
-webkit-box-shadow: 1px 2px 6px rgba(0,0,0,0.3);
box-shadow: 1px 2px 6px rgba(0,0,0,0.3);
}

[aria-label]:hover:before, [aria-label]:hover:after, [aria-label]:focus:after {
display: block;
}
```

## custom tooltip
* Pass a 'data-tooltip' parameter to anchor tag or anywhere you want to add tooltip then in css add this code
```
[data-tooltip] {
  position: relative;
  z-index: 2;
  cursor: pointer;
}

/* Hide the tooltip content by default */
[data-tooltip]:before,
[data-tooltip]:after {
  visibility: hidden;
  -ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity=0)";
  filter: progid:DXImageTransform.Microsoft.Alpha(Opacity=0);
  opacity: 0;
  pointer-events: none;
}

/* Position tooltip above the element */
[data-tooltip]:before {
  position: absolute;
  bottom: 100%;
  left: 50%;
  margin-bottom: 5px;
  margin-left: -80px;
  padding: 7px;
  width: 160px;
  -webkit-border-radius: 3px;
  -moz-border-radius: 3px;
  border-radius: 3px;
  background-color: #000;
  background-color: hsla(0, 0%, 20%, 0.9);
  color: #fff;
  content: attr(data-tooltip);
  text-align: center;
  font-size: 14px;
  line-height: 1.2;
}

/* Triangle hack to make tooltip look like a speech bubble */
[data-tooltip]:after {
  position: absolute;
  bottom: 100%;
  left: 50%;
  margin-left: -5px;
  width: 0;
  border-top: 5px solid #000;
  border-top: 5px solid hsla(0, 0%, 20%, 0.9);
  border-right: 5px solid transparent;
  border-left: 5px solid transparent;
  content: " ";
  font-size: 0;
  line-height: 0;
}

/* Show tooltip content on hover */
[data-tooltip]:hover:before,
[data-tooltip]:hover:after {
  visibility: visible;
  -ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity=100)";
  filter: progid:DXImageTransform.Microsoft.Alpha(Opacity=100);
  opacity: 1;
}
```