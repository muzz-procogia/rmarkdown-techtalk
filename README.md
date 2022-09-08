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

# Analyzing data

## 1. Analyzing the data
Now that we understand the Markdown file elements, let's analyze the data and include the analysis in the report.

## 2. Loading packages
Let's filter the investment_services_projects data to view information about the projects in a specific country. First, we load the dplyr package.

## 3. Loading packages
The packages are loaded in the first code chunk in the Markdown file, since this is the first chunk that runs when the file is knit. Listing all necessary packages at the beginning of the file also keeps it organized and ensures that we aren't listing packages that we already loaded elsewhere in the report.

## 4. Filtering for projects in Indonesia
Let's add a new code chunk with two sets of three backticks and curly braces with the letter r. Within the code chunk, we add the dataset name, a pipe, and filter for country equals equals Indonesia. We can see that there are 38 projects from the 2012 to 2018 fiscal years. Let's use assignment and the arrow operator to call this indonesia_investment_projects.

## 5. Filtering for projects in Indonesia in 2012
Let's add another code chunk and filter for the projects from a specific year, 2012. We add to the existing filter and specify the date disclosed as greater than or equal to July 1st 2011, and less than or equal to June 30th 2012, keeping in mind that the fiscal year is defined as starting on July 1st of the previous year through June 30th of the year of interest. Using assignment, we call this indonesia_investment_projects_2012. We can see that there are 6 projects from the 2012 fiscal year.

## 6. Including code results in text
We can also reference code results in the text of the report. This way, if we update the analysis and the value of the object changes, the text will update automatically to reflect the object value, and won't need to be edited manually. Let's use indonesia_investment_projects_2012 to calculate the total investment amount for projects in the 2012 fiscal year. We add a pipe and the summarize function, list the name of the new column we're creating, sum_total_investment, and pass the total_investment column to the sum function. We include na-dot-rm equals TRUE within the sum function to exclude any values that do not have a total investment amount.

## 7. Including code results in text
Below the code chunk where we create the object, we reference the object with the letter r to specify the language and the object name, in backticks. When we knit the file, we see the total investment amount, 435 million dollars, appears in the text of our report.

## 8. Multiple code chunks
At this point, we've added a few different code chunks to the file. If we run into problems when knitting the file, or receive errors about the code, it will become more difficult to spot the errors and easily edit them as we continue to add more code chunks.

## 9. Naming code chunks
To solve this issue, we can name each code chunk in the document so that the code is easier to identify. Naming each code chunk is a way of tagging the code throughout the report, which will be helpful when we are looking for a specific section we want to edit. When naming code chunks, it's best to give the code a name that provides some insight into what the code in that section achieves. The code chunk name should be included within curly braces after the letter r. In this case, we'll name the chunks indonesia-investment-projects and indonesia-investment-projects-2012 to clarify that these are the sections where we identify all projects in Indonesia, and all projects in Indonesia in the 2012 fiscal year.

# Adding Plots

## 1. Adding plots
Now let's discuss how to create visualizations of the data and include them in a report.

## 2. Loading ggplot2
We can make plots the same way we would in the console. Simply put the code in a code chunk, and the plot will render when the file is knit. First, we'll need to load the ggplot2 package in the first code chunk in the document, as we did before with dplyr.

## 3. Visualizing the annual summary
Let's use the Investment Annual Summary data to create a line plot to visualize the investment amount of dollars in millions across the different fiscal years. We call the ggplot function, and pass it the dataset name, followed by the aes function to specify the aesthetics of the plot, with x equal to the fiscal year, y equal to the dollars in millions invested, and color equals region. We then add the geom_line() function to create the line plot. Now we can see how the investment amount has varied over time across the different regions.

## 4. Adding plot labels
Let's improve the plot by adding labels. After the geom_line() function, we add a plus sign and the labs() function to add labels for the title, and x and y axes. When we knit the file, we can see the plot with the added labels.

## 5. Visualizing projects in Indonesia
Let's also create plots for the investment services projects data that we filtered previously. First we can create a plot for all projects occurring in Indonesia from the 2012 to 2018 fiscal years, and display each project and the total investment amount associated with each project as a scatterplot. We call the ggplot() function, indonesia_investment_projects, followed by the aes() function, with x equal to the date_disclosed, and y equal to the total_investment. We add the geom_point() function to create the scatterplot and include labels for the title and x and y axes. We knit the file, and see the resulting scatterplot that displays the projects and associated investment amounts.

