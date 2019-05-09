## Analysis of Play store apps

Data source : <https://www.kaggle.com/lava18/google-play-store-apps#googleplaystore.csv>

**The Play Store apps data has enormous potential to drive app-making businesses to success. Actionable insights can be drawn for developers to work on and capture the Android market!**



| Parameter      | Indicates                                                    |
| -------------- | :----------------------------------------------------------- |
| App            | Application name                                             |
| **Category**   | Category the app belongs to                                  |
| Rating         | Overall user rating of the app (as when scraped)             |
| Reviews        | Number of user reviews for the app (as when scraped)         |
| Size           | Size of the app (as when scraped)                            |
| Installs       | Number of user downloads/installs for the app (as when scraped) |
| Type+          | Paid or Free                                                 |
| Price          | Price of the app (as when scraped)                           |
| Content Rating | Age group the app is targeted at - Children / Mature 21+ / Adult |
| Genres         | An app can belong to multiple genres (apart from its main category). For eg, a musical family game will belong to Music, Game, Family genres. |
| Last Updated   | Date when the app was last updated on Play Store (as when scraped) |
| Current Ver    | Current version of the app available on Play Store (as when scraped) |
| Android Ver    | Min required Android version (as when scraped)               |



What I have tried is finding useful business information about Android market. Which of the things are more profitable and important to know for businesses.



### Number of apps in each category in our dataset.



Using pivot table and plotting category on axis and also category on values, we can get counts of each category right inside pivot table.



![1554283193873](images/pivot_app_catetgory.png)



After sorting these values from lowest to highest and plotting chart we can get below result.



![1554283002647](images/apps_in_category.png)



> ### Family, Games, tools, Medical and Books are the top 5 categories in terms of app counts



### Market shares on basis of types. [Free/Paid]

##### Steps included

First by applying filter on Type column, I have found that It actually have other values along with Free/Paid types. There was one row with **NaN** and one with **0** values, So I Ignored it for sake of simplicity.

Select column and Press,

```
CTRL + H
```

Now we can find Word from Specific column that is selected, and perform operations.

Then sorted all data based on type. For making next step 

Just using subtotal we can easily achieve how many of are them are Free and Paid.



![market_share_on_type](images/market_share_on_type.png)

Then collapse the sheet at Level 2, It will show counts for Free and Paid.

We can easily make chart now, I preferred Pie chart for showing Proportion of 100% here.



![1554188844142](images/market_share_on_type_chart.png)

Conclusion: As we can see Free Apps are dominating the market.  

> #### 93% of apps are available for Free.
>



### Next we will dig further and find App prices for paid apps for each category.

For this, I have created Pivot table for whole table, And added Mapped Category on rows and Types on column. 



![1554193890562](images/Average_price_by_category_pivot.png)

And put Price in VALUES, After that By sorting values from Lowest to highest for price and creating bar chart for that will be our output, I have changed many small things in charts design for achieving below chart.



![1554193890562](images/Average_price_by_category.png)



> #### Finance, Lifestyles and Events categories apps are costlier then other categories.
>

Further we can analyze those 3 categories to see why they have such high values?

So, I have made changes in Pivot table and added **App** into Axes part and Moved **type and Category** into Series part of pivot table. as shown below:

![](images/finance_event_lifestyle_prices_pivot.png)

And then sort the table prices from Low to High and draw Bar chart will create below chart



![1554204501772](images/finance_event_lifestyle_prices.png)



**Conclusion:**

> #### There is only a single app for Event category and it's price is 109$ and thus category has higher value overall.
>
> #### Though, In Finance and Lifestyle has more apps with prices less than it's average values there are some apps which have higher prices and thus Average values are higher for categories also.
>
> #### Side note: Those apps which have higher prices shows similarities in their names, and it could be similar types of apps also.



### Let's see in which categories apps has highest installs?

Here, Install column is textual format and not number so we can't really do math over it.

As, values in this column is in format like 25000+ 

We will remove that **+** sign very first and **then convert it to number data type**

Then I took pivot table and calculated Average install counts for each category and plotted them.



![1554208480512](images/Avg_installs_category.png)



> #### Communication and social apps have highest installs as it include giant apps like Facebook, Whatsapp, Instagram etc. followed by video players, Productivity and Games.





