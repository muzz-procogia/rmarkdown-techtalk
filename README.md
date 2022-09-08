# rmarkdown-techtalk
September 8, 2022 | ProCogia Weekly Tech Talk


## text for presentation

R Markdown is a tool we use to create efficient reports to summarize analyses and communicate results to an audience. We can create HTML and PDF documents with R Markdown using only R code. R Markdown is also a way to ensure that the results are reproducible, which is important to guarantee when creating reports.

Reproducible results
Consider the following scenario: you've conducted your analyses and created a presentation to demonstrate the findings.
You give the presentation to stakeholders, and they request some modifications.
However, you can't remember each step you went through
and aren't able to reproduce your work! By generating the results and report from code with R Markdown, you, and others, can always reproduce your results.

An R Markdown document is made of three components: the code, the text of the report, and the metadata for the file.
The YAML header containing the metadata appears at the top of the file, followed by the contents that make up the report, including the text and code in code chunks. YAML is a syntax for hierarchical data structures that is commonly used for configuration files.

When we finish modifying a file and are ready to see the report, we'll need to knit it. Knitting a file is how we generate an output file from the R markdown file. When a file is knit, R Markdown runs the chunks of R code contained in the file and combines them with the text in the document into an HTML file. For example, when the R Markdown file shown on the left is knit, it will create the output shown on the right. We'll learn more about output types later in the chapter.

To get started, we'll add some code by adding a code chunk. A code chunk is a section that contains the code that will either render output in the report or display the code itself as part of the report. Chunks are what separate the text of the report from the code.
Code chunks start and end
with a set of three backticks. The first set of backticks signify the beginning of the code chunk
and are followed by curly braces that include the letter r, to specify that we are adding r code. Within the curly braces, we can specify a number of other chunk options. We'll be discussing the details of this later in the course.