## 6. Visualizing project status
When we take another look at the indonesia_investment_projects data, we see that it includes a status column, which identifies the project's status as either Pending Approval, on Hold, Active, or Completed. Let's add color equals status, to color each point by project status. This plot provides a lot more clarity because we're able to see the date disclosed, associated investment amount, and status of each project. Notice that the knit file includes a warning message about the data that was excluded. Let's create another plot and continue to explore the data.

## 7. Visualizing projects in Indonesia in 2012
We can add another plot using similar code and the data that was filtered for projects in Indonesia in the 2012 fiscal year. When we create this plot and knit the file, we see another warning message that one of the points was removed due to missing values. We'll discuss how to handle these warning messages in the report later in the course, but for now, let's explore why the data was removed.

## 8. Missing values
If we take a closer look at the indonesia_investment_projects_2012 data, we can see each project from the 2012 fiscal year. Notice that the LMS Toll Project is on hold and has no investment values listed, including for the total investment. Since we used the investment amounts to create the plot, and the project is on hold and has no associated investment amounts, the data was excluded from the plot. This is another example of something we may want to include in the text of the report to provide more information to the audience.

# Plot options

## 1. Plot options
Now that we've added plots to the report, let's discuss how to modify each plot and how they appear throughout the report.

## 2. Figure dimensions
Oftentimes we'll want to modify the figure dimensions. There are a number of ways to do this. The first, is using fig-dot-width and fig-dot-height to specify the width and height of the figure in inches in the final report.

## 3. Figure dimensions
For example, if we want the figure to be 5 by 3 inches, we put a comma after the code chunk name within the curly braces and include fig-dot-width equals 5 and fig-dot-height equals 3. Note that each additional option is separated by a comma.

## 4. Figure dimensions
Alternatively, instead of specifying these dimensions separately, we can use fig-dot-dim equals c 5 comma 3 in parentheses, and we'll get the same result with a single argument instead of two.

## 5. Output dimensions
We're also able to modify the dimensions of the figure using out-dot-width and out-dot-height.

## 6. Output dimensions
These arguments determine the dimensions of the output of the images in the knit document, and are specified as percentages. For example, out-dot-width equals 50 percent, will result in the figure occupying 50 percent of the width of the report once it's knit. We include the percentage in quotations. Here, we use single quotes but double quotes can also be used. Specifically using single or double quotes is important when quotes are used within quotes, for example, when we added formatting to the date field in the YAML header.

## 7. Figure alignment
We can also modify the alignment of each figure in the report using fig-dot-align. The options for this are left, right, or center, listed in quotations.

## 8. Figure alignment
Here, we've used left alignment for the figure and see that this is reflected in the knit document.

## 9. Local vs. global options
As we set the options for the figures in each code chunk, we may notice that some code chunk options are repeated throughout the report. When this happens, we may want to consider setting these options globally instead of locally. When we're specifying options locally, we add them to each code chunk and they impact only the code contained in that chunk. If we set the options globally instead, they will apply to all figures throughout the code chunks in the report.

## 10. Setting options globally
Notice the code chunk that appears when we create a new Markdown file, at the beginning of the file, in the code chunk named setup. In this chunk, the knitr package is being called with knitr and two colons. The knitr package is what runs each code chunk and knits the document. In this chunk, knitr will use the specified options as global defaults for each chunk in the document when the file is knit. Following opts_chunk dollar sign set(), we can add the options that we want to set globally to the parentheses before the echo equals TRUE argument. For example, here we add fig-dot-align equals left in quotations, and when we knit the report we see the alignment reflected in all figures throughout the document. We'll discuss the include and echo options that appear in this chunk later in the course.

## 11. Adding captions
In addition to modifying the formatting of the figure, we can also add a caption to each figure, using fig-dot-cap and including the caption in quotations. Here, we've added a caption to label the first plot as Figure 1-point-1 and to specify which fiscal years the plot displays.

