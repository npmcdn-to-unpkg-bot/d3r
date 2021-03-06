
<!-- README.md is generated from README.Rmd. Please edit that file -->
[![CRAN\_Status\_Badge](http://www.r-pkg.org/badges/version/d3r)](https://cran.r-project.org/package=d3r) [![Travis-CI Build Status](https://travis-ci.org/timelyportfolio/d3r.svg?branch=master)](https://travis-ci.org/timelyportfolio/d3r)

### Why d3r?

I tried to explain the purpose of `d3r` in this Building Widgets blog post [Why d3r?](http://www.buildingwidgets.com/blog/2016/8/28/why-d3r).

### Installing d3r

`d3r` is not on CRAN, so install with `devtools`.

    devtools::install_github("timelyportfolio/d3r")

### d3 Dependency Functions

`d3r` makes `d3.js` dependency injection in R easy with two functions `d3_dep_v3()` and `d3_dep_v4()`. These functions work well with `htmltools::tags`.

    library(htmltools)
    library(d3r)

    # check web developer tools to see d3 is available
    browsable(
      attachDependencies(
        tagList(),
        d3_dep_v4()
      )
    )

Also, I will commit to keeping `d3r` up-to-date with `d3.js`, so you'll no longer need multiple copies of `d3.js` for your `htmlwidgets`. If you are a `htmlwidget` author, you will no longer need to worry every time `d3.js` gets a new release. See `treebar` [lines](https://github.com/timelyportfolio/treebar/blob/master/R/treebar.R#L66-L74) for an example of using `d3r` with your `htmlwidget`.

### d3 Hierarchy from data.frame

Building `d3.js` hierarchies can be very difficult. `d3r::d3_nest()` will convert `table` and `data.frame` to a nested `d3.js` hierarchy ready for work with the [`d3-hierarchy`](https://github.com/d3/d3-hierarchy).

    d3_nest(as.data.frame(Titanic))

As another example, let's go from `treemap` to `d3.js`.

    library(treemap)
    library(d3r)

    d3_nest(
      treemap::random.hierarchical.data(),
      value_cols = "x"
    )

### d3 Network from igraph

`igraph` to `d3.js` network of `nodes` and `links` is a very common conversion. `d3r::d3_igraph` will do this for you.

    library(igraph)
    libary(d3r)

    d3_igraph(igraph::watts.strogatz.game(1, 50, 4, 0.05))

### Todo

I have a whole lot of ideas. Please let me know yours, and let's make this package great.

### Code of Conduct

Please note that this project is released with a [Contributor Code of Conduct](CONDUCT.md). By participating in this project you agree to abide by its terms.
