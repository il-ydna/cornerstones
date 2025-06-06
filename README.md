# cornerstones

[![Our Demo Video!](https://img.youtube.com/vi/OhO3-RLJv2k/hqdefault.jpg)](https://www.youtube.com/watch?v=OhO3-RLJv2k)

This project had a unique problem to tackle: how do we find patterns in our user base using only data about the places they’ve visited?  
	We believed from the beginning that utilizing the embeddings in some way was our best bet. If the good people at Corner have done their due diligence, a strong majority of the information that could be gleaned from the other columns in the dataset is already wrapped up in the vectors. However, thirteen dimensions felt quite unwieldy. We needed to crunch down the data space into something more manageable. All figures used in this report are from the final version of the ipynb, so feel free to check them out in greater resolution there. 

![][image1]![][image2]  
**Fig 1: tSNE and PCA dimensionality reduction into two dimensions**  
	We first tried both tSNE and PCA on the vectors, collapsing the data space into two dimensions. We wanted to get a lay of the land and see what kind of relationships may be present in our data, and a 2D space is easily visualized.  
	However, we felt that two elements per restaurant wasn’t enough to capture the nuances of a location that Corner clearly cares about, so we upped the number of dimensions to four. Not visualizable in all its glory, but easily broken down into understandable 2D graphs (you will see why this is important soon).  
We ran our PCA to break down the location data into four dimensions and normalized the scores (also important later), which is visualized below as six different relationship graphs between the four axes.	  
![][image3]  
**Fig 2: 2D Relationship Graphs between the Vibes in 4D space**  
We called these axes “vibes” for the cute marketable name, so if I use the word vibe in this report that is what I’m referring to. Taking a look at these grapes and some of the restaurants that were on the extremes of these axes we began to look for possible interpretations of these vibes. We eventually landed on four factors: Yum factor, Glow factor, Spark factor, and Spice factor in descending size of principal component.   
It was clear looking at our 2D graphs that the largest principal component had to do with food. Places with negative Yum were landmarks, libraries, and thrift stores while positive yum was almost exclusively restaurants and sweet shops.   
The second principal component we called Glow to refer to atmosphere as well as the usual time of day that they’d be visited. Low Glow scores were dominated by cafes, which we’d usually associate with bright natural light and sunny mornings. The most represented kind of location in the higher glow scores were bars and clubs. Ergo, nightlife stuff.   
Next is Spark, which we interpreted to mean surprise factor. High Spark locations were places like thrifts and antique stores where you’re almost gambling. You show up to be surprised by the awesome pull you find in a bin. On the low end are, again, cafes. People usually don’t go to cafes to be surprised. They go in, order the usual, and get to work or read a book.   
Finally we have Spice. On one extreme is your European fare (think Pizza and Steakhouses) while the other pole had sushi, hot pot, boba and the like. This one is a measure of how many people go there seeking some kind of adventure or new experience.   
Once we’d fully digested what each location means, we then sought to calculate how the places a person has visited informs us about their personal vibes.  
![][image4]  
**Fig 3: Raw calculated Vibe scores**  
	We opted for a weighted sum, with favorites and dislikes pulling the scores heavily while visited and want-to-tries gently pulled up the sum. We then normalized the scores so that they’d sit on the same scale as the locations they were derived from. This lets us cluster users and locations in the same way later down the line.We also used these Vibe scores for a different purpose: to create a fun shareable personality type like the the Myers-Briggs Type Indicator (MBTI) test.   
![][image5]![][image6]  
**Fig 4: Frequencies of personality in the dataset**  
	The most common personality type on Corner according to our models is someone who lives to hang out and shop, who goes out at night, is probably a regular at a cafe, but likes to go out and try food from many different cultures.   
![][image7]  
**Fig 5: User Vibe Scores Overlaying Location Vibe Scores**  
	The final piece of analysis (and probably the most actionable) is shown above in figure 5\. Remember how we scaled our vibe scores so that users and locations can align? Here is the payoff for all that trouble. We can take any user and put them on the map. Not a street map where venues are placed by location, but a 4D map where they are placed by how similar they are. A BSAL (someone who loves eating, enjoying the sun, and is a bit tired of getting “the usual”) would probably love to find new cafes to explore. We can easily find places that suit his vibe by seeing what places are in their “neighborhood” on the 4D map.   
	The Corner app could go even further, connecting people with similar personality types so that they can take over a booth of a local dive bar together or try to forget how much they’re paying for omakase. We’re very proud of the vibe system we created, and hope you see the value it can bring in categorizing users and bringing them together\!
