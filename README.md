# BIG-DATA-ANALYSIS

*COMPANY*: CODETECH IT SOLUTIONS

*NAME*: MAYANK SINGH

*INTERN ID*: CT04DH1908

*DOMAIN*: DATA ANALYTICS

*DURATION*: 4 WEEKS

*MENTOR*: NEELA SANTOSH

*DESCRIPTION*
** This task aims to perform an in-depth genre analysis of the IMDb Top 1000 movies using big data tools and visualization libraries. We employ Dask for scalable data processing, Pandas for tabular manipulations, and Matplotlib for generating insightful visualizations. The dataset (imdb_top_1000.csv) comprises a broad spectrum of movie metadata, with particular focus on the genre information tagged to each film.

Step-by-Step Task Description:

Library Imports and Environment Setup:
The notebook begins with importing required libraries: Dask (for distributed, scalable dataframe operations), Pandas (for tabular data handling and interoperability with Dask), and Matplotlib (for data visualization). Dask is chosen for its ability to handle larger-than-memory datasets efficiently, making it an ideal tool for processing potentially large CSV files.

Data Loading:
The dataset (imdb_top_1000.csv) is loaded into a Dask DataFrame. Special care is taken to correctly type specific columns (e.g., setting Released_Year as object and Meta_score as float). Dask’s lazy evaluation allows efficient handling of the data until actions like compute are explicitly called, ensuring memory-efficient operations.

Preprocessing – Genre Splitting and Normalization:
In most movie recommendation or analytics datasets, genres are often present as comma-separated lists within a single column. To perform robust analytics, each genre entry (e.g., “Action, Adventure, Sci-Fi”) needs to be treated as individual rows. This is achieved through a function split_and_stack, which splits the genre strings into lists, then "explodes" them so that each genre per movie becomes a separate record. The method carefully removes any leading/trailing whitespace, ensuring consistent genre labeling.

Partitioned Operations with Dask:
Dask works on data partitions (subsets of the dataset), so map_partitions is leveraged to efficiently apply the genre splitting/exploding process over each partition, maintaining parallelism and performance. This step results in a normalized Series containing one genre per row, primed for aggregation.

Genre Occurrence Counting:
With genres now in single rows, the analysis proceeds to tally the frequency of each genre across the Top 1000 movies by using .value_counts(). Dask computes the counts in a distributed fashion and, upon .compute(), consolidates the results into a standard Pandas Series. This enables seamless transition to plotting and further exploration.

Tabular and Visual Reporting of Results:
The computed genre frequencies reveal the most common genres among the highest-rated or most-known films. The top ten genres by prevalence are displayed both as text output for quick reference and as a bar chart using Matplotlib. The visualization succinctly communicates which genres dominate the IMDb Top 1000 list, aiding film historians, cinephiles, or business analysts in quickly understanding trends.

Extended Analytics (Optional in Current Notebook):
Additional code cells (present in the notebook) are designed to analyze movie count per decade and other breakdowns (not fully visible in the excerpt but hinted at). This typically involves extracting release years, bucketing them into decades, counting entries, and visualizing as bar charts, which further adds to the demographic and temporal understanding of movie popularity.

Key Challenges Addressed:

De-normalized Data: Genre data is not pre-exploded, requiring custom transformation.

Efficient Scalability: Dask enables analysis to scale beyond what Pandas alone could handle smoothly, setting a template for analyzing larger datasets.

Accurate Counting: By exploding genre entries, each occurrence is counted appropriately, avoiding underestimation that could result from treating multi-genre movies as single data points.

Learning Outcomes:

Practical Dask Use: The workflow demonstrates practical use of Dask for scalable data handling in the context of text field normalization and aggregation.

Pandas and Dask Interoperability: Shows best practices in moving between Dask and Pandas, especially for visualization and final result computation.

Data Visualization: Reinforces the importance of visual communication of analysis findings through Matplotlib.

Text Data Handling: Illustrates common preprocessing steps for dealing with comma-separated list fields within CSV/tabular data.

Applications:
This genre analysis template serves many real-world applications—film market research, streaming platform content strategy, academic studies in film or media, and the design of recommender systems. By quantifying and visualizing genre prevalence, stakeholders can identify trends, gaps, and potential opportunities in film content curation.

Summary:
This task exemplifies an end-to-end genre frequency analysis pipeline using modern, scalable Python tools. From data ingestion, transformation, through distributed computing, to insightful visualization, it provides a practical and robust methodology for understanding categorical data within large movie datasets. The approach is generic and extendable, providing a foundation for more advanced film analytics or other genres/categorical data analyses.**
