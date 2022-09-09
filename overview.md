# Shiny Presentation slides

## Layout:


### 1. Introduction

- What is R Markdown, why use it over other tools?

# What is RMarkdown?

- R Markdown is an interactive document that can be used to create efficient reports to summarize analyses and communicate results to an audience. 

--
- It interweaves narrative and prose with code, its outputs, and graphics to create technical documents, that are easily shared, presented, or reproduced. 

--
- We can create HTML, PDF, Word documents with R Markdown using only R code, as well as presentations of various types.

--
- This presentation is an rmd! 

--
- R Markdown shines in its one-click compiling, or "knitting", making it easy to set up a template document that can accept different parameters.

### 2. Code chunks and language integration

---
# How is RMarkdown Different?

--
- For writers, rmd is often compared to LateX

--
- Easier to write and format based on plain text and markdown.

--
- Very flexible as a 'kitchen knife'

--
- Can include custom LateX packages in your rmd

---
# How is RMarkdown Different?

- For programmers, rmd is often compared to Jupyter Notebook

--
- JSON based

--
- Acts better as a logbook, or work file, rather than an interactive report

--
- rmd allows for in-line HTML, css reference files, custom javascript

---

# Output Code Results

```{r comment='#'}
# a simple regression
fit = lm(dist ~ 1 + speed, data = cars)
coef(summary(fit))
```
--
- Code chunks with the output included in the document

--
- rmd has language support for all* programming languages

- Rmd documents combine markdown 
- Language support, and how code chunks are run inside of the document, either to echo on foreground or run silently in the background
- Markdown support (maybe show cheat sheet), emoji support
- HTML in-line (showcase toggle - see below)
- Show the hover-over for code chunk
- Also show how SQL looks in the code, and saving it to a var (using out.var ="")
- This can give an idea of a pipeline of work that can be done

### 3. YAML

- Go into the metadata and the options that are provided in YAML
- Also the output types - Word, pdf, HTML, presentations

### 4. LateX and easy integration of formulas and structures

- Historically it has been cumbersome creating a document with complex mathematical equations and formula. RMarkdown allows for simple in-line LateX code
- This also includes non-Latin scripts, such as Arabic and Sanskrit


### 5. Interactive code chunks

- Cases when every time the rmd runs, it will update the output.
- This is because the data file is read every time the rmd is compiled
- example is a growing data file that gains more observations over a period of time

### 6. Reports and reproducibility

- Reiterate the importance of reproducibility alongside dynamic documents
- Paramaterized reports
- shiny to rmarkdown

### 7. Dashboarding and Shiny

- https://bookdown.org/yihui/rmarkdown/parameterized-reports.html

### 8. Bookdown 

- https://bookdown.org/yihui/rmarkdown/books.html

### 9. CSS showcase

<details>
  <summary style="font-size:=14px"> Toggle example using in-line HTML </summary>
  <hr>
  - Point
  
  1. One
  2. Two
     * A
     * B
     
</details>

### footnote notation:
```
.footnote[
[1] 中文用户请看[这份教程](https://slides.yihui.org/xaringan/zh-CN.html)

[2] See [#2](https://github.com/yihui/xaringan/issues/2) if you do not see the template or addin in RStudio.
]
```

### to animate slides:

```
class: animated slideInRight fadeOutLeft
```
