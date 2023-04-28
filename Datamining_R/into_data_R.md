##Intro
In this lab, we will learn to work with table data. We'll use data from online databases, and view, arrange, and analyze the data using the programing language R. The data that we'll focus on is data on gene interactions, and data on gene expression. We will use data integration to identify a set of candidate gene interactions to explain the effect of variation in the gene BRCA1.

Specifically, we'll find genes that interact with BRCA1, and then ask whether these interacting genes are actually ever expressed in the same tissue as BRCA1. They can't really interact in vivo if they're not expressed together!

The overall outline is:

Query a database of gene interactions for BRCA1
Download a table of the interaction data
Find and download a database of gene expression by tissue
Inspect both data tables, and identify common keys
Use BioMart to create a new table to match the keys between our two tables
Use R to test whether each pair of interacting genes is expressed in the same tissue
The main skills we will learn are about processing data in R. We will cover:

Importing table data
Filtering tables
Sorting tables (arranging)
Parsing columns in tables
joining tables
intersecting lists
for loops in R

##Step 1: Gene interaction data

STRING is a database of gene-gene interactions. It's really a type of secondary, or federated database, meaning that it collections data on interactions of different types from many different databases and packages them into a common format. We'll use this database to download a table of genes that interact with BRCA1.

Start by going to the STRING website and doing a query for genes that interact with BRCA1 in humans.

Take a few minutes to explore the results.

Click the Exports button. You'll see the interaction data in table format. We want to download this data so that we can process it. Click the download button for ... as tabular text output. Save the file on your desktop as BRCA1_String.tsv. Open the file with Notepad++.

Note:

In a text editor, a tsv file looks fairly ordered, but is still hard to read. The file would look pretty much like this if you used head or cat to view the file in BASH.
The main thing to notice here is what separates the fields (or columns). In this file it is just whitespace. In a csv file, there would be a comma (,) separating each field. In a tsv file, it's actually the TAB character (not a space). This is important because then programs that read this file can tell the difference between a value with multiple words ("Gene 3"), and two values in different fields ("Gene" "3").
If you haven't worked with R before, you would probably open this file in Excel. Go ahead and do this. Excel understands the tsv format, and correctly separates the data into columns.

Question:

In Excel, can you sort the interactions by their experimental evidence? What is the strongest-supported interaction in this list?
In Excel, can you find all interactions that involve BRCA1 itself? How many are there?
Note:

Excel is relatively easy to use. However, it can cause lots of problems in Bioinformatics! One common problem is that Excel tries to be too smart.
Try adding a new entry for an interaction between BRCA1 and SEPT2. What happens? What problems would this cause? 
