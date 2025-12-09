Gabrielle Edwards <br>
Wol Bol Wol Majok

### Introduction
My data comes from the [ACLED Data Export tool](https://acleddata.com/conflict-data/data-export-tool?event_date_from=2016-01-01&event_date_to=2025-09-18&fields_on%5Bevent_id_cnty%5D=event_id_cnty&%2Fviews%2Fajax%3F%2Fviews%2Fajax%3Fevent_date_from=2016-01-01&viewsreference%5Breload%5D=eJxdi8EKwjAQRP9lzx5stVDzKyLLSsa6kMaQLJUi_rspORQ8zGHmvfkQotwDPBeYaZwKuevtQEkyonGN2sq2JpDbRpmypCf9C-or7k_jOOzooQieo8zbtZVF8d6FjEWLvmJ7d_25Gy6VNlUNM3sEE3LH7w-71Dq1&order=event_date&sort=desc), which includes “type, agents, location, date, and other characteristics of political violence events, demonstration events, and other select non-violent, politically-relevant developments in every country and territory in the world,” according to the [ACLED Codebook](https://acleddata.com/methodology/acled-codebook#civilian-targeting-4). Before downloading the data, I filtered it to focus on events taking place in the countries of Palestine and Israel. The event data I work with in this project takes place between January 1, 2016 and December 31, 2024.

My partner used the [Uppsala Conflict Data Program (UCDP) dataset](https://www.kaggle.com/datasets/zazaucd/conflict-data) from Kaggle, which contains event-level records of organized violence, including the actors involved, conflict type, location, and date. He planned to look at the subset of the data focused specifically on Israel and Palestine.

Through this project, my partner and I posed several guiding questions which we attempted to answer through data analysis and visualization:
* Which group has perpetrated the most violence over time?
* How does the distribution of conflict types involving Israel and Palestine change over time?
* What kinds of conflict has each group perpetrated, experienced, or otherwise taken part in and how has this changed over time?
* How does the distribution of conflict events differ between Gaza, the West Bank, and Israel?

Our task was to identify, clean, and analyze our specific datasets as they related to Palestine and Israel in order to answer these questions.

### Methods and Results
To begin, out of the thirty columns in the original DataFrame I selected the fifteen that were most relevant to the research and I filtered out all events from the year 2025, as they only went through September and would skew certain types of visualizations.

The data includes four columns of actors: actor 1, associate actor 1, actor 2, and associate actor 2. Specific actors were not relevant to my analysis, but the country the actor represented was. To generalize each actor to a country, I fed the list of all possible actors to ChatGPT and had it come up with a list of keywords to classify an actor as either Israeli, Palestinian, or ‘other.’ I made four new columns: party 1, associate party 1, party 2, and associate party 2, and put the respective classification into each column. Though it is not a perfect system, it was able to account for the most relevant actors from each country.

After that, I began the process of filtering for relevant information. I started by filtering for rows that include both an Israeli and a Palestinian party to ensure that the data reflects interactions between Israeli and Palestinian actors. Next I filtered the data to only include sub-event types coded as Political Violence. Political Violence in the ACLED Codebook is defined as a single altercation defined by “the use of force by a group with a political purpose/motivation, or with distinct political effects,” and includes the following broad event types: battles, excessive force against protestors, explosions/remote violence, and violence against civilians.

I created separate DataFrames for events taking place in the country of Israel and the country of Palestine. I then also made separate Dataframes for events taking place in the West Bank and the Gaza Strip (the two territories within Palestine). I did so because I wanted to do a comparison of Israel and Palestine as a whole, but given the differences between the types of events that occur in the West Bank and in Gaza, I also wanted to compare each with Israel individually. This necessitated the separate DataFrames, as Palestine and Israel are listed under the ‘country’ column, while the West Bank and Gaza Strip are listed in the ‘admin1’ column.
Finally I grouped each of these DataFrames by year, totaling the number of events in the DataFrame, concatenated each of the non-Israel GroupBy’s with the Israel GroupBy, and pivoted each of the concatenations.
With the cleaned data I was able to create three bar graphs, two pie charts, and a density map, shown on the following pages.