# Organizing the Report

## 1. Organizing the report
Let's discuss ways to organize information in your report.

## 2. Lists and tables
You can add more information to your report using bulleted lists,

## 3. Lists and tables
numbered lists, or tables.

## 4. Bulleted lists
Items are added to a bulleted list using an asterisk, a hyphen, or a plus sign outside of any code chunks. You can structure the list formatting by adding indentation before an item on the list. Indenting a bullet will make it a sub-bullet. Notice that, in the example shown, each of the individual regions are sub-bullets of the first "Region" bullet. Let's create a list of the regions that are included in the Investment Annual Summary data. We have information on six different regions from the data and can see the bulleted list in the report when we knit the file.

## 5. Numbered lists
Alternatively, we create a numbered list by adding numbers with periods before each item on the list. When we knit the file, we can see the list has been added to the report.

## 6. Adding tables with kable()
We can add tables to the report using the kable() function from the knitr package. The knitr package is what runs each code chunk and knits the document. There are a number of options to customize the table, but it isn't possible to format the data within the table to perform tasks like combining cells. These data wrangling tasks should be done before using kable() to create the table. The indonesia_investment_projects_2012_summary provides the total investment of all projects in Indonesia in the 2012 fiscal year. Instead of printing this information as a tibble, we can call the kable() function and pass it the name of the dataset. When we knit the file, we see a table of the data.

## 7. Modifying table column names
We can modify the column names of the table using the col-dot-names argument within the kable() function. We use the c function and pass it a list of the column names we'd like to appear in the final table.

## 8. Table alignment
We can also modify the column alignment within the table, using the align argument. The default alignment for columns is right for numeric and left for all others. We see this reflected in the existing table, with total investment aligned on the right, and the project name and status aligned on the left. Let's modify this so everything is aligned to the center.

## 9. Modifying table alignment
Alignment is specified using a single letter: l for left, r for right, and c for center. Since we have three columns and we want all columns to be center aligned, we specify align equals ccc in quotations.

## 10. Adding table caption
Finally, we may want to add a caption to the table, which we can do using the caption argument and passing the caption as a string. Here, we include the caption "Table 1-point-1 The total investment summary for each project in Indonesia in the 2012 fiscal year."

# Code Chunk Options

## 1. Code chunk options
We've learned how to add, label, and modify code chunks. Now, let's discuss some code chunk options we can use to modify the knit report.

## 2. The data code chunk
Let's look at the code chunk we've seen in the exercises throughout the course, called data. The data chunk has loaded the data and packages needed for each exercise.

## 3. The data code chunk
Notice that, after the code chunk name, we see include equals FALSE inside the curly braces.

## 4. The include option
The include option determines whether or not the code and results appear in the report. When include is FALSE, the code and results do not appear in the report. When the file is knit, the code chunk runs and the results can be used throughout the file, like the data chunk in each exercise. The default argument for include is TRUE. Since include is not specified in any other code chunks in previous exercises, the code and results from those chunks have been included in the report.

## 5. The echo option
A related option is echo. When the echo option is set to FALSE, it prevents the code from appearing in the knit file, but displays the results of the code. This is an option we might use when creating plots. While we want the report to include the plot, we may not want the report to display the code that created it. Similar to include, the default for echo is also TRUE. We have also seen this in previous exercises, since the report displays both the code and the results from a code chunk by default.

## 6. The eval option
The eval option specifies whether or not we want to evaluate the code in a code chunk. If we want to exclude a code chunk from the report for the time being, we can set eval equals FALSE. When eval is FALSE, the code will not run and the results will not be included in the report. Notice that the code itself still appears in the report. This differs from other options, like include, because the code does not impact the report. Recall, with the include option, even if the code is not in the knit report, it will still be evaluated when the file is knit and impact any subsequent code chunks that reference defined objects from the code chunk. The default for eval is TRUE, since all code chunks are evaluated when the report is knit unless otherwise specified using this option.

## 7. Code option summary
Let's summarize each option we've discussed so far. The code is run in the report when either the include or the echo options are set to FALSE. Using the echo option, the results also appear in the report. When eval is set to FALSE, the code appears in the report, but the code is not run and the results do not appear.

