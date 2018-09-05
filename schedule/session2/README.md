## Hands-on Session 2: Combining Heterogeneous Review Datasets

This is a group assignment. Before you start working on each of the steps below, discuss possible approaches together. 

The dataset for this assignment consists of reviews extracted from three different websites:

- [leestafel.info](http://leestafel.info/)
- [literairnederland.nl](https://www.literairnederland.nl/category/recensies/)
- [boekreviews.nl](http://www.boekreviews.nl/)

These websites were crawled for book reviews. Not all website content was crawled, and some reviews may have been missed. Also, some crawled pages may not represent book reviews. The reviews were parsed to extract as much useful data as possible, but focusing on metadata fields that occur in the ODBR dataset of the previous assignment.

Go to the workshop SurfDrive folder (you should have received the URL for that in an email) and download the dataset of crawled reviews, *crawled_reviews.csv.gz*.

This dataset contains some 8k reviews. Because the websites each have their own choices of what metadata to include, have changed their policies over time and have not always been consistent, the available metadata per review varies. 

The goal of this assignment is to add these crawled reviews to the ODBR dataset, keeping track of transformations, selections, etc.

### Step 1. Comparing Datasets

Create a new project in Open Refine (or some other tool) and import the dataset. For several of the metadata fields, there is an additional field that indicates how that metadata was extracted, e.g. from a clearly marked HTML element or meta header, or via a regular expression in the page text. 

Compare the three datasets on a number of aspects:

- number of reviews
- number of reviewers
- source of metadata fields like ISBN, author and publisher
- completeness of metadata fields like ISBN, author and publisher
- overlap in metadata fields with the previous dataset

Make a description of this analysis for others (or yourself at a later date) so they can get a quick understanding of the characteristics of these datasets.

### Step 1a. Filling in Missing Metadata

This step is optional, if you have a WorldCat Search API key.

If you know the ISBN of a book, it is possible to look up additional information connected tot that ISBN via e.g. the WorldCat Search SRU service. 

For instance, to look up information for ISBN 9789038890074, use the following URL:

- *http://www.worldcat.org/webservices/catalog/content/libraries/isbn/9789038890074?format=json&wskey=<YOUR_WS_API_KEY>*

In Open Refine, you can do this by editing the *isbn* column and adding an additional column with information fetched via the WorldCat Search service (*Edit column* > *Add column by fetching URLs...* and in the *Expression* box replace *value* with *"http://www.worldcat.org/webservices/catalog/content/libraries/isbn/" + value + "?format=json&wskey=<YOUR_WS_API_KEY>"*). Make sure the throttle delay is not too low to use up too much of WorldCat's bandwith. Also, make sure you also fetch ISBN information for records that you want to enrich. 

The fetching process will take some time, but will add book metadata as JSON data. See [Open Refine documentation on fetching URLs](https://github.com/OpenRefine/OpenRefine/wiki/Fetching-URLs-From-Web-Services) for how to parse this.

### Step 2. Filtering/Selecting Reviews

Before mapping the crawled review metadata to the ODBR data model, you might first want to consider if all reviews should be included, or if there are reviews that you would leave out. E.g., data records for which the reviewed book cannot be identified, (f.i. there might be records in the dataset that are not actual book reviews).

Think of a good way to keep track of what has been filtered out, along with clear filtering criteria.

Also, some reviews may review multiple books. How would you deal with these in combining the three datasets?

How do you deal with different provenance of specific metadata fields? E.g. ISBN extracted from text vs. ISBN via WorldCat Search SRU lookup?

### Step 3. Mapping Metadata Fields

Finally, make a mapping of metadata fields from the crawled reviews to the ODBR dataset. Don't worry about ODBR fields you don't find in the crawled dataset. 



