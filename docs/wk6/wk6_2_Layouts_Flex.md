# 

*This lesson was based on the page **[Flexbox](https://internetingishard.com/html-and-css/flexbox/#grouping-flex-items)** by Interneting is Hard.*

# Page Layout with Flexbox



Once you've learned to control the position of flex-items, creating non-linear page layouts becomes much easier and intuitive.



## Grouping Flex Items

Flexbox opens a new strategy for creating more interesting layouts: **grouping elements inside multiple flex containers**.



> Separate sibling flex items by grouping them into one or more flex containers.
>
> 
>
> When necessary, enable vertical configurations by changing the flex direction a wrapping container to column instead of row.



<br>

![Diagram: wrapping two flex items in a <div> to eliminate one of the flex items](https://internetingishard.com/html-and-css/flexbox/grouping-flex-items-1bb642.png ':size=500')

<p align="center"><strong>Grouping Flex Items </strong><a href="https://internetingishard.com/html-and-css/flexbox/"><em>Interneting is Hard</em></a></p>

<br>

### Example 1:  Three equal columns

Consider the starting code below:

<iframe height="500" style="width: 100%;" scrolling="no" title="Wk6_3_equal_cols" src="https://codepen.io/maujac/embed/wvaJYoO?height=265&theme-id=dark&default-tab=html,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/wvaJYoO'>Wk6_3_equal_cols</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>



<br>

**Notice the following:**

- The elements to be converted into columns are inside the **wrapper container** tagged with the class ***.call-outs-container***.
- The wrapper container is a sibling of the `<h2>` element.
- All elements are initially block level.



**Do the following:**

1. Convert ***.call-outs-container*** to a flex container by adding `display: flex;` to it's styling.
2. Notice how the size of the flex items depends on their content (the flex default behaviour).
3. Make each flex item grow to take equal parts of the flex container:
   - In the **styling for flex item** add `flex: 1;`
   - This will cause each item to take 1 equal part (from the total of 3 distributed parts)



### Example 2: Main and side columns

Consider the starting code below:

<p class="codepen" data-height="500" data-theme-id="dark" data-default-tab="html,result" data-user="maujac" data-slug-hash="bGdqmeZ" style="height: 500px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Wk6 - main_side_cols">
  <span>See the Pen <a href="https://codepen.io/maujac/pen/bGdqmeZ">
  Wk6 - main_side_cols</a> by Mauricio Buschinelli (<a href="https://codepen.io/maujac">@maujac</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

<br>

**Notice the following:**

- All elements are inside the `<section>` **wrapper container**.
- All elements are initially block level and include the class of *.col-margin*.



**Do the following:**

1. Convert `<section>`  to a flex container by adding `display: flex;` to it's styling.
2. Since the div tagged ***.main-column*** has much more content then the other elements it is assigned more space (the flex default behaviour).
   - This makes sense, however, we did not control the spacing. 
3. Make the main section 3 times as large as the sidebar :
   - In the **styling for *.main-column*** add `flex: 3;`
   - In the **styling for *.sidebar-one/two*** add `flex: 1;`
   - The `flex:` assignment is proportional to the total distribution of parts (a total of 5 parts in this case).

<br>

![flex_proportions](assets/flex_proportions.png)



<br>

### Example 3: Navbar

In this example we will create a navigation bar where:

- The date leans to the left side of the navbar;
- "Sign Up" and "Login" lean on the right side of the navbar

![image-20200226211708651](assets/image-20200226211708651.png ':size=500')



<br>

Consider the starting code below.

*Note: the white borders are being used purely for debugging purposes. We will remove them at the end.*

<br>

<iframe height="400" style="width: 100%;" scrolling="no" title="Wk6 - navbar_flex" src="https://codepen.io/maujac/embed/zYGZbqR?height=265&theme-id=dark&default-tab=html,result" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/maujac/pen/zYGZbqR'>Wk6 - navbar_flex</a> by Mauricio Buschinelli
  (<a href='https://codepen.io/maujac'>@maujac</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>



<br>

**Notice the following:**

- The `<nav>` element with class ***.menu-container*** only has one child, the `<div>` of class ***.menu***.



**Do the following:**

1. Convert ***.menu-container*** into a flex container with `display: flex;`

   - Since `<nav>` only has one child nothing will change.

2. Add the flex property `justify-content: center;`  to the ***.menu-container*** element in order to center its single flex item.

   > This has the same effect as adding a `margin: 0 auto` declaration to the `.menu` element.
   >
   > Notice how we did this by adding a property to the *parent* element (the flex container) instead of directly to the element we wanted to center (the flex item).

   

3. Convert ***.menu*** into a flex container by adding `display: flex;`

4. Distribute the children of *.menu* in order to maximise the space between them by adding `justify-content: space-between;`

   

   ![image-20200226215018429](assets/image-20200226215018429.png)

   <br>

5. In the HTML wrap the "Sign Up" and the "Login" elements by creating a new `<div>` with the class of ***.links***

   - The flex behaviour `space-between`  should push the newly created container (the `<div>` with *.links*) away from it's sibling, the `<div>` with *.date*

     <br>

     ![Web page showing two menu bar <li> items wrapped in a container <div>](https://internetingishard.com/html-and-css/flexbox/menu-bar-grouped-items-1-31c157.png)

   <br>

6. Turn the ***.links*** element into a flex container so that its siblings lie side-by-side

   - At the same time, add a solid white border to *.links* in order to see how the layout is happening

7. Send the flex items of *.links* to the right side by using `justify-content: flex-end;`

8. Add a small spacing between "Sign Up" and "Login" by creating a new CSS rule:

   <br>

   ```css
   .login { margin-left: 20px; }
   ```



<br>

![Web page <li> elements laid out with nested flexbox containers](https://internetingishard.com/html-and-css/flexbox/menu-bar-grouped-items-2-50cec0.png)



<br>