## 8. The collapse option
Let's discuss one more chunk option, collapse. The collapse option specifies whether or not the code and any text output are split into multiple blocks or included in a single block in the final report. Consider the warning messages we saw when creating plots. We can modify how these render in the final report using the collapse option. Unlike the other options we've discussed so far, the default option for collapse is FALSE. This means that the code from the code chunk and text output resulting from the code will be separated in the knit report.

## 9. The collapse option
If instead we specify collapse equals TRUE, the code and text output are merged into a single block in the knit report.

# Warnings

## 1. Warnings, messages, and errors
Let's discuss warnings, messages, and errors, and how to specify whether or not to include them in a report.

## 2. Warnings
We encountered warnings earlier while creating visualizations. Recall that when data was excluded from a plot, the knit file included a warning in the final report. The default for the warning chunk option is TRUE and, since we had not included an argument to suppress warnings, they were included in the knit file.

## 3. Warnings
Earlier, we learned to use collapse equals TRUE to prevent warning messages from appearing in a separate block from the code in the knit report.

## 4. Warnings
However, we may want to exclude them entirely and can do this by setting the warning chunk option equal to FALSE. As we discussed earlier when we first encountered warnings, if we exclude the warnings, we may want to include additional information about them in the text of the report.

## 5. Messages
We have not encountered messages in our reports thus far, but this is because of another option that has been included. Recall, the data code chunk has the include option set to FALSE, which prevents the code and any results of the code from appearing in the final report.

## 6. Messages
Notice that, if we remove this option, we see messages appear in the knit file. These messages are related to the packages and the data files that are loaded in this chunk.

## 7. Messages
If we set message equals FALSE, these messages do not appear in the report. The include option has been used in the data chunk instead because we did not want the code or the results from the code in the report. Here, the results of the code are the messages we see when we do not specify any options in the code chunk. If we want the code to appear, but not any of the resulting messages, we should set message equals FALSE instead.

## 8. Messages
For example, if the code chunk contains code to load the data and filter it further, we may want the code to appear in the report without any messages. To do this, we use message equals FALSE instead of include equals FALSE.

## 9. Errors
The error option determines how errors in the code should be handled when knitting the report. The default option for error is FALSE, which means that if there is an error and we attempt to knit the file, the report will stop knitting when it encounters an error and return the error. If we set error equals TRUE instead, our report will knit, even with errors in the code, and the report will include the errors. This option is used less commonly, but it can be useful when working on a report to point out which code chunks are running as expected and which code chunks are causing errors. If we include this option, we should set it globally so it applies to all code chunks throughout the file.

# Customizing the report

## 1. Adding a table of contents
Let's discuss how to add a table of contents to a report.

## 2. Table of contents
Including a table of contents provides the audience with an overview of the report. To add a table of contents, we add toc and true as a new key value pair in the YAML header. The file won't knit unless the correct indentation is used in the YAML header. We include the toc field with an added indentation, and nest it within the html_document field.

## 3. TOC depth
We can specify which headers will appear in the table of contents by adding the toc-underscore-depth field. The number we list after toc_depth specifies the size of headers that will be listed in the table of contents. For example, a toc depth of two means that headers that use two hashes, and larger headers that use one hash, will appear in the table of contents. When we knit the file, only the Datasets header is shown, since it is the only header that uses two hashes and there are no headers with one hash. By default, the depth is three for HTML documents and two for PDF documents.

## 4. Number sections
We can also add section numbering to the headers in the table of contents by adding number-underscore-sections colon true. If we include number sections, and want the decimal numbering to start with one, the largest headers in the report should use one hash.

## 5. Number sections
If the largest headers in the report start with two hashes, the section numbering will start with zero. In the Markdown file shown, Datasets is the largest header and uses two hashes, so the number next to the Datasets header in the table of contents is zero-point-one-point-one.

## 6. TOC float
When creating HTML documents, we have some additional options for the table of contents. When toc-underscore-float is set to true in the YAML header, the table of contents will appear on the left side of the document and will continue to remain visible while the reader scrolls through the document.

