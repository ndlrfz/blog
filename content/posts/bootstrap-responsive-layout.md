+++
date = '2025-05-09T12:30:40+07:00'
draft = false
title = 'Boostrap Grid, Breakpoints, Gutters, and Spacing'
tags = ["bootstrap5", "webdev"]
showTags = true
toc = true

+++

Grid is a system for building fully responsive layout in Bootstrap.

You can create layout with **Grid** via the following classes:

1. `container` or `container-fluid` (width 100%).
2. `row` as row inside the `container`.
3. `cols` as column inside the `row`.

Example:

```html
<div class="container">
   <div class="row">
      <div class="col">
         <div>
            Col 1
         </div>
      </div>
      <div class="col">
         <div>
            Col 2
         </div>
      </div>
   </div>
</div>
```

## 6 Grid System for Responsive Layout

There are 6 grid system in Bootstrap:

1. Extra small with class `col-*` with the _width_ auto or **<576**.
2. Small with class `col-sm-*` with the _width_ **576px to 767px**.
3. Medium with class `col-md-*` with the _width_ **768px to 991px**.
4. Large with class `col-lg-*` with the _width_ **992px to 1200px**.
5. Extra large with class `col-xl-*` with the _width_ **1200px to 1400px**.
6. Extra extra large with class `col-xxl-*` with the _width_ **>=1400px**.

> Keep in mind that the `*` in column represent number between **1 to 12**. And **12** is max of column number that you can have.

So..

### How to create two columns with the same width?

**Answer**: Create _two_ columns with the class `col-6` (**6 + 6 = 12**).

```html
      <div class="col-6">
         <div>
            Col 1
         </div>
      </div>
      <div class="col-6">
         <div>
            Col 2
         </div>
      </div>
```

### How to create two columns with the different width?

**Answer**: Create _two_ columns with the `col-8` and `col-4` (**8 + 4 = 12**).

```html
      <div class="col-8">
         <div>
            Col 1
         </div>
      </div>
      <div class="col-4">
         <div>
            Col 2
         </div>
      </div>
```

> Keep in mind that you can create columns max **12** or **sum** of `col-*` classes up to **12**.

## Breakpoint

>Breakpoint is the controller for reponsive design in Bootstrap.
It determine **when** container adapt to the device viewport or width.

As you know there are **6 Grid System**. So when container reached the _breakpoint_ of the _grid_, the container will adapt and columns will change.

### How Breakpoint and Grid works?

* Breakpoint works to the top.

When you define a single grid column such as `col-md-4`:

1. The size will become **bigger** on _Large, Extra Large, and Extra Extra Large_.
2. Columns will be stacked when viewport reached the breakpoint of _Small_ and _Extra Small_ viewport.

_Example_:

```html
      <div class="row">
        <div class="col-md-4 bg-primary text-white">Column A</div>
        <div class="col-md-4 bg-info text-white">Column B</div>
        <div class="col-md-4 bg-success text-white">Column C</div>
      </div>
```

Explanation from the above script:

* Each column will become **bigger** on _Large, Extra Large, and Extra Extra Large_ viewport.
  * On screen `>=768`, columns bigger.
* Each column will be **stacked** on _Small and Extra Small_ viewport.
  * On screen `<=767`, columns will be stacked.

## How to arrange columns on different viewport?

**Answer**: Use multiple grid system on your class.

_Example_:

```html
      <div class="row">
        <div class="col-lg-6 col-md-4 col-sm-12 bg-primary text-white">Column A</div>
        <div class="col-lg-3 col-md-4 col-sm-6 bg-info text-white">Column B</div>
        <div class="col-lg-3 col-md-4 col-sm 6 bg-success text-white">Column C</div>
      </div>
```

Explanation of the script above:

* On _lg, xl, and xxl_ _Column A_ will be bigger `col-lg-6` than _Column B_ and _C_ `col-lg-3`.
* On _md_ viewport, all columns will have the same size `col-md-4`.
* On _sm_ viewport, _Column A_ will be full width `col-sm-12`, then _Column B_ and _C_ at the bottom with the same size `col-sm-6`.
* On _xs_ viewport, all columns will be stacked.

## What is Gutters?

Gutters is padding and provides spacing between your columns.

There are two gutters in Bootstrap:

1. **Horizontal** for spacing _left and right_ `gx-*`.
2. **Vertical** for spacing _top and bottom_ `gy-*`.

> The value `*` for Gutters is between **1-5**. You can use `g-*` to set up Gutters for both _Horizontal and Vertical_.

## Spacing in Bootstrap

It is **Padding** and **Margin** on Bootstrap.

Here the classes:

* `p-*` for padding
* `m-*` for margin

How about _top, bottom, left, and right_? Sure:

* `t` for top
* `b` for bottom
* `s` or start
  * **LTR**: margin left or padding left
  * **RTL**: margin right or padding right
* `e` or end
  * **LTR**: margin right or padding right
  * **RTL**: margin left or padding left
* `x` for horizontal _left and right_
* `y` for vertical _top and bottom_

Now you can use something like this:

* `pt-3` means _Padding top is set to 3_.
* `pt-md-2` means _Padding top will become 2 on **md** viewport_.

> Keep in your mind that the `*` is value between **0-5** or _auto_.

## How to create Responsive Layout without Overflow?

Most people struggle for this with bootstrap (_because so many questions about this on Stackoverflow and others_), espcially when combining with gutters and spacing.

**Answer**: Here the step-by-step:

1. Create `container` or `container-fluid` and expand the horizontal padding `px-2` or `px-0` to get full width.
2. On your `row` class, add the gutters `g-2` for spacing between columns.
3. Wrap your the column content with new `div`.
4. _Optional_, add `py-2` for padding top and bottom on your content `div`.

_Example_:

```html
    <div class="container-fluid px-0 text-center text-white">
      <div class="row g-2">
        <div class="col-lg-6 col-md-4 col-sm-12">
          <div class="bg-primary py-2">Column A</div>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6">
          <div class="bg-info py-2">Column B</div>
        </div>
        <div class="col-lg-3 col-md-4 col-sm-6">
          <div class="bg-success py-2">Column C</div>
        </div>
      </div>
    </div>
```

> I believe this is the most important concept in Bootstrap for creating responsive layout. You can implement this tips on every `containers`.

bye.