### Content rating distribution of apps.

There is content rating which every developer must submit for distributing app on play store, This basically indicates the Age group which can use this app.

Categories : **Everyone, Teen, Mature 17+, Everyone 10+, Adults only 18+** 

For getting these counts, I have took simple pivot table of Content rating with it's own count.

![1554271777274](images/content_ratings.png)



> #### Clearly maximum apps are suitable for every age group and also around 11% of apps are targeted for Teens. There are also considerable amount of apps: 5% which are targeting to 17-18+ age users. 



### Top 25 apps with Average ratings on base of Total ratings

| Facebook                                             |
| ---------------------------------------------------- |
| WhatsApp Messenger                                   |
| Instagram                                            |
| Messenger â€“ Text and Video   Chat for Free         |
| Clash of Clans                                       |
| Clean Master- Space Cleaner   & Antivirus            |
| Subway Surfers                                       |
| YouTube                                              |
| Security Master - Antivirus,   VPN, AppLock, Booster |
| Candy Crush Saga                                     |
| Clash Royale                                         |
| Snapchat                                             |
| UC Browser - Fast Download   Private & Secure        |
| 360 Security - Free Antivirus,   Booster, Cleaner    |
| My Talking Tom                                       |
| 8 Ball Pool                                          |
| DU Battery Saver - Battery   Charger & Battery Life  |
| BBM - Free Calls &   Messages                        |
| Cache Cleaner-DU Speed Booster   (booster & cleaner) |
| Twitter                                              |
| Viber Messenger                                      |
| LINE: Free Calls &   Messages                        |
| Skype - free IM & video   calls                      |
| PokÃ©mon GO                                          |
| Pou                                                  |



### App sizes in Mb 

In original data, App sizes were given in Mb and kb and also some entries are also "Varies with size" for adjusting those here are the steps:

1. By applying formula I have checked if size is "Varies with devices", If so then change it to 0 for now

2. Then if the last character in size cell if it is "M" then discard just last character, but if it is k then we will remove last character and divide it by 1024 to convert it into Mb.

3. Then I have converted whole column to numbers from text.

4. So, now we have all numbers in Mb and 0 values which we took for "Varies with devices"

5. Then for those values I have checked Mean and Median values of available values but they differ with almost double margin. 

   | Values   | Item   |
   | -------- | ------ |
   | 18.15346 | Mean   |
   | 9.2      | Median |
   | 22.17119 | Stddev |

6. In confusion of taking mean or median for replacing 0 values, I just replaced all 0's with Random numbers between **0 to 100** so the overall data won't get affected. 
7. Then I plotted histogram from the data, here it is.



![1554444156128](images/app_sizes_mb.png)



> Conclusion : 
>
> We have almost 1300 apps which have size less then 3 Mb and maximum apps are between 3-6 Mb sizes,
> There are also apps with very high sizes but there numbers are low considering other sizes.

### Range of size

Starting from very small sizes from 0.008 Mb we have up to 100 Mb apps.

![1554445570971](images/app_size_range.png)





### Median App prices by category of app.

![1557316759006](images/category_median_price.png)



Here, Event category has highest value as there is only one app in Event category that is Paid and it has 109$ price. Also, **Finance related apps are costlier than other categories.**



### Median app sizes per categories.

![1557316561669](images/app_median_sizes_category.png)



Games are by far has most app sizes median values which is obvious because generally games has lot of graphics and game engines related things.

 

### App sizes Vs installation counts. [Median]

![1557322262228](images/median_install_vs_app_sizes.png)



### App sizes Vs installation counts. [Mean]

![1557322816542](images/mean_install_vs_app_sizes.png)



**Hence, with Increasing app sizes also increase app counts.**



### App price Vs install counts. [Median]

![1557325929886](images/median_install_vs_price.png)



### App price Vs install counts. [Mean]

![1557327031850](images/mean_install_vs_price.png)



Hence, With increasing app price installation counts will be less, as there will be limited users who will install costly apps.



------

**Note:**

These kernels on kaggle for this specific dataset I found useful and elaborative.

<https://www.kaggle.com/lava18/all-that-you-need-to-know-about-the-android-market>

<https://www.kaggle.com/akashram/google-play-store-data-exploration-baseline>







