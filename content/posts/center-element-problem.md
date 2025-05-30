+++
date = '2025-05-31T06:27:45+07:00'
draft = false
title = 'How to Center Element Problem in Web Design'
tags = ['webdev']
+++

> How to center my div/element? Why I can't center my div/element?

The classic webdev question for everyone. I always struggle with this.

How to solve this?

**The Answer**: Restructure your HTML elements.

Let's take a look.

This is the common HTML structure that I always use:

```html
...
<body>

    <header>
    </header>

    <main>
    </main>

    <footer>
    </footer>

</body>
```

I will creater header element like this:

```html
<!-- root element -->
<header class="w-full mt-5">
    <!-- div to create container -->
    <div class="container mx-auto">
        <!-- nav with flex -->
        <nav class="flex flex-row items-center justify-between">
            <!-- logo -->
            <div>
                <img src="" alt="Logo">
            </div>
            <!-- menu -->
            <!-- div and span to create hamburger icon menu -->
            <div>
                <span></span>
                <span></span>
                <span></span>
            </div>
            <ul>
                <li><a href-"#">Menu</a></li>
            </ul>
        </nav>
    </div>
</header>
```

For the main content:

```html
<main>
    <!-- section -->
    <section>
        <!-- div for container -->
        <div class="container mx-auto">
            <!-- div for flex -->
            <div class="flex flex-row">
                <!-- div for content -->
                <div>
                    <h3>Content</h3>
                </div>
                <!-- another div for content -->
                <div>
                    <h3>Content</h3>
                </div>
            </div>
        </div>
    </section>
</main>
```

Did you see the pattern?

This way, I can set up `padding` and `margin` for each `container` box to make sure every elements inside is alignment with each other. So no more question about _how to center my element?_.
