# Hands-on Session 2: Combining Heterogeneous Review Datasets

The dataset for this assignment consists of reviews extracted from three different websites:

- [leestafel.info](http://leestafel.info/)
- [literairnederland.nl]()https://www.literairnederland.nl/category/recensies/
- [boekreviews.nl](http://www.boekreviews.nl/)

These websites were crawled for book reviews. Not all website content was crawled, and some reviews may have been missed. Also, some crawled pages may not represent book reviews. The reviews were parsed to extract as much useful data as possible, but focusing on metadata fields that occur in the ODBR dataset of the previous assignment.

Go to the workshop SurfDrive folder (you should have received the URL for that in an email) and download the dataset of crawled reviews, *crawled_reviews.csv.gz*.

This dataset contains some 8k reviews. Because the websites each have their own choices of what metadata to include, have changed their policies over time and have not always been consistent, the available metadata per review varies. 

The goal of this assignment is to add these crawled reviews to the ODBR dataset, keeping track of transformations, selections, etc.

## Step 1. Comparing Datasets

Create a new project in Open Refine (or some other tool) and import the dataset. For several of the metadata fields, there is an additional field that indicates how that metadata was extracted, e.g. from a clearly marked HTML element or meta header, or via a regular expression in the page text. 

Compare the three datasets on a number of aspects:

- number of reviews
- number of reviewers
- source of metadata fields like ISBN, author and publisher
- completeness of metadata fields like ISBN, author and publisher
- overlap in metadata fields with the previous dataset

Make a description of this analysis for others (or yourself at a later date) so they can get a quick understanding of the characteristics of these datasets.

### Step 2. Filtering/Selecting Reviews

Before mapping the crawled review metadata to the ODBR data model, you might first want to consider if all reviews should be included, or if there are reviews that you would leave out. E.g., data records for which the reviewed book cannot be identified, (f.i. there might be records in the dataset that are not actual book reviews).

Think of a good way to keep track of what has been filtered out, along with clear filtering criteria.

Also, some reviews may review multiple books. How would you deal with these in combining the three datasets?

How do you deal with different provenance of specific metadata fields? E.g. ISBN extracted from text vs. ISBN via WorldCat Search SRU lookup?

### Step 3. Mapping Metadata Fields

Finally, make a mapping of metadata fields from the crawled reviews to the ODBR dataset. 