## 7. TOC float: collapsed
Within toc float, we can also use the collapsed and smooth scroll options. The previous table of contents options we've discussed, toc and toc_depth, are separate attributes, while the collapsed and smooth scroll options are nested within the toc_float field. Since these options are nested, we remove true from toc_float when specifying either collapsed or smooth scroll. The collapsed option is true by default, and it determines whether or not the table of contents only displays the largest headers. When collapsed is used, the table of contents expands as someone is reading through the report or navigating to another section. When collapsed is set to false, the full table of contents remains visible.

## 8. TOC float: smooth scroll
The smooth-underscore-scroll option is also true by default. This option animates page scrolls when a reader clicks on an item in the table of contents to navigate to another section of the report. When smooth scroll is set to false in the YAML header, clicking on an item in the table of contents will navigate the reader to that section of the article without animation.

## 9. Summary
We've discussed a number of options for the YAML header. To summarize, we discussed the toc, toc_depth, and number_sections options for HTML and PDF files. Recall that the default toc_depth is three for HTML documents and two for PDF documents. Then, we discussed toc_float for HTML documents, and the collapsed and smooth_scroll options within that field that can be used to further customize the knit report.

# Parameters

## 1. Creating a report with a parameter
Throughout the course, we've created reports that present information on the projects in a particular country.

## 2. Parameters
Using the investment_services_projects data, we could create reports for a number of different countries. If we want to create a report for 10 countries from the data, it would require a lot of time and effort to create each report separately and manually edit each report for each country. Instead of manually editing new reports, we can use a parameter to efficiently create new reports that summarize the data for different countries. Parameters are used to create a report with specific values for key inputs that are listed in the YAML header.

## 3. Adding a parameter
Let's add a parameter that will help create a report for any country we specify. At the top of the document, within the YAML header, we add the params field and a colon. We then add another line, indent it, and add the parameter name, followed by a colon. Let's call this parameter country, since we'll be using it to indicate the country that will be the focus of the report, and list Indonesia as the country. Notice that Indonesia is not listed in quotations. Recall that specific indentation must be used correctly in the YAML header for the report to be successfully knit. After adding the parameter, we should review each element of the document, the code, text, and YAML header, for any references to a specific country.

## 4. Reviewing the code
When reviewing the code, we'll want to rename any code chunks and objects that reference a particular country

## 5. Reviewing the code
to avoid confusion for others who may be reviewing the code for subsequent reports that focus on other countries.

## 6. Reviewing the code
Within each code chunk, we review and replace any instance where we referenced a particular country with

## 7. Reviewing the code
params dollar sign country, where country is the parameter we added to the YAML header.

## 8. Reviewing the code
We also need to review the labels used in the plots we created,

## 9. Reviewing the code
and remove any references to a particular country.

## 10. Reviewing the text
While reviewing the text, we'll want to edit references to a particular country so that when we knit a new file using the parameter, the file will be consistent with the country we specify.

## 11. Reviewing the text
We can modify text, headers, and even the YAML header using syntax we used when adding date formatting to the date field in the YAML header earlier in the course. Where the text or header refers to a specific country name, we can replace the name with, in backticks, the letter r to specify the language and params dollar sign country.

## 12. Reviewing the YAML header
We'll then review the YAML header and modify the document title to include the country using the parameter. Using the same syntax we used to modify the text and headers, in backticks, we specify r as the language followed by params dollar sign country.

## 13. Knitting the report
When we knit the document using Turkey for the country parameter, we see the resulting report is updated with the information from this country.

## 14. Knitting a new report
Let's knit the document using another country, the Philippines. Notice that we only need to replace the country parameter and the file knits with the updated information.

# Multiple Parameters

## 1. Multiple parameters
Let's add another parameter to the YAML header to increase efficiency when creating new files. Another piece of information we've specified in the document that we can use as a parameter is the fiscal year.

## 2. fiscal year
The data we've been using has information from the 2012 to 2018 fiscal years, and the fiscal year is defined as beginning July 1st of the previous year through June 30th of the year of interest. We've used the fiscal year in the report when filtering to create a plot of the projects within a particular year.

## 3. Adding a parameter for fiscal year
Since we reference the fiscal year of interest in the report, let's add it as a parameter. Below the existing country parameter, we add fy for fiscal year, a colon and 2012. Remember, indentation is important.

