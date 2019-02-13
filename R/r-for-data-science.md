# Notes - R for Data Science

> Notes from reading online free book, called *R for Data Science*
> written by Garrett Grolemund and Hadley Wickham,
> Available at https://r4ds.had.co.nz/introduction.html

## 1-2 Introduction

### Workflow, Other Vocabulary
- Import data to R
- Make data tidy
    - each column is a variable
    - each row is an observation
- Transform the data: narrow in on observations of interest
- Wrangling: refers to the process of making data tidy and transform it
- Visualisation: graphs
- Models: Making predictions
- Communicaiton
- Programming

### Tools
- CRAN: Comprehensive R Archive Network
- RStudio: IDE for R
- Package: tidyverse
    - `install.packages("tidyverse")` to install
    - `library(tidyverse)` to include it
    - `tidyverse_undate()` to update packages
- Other packages
    - `nycflights13`: airline flights
    - `gapminder`: world development
    - `Lahman`: baseball


## 3 Data Visualisation

- Will use `ggplot2`
- Example data: `ggplot2::mpg`
    - `displ`: car's engine size, in litres
    - `hwy`: fuel efficiency on highway, in miles per gallon (mpg)
    - Run `?mpg` for more

- Graph Example: `hwy vs displ`
    ```r
    ggplot(data = mpg) +
        geom_point(mapping = aes(x = displ, y = hwy))
    ```

- Graphing Template
    ```r
    ggplot(data = <DATA>) +
        <GEOM_FUNCTION>(mapping = aes(<MAPPINGS>))
    ```

### "Level" of Aesthetics (color, size, shape, etc)
- Can use a text value for level (such as color)
- `aes(x=.., y=.., color=class)`
- `color` `size` `shape` `alpha`
- When use shape aesthetics, maximum 6 shapes can be plotted
- Also think x and y as aesthetics, it does not create legends
for these, but axis lines and tick marks act as legends

###  Mannually Set Aesthetic Properties
- Put them outside of mapping part `geom_*()`, for example
    ```r
    ggplot(data = mpg) +
        geom_point(mapping = aes(x=displ, y=hwy), color = "blue")
    ```
- Need to choose a meanful value:
    - color: string
    - size: in mm
    - shape: a number, see corresponding table

### Facets
- For categorical variables, besides using colors, facet is another option
- `facet_wrap()` for single variable
- `facet_grid()` for two variables
    ```r
    ggplot(data = mpg) +
        geom_point(mapping = aes(x = displ, y = hwy)) +
        facet_wrap(~ class, nrow = 2)

    ggplot(data = mpg) +
        geom_point(mapping = aes(x = displ, y = hwy)) +
        facet_grid(drv ~ cyl)
    ```
- `~` is a "formula"
    - Can contain one variable: `~ class`
    - Can contain two variables: `drv ~ cyl`
    - Can omit a variable using a dot: `. ~ cyl`

### Geometric Objects, Geom Overlays
- Functions like `geom_smooth`, who takes display multiple rows of data, will treat any discrete variables as groups and draw them as a seperate objects
- Can also manually pass a `group=` argument
- When we have multiple geoms, we don't want to have any duplicated code, therefore, we can put mapping into the ggplot function instead of every geom function
- This creates a global mapping, and any further local mapping can still be made inside desired functions
- Also, `data` can be specified differently for each layer too. Maybe by using `filter()` function

### Statistical Transformations
- Example Data: `ggplot2::diamonds`
- Some plots calculate new values to plot:
    - bar charts, histograms, and frequency polygons bin your data and then plot bin counts, the number of points that fall in each bin.
    - smoothers fit a model to your data and then plot predictions from the model.
    - boxplots compute a robust summary of the distribution and then display a specially formatted box.
- The algorithm used to calculate new values for a graph is called a stat, short for statistical transformation
- every geom has a default stat and every stat has a default geom
- Use `stat="identity"` when already have the height for bars in `geom_bar`
- Use `stat_summary()` to see more statistics for each x values
    ```r
    ggplot(data = diamonds) +
        stat_summary(
                mapping = aes(x = cut, y = depth),
                fun.ymin = min,
                fun.ymax = max,
                fun.y = median
                )
    ```

REMARK: Stopped at section 3.8
