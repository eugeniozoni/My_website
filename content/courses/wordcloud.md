---
title: Wordcloud
linktitle: Wordcloud
toc: true
type: docs
date: "2020-04-08T00:00:00+01:00"
draft: false
menu:
  example:
    parent: Data visualization with R
    weight: 2

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 
---

In this small project I wanted to generate a wordcloud from the keywords of my scientific publications, to visualize all my scientific work in one figure.

<img src="/courses/wordcloud_files/wordcloud_150.jpg" alt="wordcloud" width="600"/>

This project is divided in three parts:
* **Retrieve the complete metadata of all my scientific publications**
* **Generate the wordcloud**
* **Personalize the word cloud**

## **Retrieve metadata from scientific literature**

I have retrieved the metadata for all my scientific publication - up to date - by searching for my author name in the author field of [**Web of Science**](https://www.webofknowledge.com). The results of the search were exported in the *BibTeX* format and saved as `savedrecs.bib` file.

I have used the R package [**bibliometrix**](https://bibliometrix.org/) to access the metadata in the BibTeX file. To do that, first we load the necessary library:
```{r, warning=FALSE, message=FALSE}
library(bibliometrix)
```

Then we use the function **convert2df** to convert the *BibTeX* file into a dataframe. We also specify the variable `dbsource='wos'` since we downloaded our metadata from Web of Science (WOS) and define the `format="bibtex"` since the file was exported in this format.
```{r , message = FALSE, warning = FALSE}
D <- convert2df("Your-path-to-the-file-location/savedrecs.bib", dbsource = 'wos', format = "bibtex")
```

According to the structure of the dataframe that we just created, as described in the [**vignette**](https://cran.r-project.org/web/packages/bibliometrix/vignettes/bibliometrix-vignette.html) of the *bibliometrix* R package, the keywords associated by SCOPUS or ISI database can be found in the column `D$ID`. 
The content of this column is the one of interest for the scope of this project.

Now we are ready to extract the contend of the column `D$ID`. We create a new object `keywords` which will contain all our keywords and we save this file as `.txt` file. 
We specify the variable `row.names = FALSE` to make sure that the only text containd in our file will be the keyword text.
```{r , message=FALSE, warning=FALSE}
keywords<-D$ID
write.table(c(keywords), "keywords.txt", row.names = FALSE)
```
The file that we created above is a text file which contains as many lines as the number of our publications. In each line we will find the keywords corresponding to each one of our publications. 

At this point we are ready to generate our word cloud!

## **Generate the wordcloud**

To generate the wordcloud we will need to do some text mining and highlight the most frequently used keywords in our text file.

First we need to load some libraries:
```{r , message=FALSE, warning=FALSE}
library("tm")
library("SnowballC")
library("wordcloud")
library("RColorBrewer")
```

Then we load the text in our *keywords.txt* file and the data as **corpus**. 
```{r , message=FALSE, warning=FALSE}
keyword_text <- readLines("keywords.txt")
docs <- Corpus(VectorSource(keyword_text))
```

Afterwards we clean the text by removing punctuation, numbers and common stopwords in english.
```{r , message=FALSE, warning=FALSE}
docs <- tm_map(docs, removePunctuation)
docs <- tm_map(docs, stripWhitespace)
docs <- tm_map(docs, removeWords, stopwords("english"))
```

Now we build a term-document matrix which is a table containing the frequency of the words.
```{r }
dtm <- TermDocumentMatrix(docs)
m <- as.matrix(dtm)
v <- sort(rowSums(m),decreasing=TRUE)
d <- data.frame(word = names(v),freq=v)
head(d, 10)
```

Finally, we can generate our wordcloud:
```{r , message=FALSE, warning=FALSE}
set.seed(1234)
jpeg("wordcloud.jpg",width=7,height=7,units="in",res=150)
worcloud<-wordcloud(words = d$word, freq = d$freq, min.freq = 1,
                    max.words=200, random.order=FALSE, rot.per=0.35,
                    colors=brewer.pal(8, "Dark2"))
dev.off()
```
<img src="/courses/wordcloud_files/wordcloud_150.jpg" alt="wordcloud" width="600"/>

## **Personalize the wordcloud**

We can decide to rotate the words in the wordcloud to improve readibility. For this we can set the value of the variable `rot.per=0` . This will rotate all the words and position them with a 90 degree angle as normally a text appears.
```{r , message=FALSE, warning=FALSE}
set.seed(1234)
jpeg("wordcloud.jpg",width=7,height=7,units="in",res=150)
worcloud<-wordcloud(words = d$word, freq = d$freq, min.freq = 1,
                    max.words=200, random.order=FALSE, rot.per=0,
                    colors=brewer.pal(8, "Dark2"))
dev.off()
```

<img src="/courses/wordcloud_files/wordcloud_150_90.jpg" alt="wordcloud" width="600"/>

## **Credits**

Credits for the feasibility of this project should be given to the authors of [**bibliometrix**](https://bibliometrix.org/) and [**STHA**](http://www.sthda.com/english/wiki/text-mining-and-word-cloud-fundamentals-in-r-5-simple-steps-you-should-know) which is an icredibly well done training website, with many tutorials on data analysis and visualization using R software and packages.







