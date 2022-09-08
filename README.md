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

## Headers
Including headers in the report will help clearly label each section. We add headers using a hash and a single space before the text. The more hashes we use, the smaller the header will be.

## Adding headers
Here we use two hashes for the section called Datasets, and three to label each dataset, Investment Annual Summary and Investment Services Projects. Remember to place the hash at the start of the line and add a single space after the hash before the text. If you include a space or another character before the hash, the header won't render. Notice that the size of each header in the knit file is determined by the number of hashes before the text.

if we want to include text within the code, we add a single hash before the text. This renders the text as a code comment within the code chunk. We'll discuss how and when to include code in the report later in the course.

There are many options for formatting text in a markdown file, including making the text bold, italicized, or strikethrough. To bold the text, we surround it with two sets of asterisks or underscores. To italicize it, we use one set of asterisks or a single set of underscores, and to strikethrough text, we surround the text with two sets of tildes.

We can also add inline code to the text to clarify that we are referring to object names from the code. Let's edit the sentences about the datasets to reference the code that defines them. We add inline code by surrounding the text with a single set of backticks.

When we knit the file, the dataset names are formatted as code and the audience knows that we are referring to code within the sentence.

We can also add website links to the report. Here, we reference the data source by placing the link text in square brackets followed by the link in parentheses. Note, there are no spaces between the square brackets and the parentheses.

## YAML header
The YAML header contains the metadata of the file as key value pairs that correspond to information about the document. It appears at the top of the markdown file and starts and ends with two sets of three hyphens. When we create a new markdown document, by default, it includes the title, the author, and the output format. The title and author are provided as strings. The YAML header requires specific formatting to render, and it's important to use colons after each field, use backticks or list information as strings where required, and avoid adding any extra spaces. After modifying any of the fields in the YAML header, we'll knit the document again to see the changes reflected in the final report.

## The output type of the Markdown file is also specified in the YAML header. Throughout the course, we'll use two different output types, HTML and PDF files. We can switch between these types manually by modifying the output section of the YAML header to indicate either html_document or pdf_document.

## Adding the date manually
Another piece of information we can add to the YAML header is the date. We can enter this manually by adding the date as a string.

## Adding the date automatically
However, entering the date manually is not really scalable. Instead, we may want the date to be added automatically. To do this, add the letter r, a space, and the Sys-dot-Date() function within backticks as a string. When we knit the document, we see that today's date is added to the report with the format year-month-day.

## Formatting the date
We may want to modify the date further so that the date is formatted differently in the report. We can use the following syntax to achieve this: r format, and, in parentheses, Sys-dot-time() followed by the format we want the date to have. Here, we're including the numeric day, the full name of the Month, and the four digit year, using percent lowercase d percent capital B percent capital Y.

## Date formatting options
There are a number of options for modifying the format of the date. Some text options for the date include percent capital A or percent lowercase a for the weekday, and percent capital B or percent lowercase b for the month; the capital letter specifies the complete name, while the lowercase letter specifies the abbreviated name. Some numeric options for the date include percent lowercase d for the decimal day, percent lowercase m for the decimal month, and percent capital Y or percent lowercase y for the year. As before, the capital letter Y specifies the full four digit year, while the lowercase letter y specifies the two digit year.

1 https://www.rdocumentation.org/packages/base/topics/strptime

## Date formatting example
We can also add any commas, hyphens, or backslashes we want to include in the date. In this example, we've modified the date so it displays as month day comma year.

## Other date options
Beyond modifying the format of the date, we may want to include text that appears next to the date. To do this, we add the text within the string before the code. Here, we want to specify that the file was last edited on a certain date. We add "Last edited" before the code in the date field so the reader knows when the report was last edited.