## 4. Adding parameters to define fiscal year
The fiscal year is defined by the start and end dates of the year. Let's also add these as parameters. Below the country parameter, we'll add a year_start parameter and a year_end parameter. The start date of the 2012 fiscal year is 2011-07-01 and the end date of the fiscal year is 2012-06-30. Notice that the dates are listed in quotations and we preserve the year-month-day format from the data. As before, we'll need to review each element of the document, the code, text, and YAML header, to ensure that the new report won't make incorrect references to previous versions of the report.

## 5. Reviewing the code
While reviewing the code, we replace the date filter we used to create the plot of projects in a given fiscal year

## 6. Reviewing the code
with params dollar sign year_start and params dollar sign year_end.

## 7. Reviewing the code
We'll also rename any code chunks and objects that reference a particular fiscal year,

## 8. Reviewing the code
remove the specific year, and use the word annual in the names instead, so that they will apply to new reports that summarize information about other fiscal years.

## 9. Reviewing the text
Recall that we can modify the document to reference parameters in the text, headers, and YAML header of the report. Notice the specific references to a particular year in the text and header of the document.

## 10. Reviewing the text
We can replace these instances with the fiscal year parameter using, in backticks, r params dollar sign fy.

## 11. Reviewing the YAML header
After reviewing the YAML header and verifying that nothing else needs to be modified, we can run the file with the parameters.

## 12. Knitting the report
Let's knit the file for the country Turkey and the fiscal year 2013. We change fy to 2013, the start date to 2012-07-01, and the end date to 2013-06-30. When we knit the file, we see the report has been updated with the new information.

# Customizing the report

## 1. Customizing the report
Let's customize a report using colors and fonts to reflect a brand. First, we'll modify the styles directly in the report, then we'll discuss how to create a Cascading Style Sheet or CSS file to add the HTML element settings to any report.

## 2. Specifying element style
Outside of any code chunks, we surround the style specifications with less than style greater than and less than backslash style greater than. To add elements, we reference a particular section of the document with the specifications enclosed in curly braces, using specific indentation. Commonly used properties include color for the text, background hyphen color, font hyphen family, and font hyphen size. We can include the styles section anywhere in the document, outside of any code chunks. To keep the sections organized, we'll add it to the top of the document, below the YAML header.

## 3. Document style
Let's start with the overall document. Within the style indicators, we add body, curly braces, color, colon, and the color we want to use for the report text. We can add a color name, like red or blue, and a semicolon. We won't get an error if we forget to include a semicolon after a property, but the style will not update. Here, we specify red and see the red text in the knit file.

## 4. Using color hex codes
We can also use hex codes to specify colors, with a single hash and no spaces before the hex code. There are many references we can use to look up color hex codes. Here we're using 708090 or slate gray. We add a background color, modify the text font using font-family, for example, Calibri, and knit the report.

## 5. Code chunks
If we include code chunks, we can modify them using pre, curly braces, and specifying the text color and the background color.

## 6. The table of contents
The table of contents properties are specified using hash TOC. Within curly braces, we specify the text color and font. We can add a border color using border hyphen color and modify the font size using font hyphen size and specifying a number followed by px. We won't discuss px in detail. At a high level, it corresponds to the pixels and the way the text appears varies depending on the device being used to view the report. We knit the file, and see the updated table of contents.

## 7. The header
The header properties are specified with hash header. Here, we add color, background-color, font-family, and font-size. We can modify the background color transparency using opacity and a decimal. The default value is one, and here we've used zero point six. Notice that the header styles modify all aspects of the header, including the title, date, and author.

## 8. The title, author, and date
Alternatively, we can modify each header element individually, using h1-dot-title for title, h4-dot-author for author, and h4-dot-date for date.

## 9. CSS file
Instead of adding styles within the file, we can reference a CSS file that contains specific styles. This means we can reuse a CSS file for many different reports without needing to copy and paste the CSS code into each new Markdown file we create. We can use any text editor to create the style sheet by adding the information in the text editor, excluding the boundary style words, and saving the file using the extension dot css. Then, we add a css field to the YAML header and the name of the style sheet. Here, the style sheet is called styles-dot-css. When we knit the file, the specified styles will appear in the report.

