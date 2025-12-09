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

With the cleaned data I was able to create three bar graphs, two pie charts, and a density map, shown as follows:

<figure>
  {% include_relative pv_bar.html %}
  <figcaption style="text-align:center; font-style:italic;">
    Figure 1: A side by side visualization of the total number of political violence events each year taking place in Palestine and Israel. The top graph shows the distribution between the total events in Palestine as a whole and Israel. The bottom divides the Palestine data between two graphs, with one representing the total events in the West Bank alongside the total events in Israel, while the other represents the total events in the Gaza Strip alongside the total events in Israel.
  </figcaption>
</figure>

<figure>
  {% include_relative pv_map.html %}
  <figcaption style="text-align:center; font-style:italic;">
    Figure 2: The distribution of political violence events between the West Bank, the Gaza Strip, and Israel, as a density map. Political violence events are clearly concentrated in the West Bank and the Gaza Strip, with relatively few events taking place in Israeli territory.
  </figcaption>
</figure>

<figure>
  {% include_relative pv_pie.html %}
  <figcaption style="text-align:center; font-style:italic;">
    Figure 3: Distribution of types of political violence that occur in the West Bank and in Gaza.
  </figcaption>
</figure>

The following figures were created by my partner:

*Insert figures*

### Discussion
My data and visualizations (Figure 1, Figure 2, and Figure 3) provide a shorter-term but more detailed account of events from 2016 through 2024, while my partner’s data and visualizations (Figure 4, Figure 5, Figure 6, and Figure 7) serve to provide a broader historical context.

Looking at Figure 1 and Figure 2, it is abundantly clear that political violence events between Palestine and Israel occur disproportionately in Palestine as opposed to in Israel. Across all years, when political violence occurs in Israel, the volume of events is almost inconsequential when compared to the scale of political violence that occurs in the Palestinian Territories. These patterns speak to the first question we posed: which group has perpetrated the most violence over time? Given that the overwhelming majority of events occur in Palestinian areas and it is well documented that these events are most often perpetrated by Israeli settlers and Israeli military forces, the data shows that Israel has perpetrated the most violence in the region from 2016 through 2024.

When answering how does the distribution of conflict events differ between Gaza, the West Bank, and Israel?, we can turn to Figure 1 and Figure 3, as well as the answer to the previous question, for insights. Once again, we can clearly see that substantially fewer events of political violence take place in Israel than in the West Bank or in Gaza. There is something to be said in comparing the distribution of political violence events in the West Bank and Gaza, however. The data shows that in the years prior to the genocide in Gaza (i.e. before October 7, 2023), the West Bank consistently experienced more events of political violence than Gaza. Though both territories have been under Israeli military occupation since 1967, the dynamics of the occupation differ greatly between them. The West Bank is defined by many expanding illegalIsraeli settlements and military checkpoints, creating conditions for frequent contact and points of friction. Meanwhile, Gaza is isolated. No settlers have been in Gaza since 2005, and it has been subjected to a blockade since 2007. For this reason, there has been significantly less daily interaction between Palestinians in Gaza and Israeli military/security forces, thus resulting in fewer events of political violence than in the West Bank.

We can further examine the differing dynamics of political violence in the West Bank and Gaza by understanding the different types of events that occur in each territory. By looking at Figure 3, we can see that there is a notable difference between the two, with air/drone strikes and shelling/artillery/missile attacks accounting for the most events in Gaza, while in the West Bank, mob violence and armed clashes make up the majority of events.

From my partner’s analysis, he was able to reveal several broad patterns. First, Conflict types vary substantially over time. Figure 7 shows clear shifts in dominant conflict types in different periods. Certain decades are marked by increases in organized battles, while others show rises in one-sided violence (civilian targeting). This information was able to assist in answering the question What kinds of conflict has each group perpetrated, experienced, or otherwise taken part in and how has this changed over time? By isolating Palestine-related and Israel-related events, we can distinguish which groups appear most often in different roles and conflict types, although precise attribution requires caution.

Next, events involving Israel and Palestinian groups occur across the entire historical range of the dataset. Figure 4 confirms that conflict events are not limited to a single era, but instead persist from 1946 through 2021. 

Further, events involving Israel and Palestinian groups occur across the entire historical range of the dataset. Figure 4 confirms that conflict events are not limited to a single era, but instead persist from 1946 through 2021. 

Finally, The dataset supports broad comparisons between actors. By isolating Palestine-related and Israel-related events, we can distinguish which groups appear most often in different roles and conflict types, although precise attribution requires caution.

### Conclusion
Through this project, my partner and I set out to examine how patterns of conflict differ between the West Bank, the Gaza Strip, and Israel, and to understand which groups have perpetrated the most violence over time, by combining broad historical data and recent, detailed data.

The modern data reveals a stark imbalance in which a vast majority of the political violence that takes place between Palestine and Israel takes place on Palestinian land. Further, before 2024, the West Bank experienced more frequent events of political violence than in Gaza, reflecting the differences between the two occupations: one characterized by everyday interactions with military forces and settlers, the other by periodic bombardment and fewer day-to-day interactions.

The historic data revealed how although conflict types vary over time, conflict events are not limited to a single era, but instead persist over the years.

The data was not without its limits. It was difficult to classify all actors into an Israeli, Palestinian, or ‘other’ group, so some of the less prevalent groups were likely excluded from the data. Furthermore, due to issues of ambiguity, Jerusalem had to be left out of the analysis, as accurate categorization could not be ensured. Finally, while data can quantitatively represent political violence events, it is unable to contextualize the information in the social, historical, and political scope in which it occurs; thus, an understanding these conditions is essential to interpret the data with the necessary depth.

Going forward, I would like to continue the analysis of this data by exploring more visualizations, especially further mapping applications. I would also like to find a better way to classify the actors, as well as dig deeper into the data in order to be able to include Jerusalem in future analysis. Additionally, combining this data with other, more qualitative sources would serve to enrich the story that this data can tell.
















