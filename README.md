# FinalProject Thai Music mood analysis
An analysis of Thai music from Spotify  mood-based playlists  using machine learning methods

# Background
	The emotion or mood of music affects the listener in various ways. Nowadays people listen to music on streaming services like Spotify. 
On streaming services, a playlist is a selection of similar songs customized based on listener preferences. 
Often, those playlist’s names contain words or phrases that express the emotion of music.

# Dataset
The following data is obtained from Spotify’s mood-based playlists using the spotipy Python library.
920 songs 
10 playlist: ความคิดถึง (missed), 10ปีกับรักแสนเศร้า(sad), ร้องไห้หนักมาก(cry), เป็นท้อ(discourage), เพลงรักไม่เคยลืม (feeling love), 
	     ฟังเพลินตอนทำงาน (focused), อารมณ์ทะเล (relaxed), เพลงไทยสายชิลล์ (chill-out), เหนื่อยนักพักก่อน (tired) and ชิลล์ฮอป (chill-hop)
10 audio features: danceability, energy, key, loudness, mode, speechiness, instrumentalness, liveness, valence, tempo

# Methods
	Classification model
	- Label each song by using their name of playlist as the mood label 
	  Split dataset into training set (70%)  and test set (30%)
	  Run and evaluate models by starting from any 3,4 or 5 labels
	Clustering analysis
	- Drop label column and rescale data  into the range [0,1]
	  Perform K mean clustering by setting number of cluster (K) be 3,4,5
	  Create clustering profiles 
      
# Results
	Result from classification
	- As the number of labels increases, the model's performance decreases (table 1)
	- Random Forest yielded 0.81 accuracy as the best performance with 3 labels : ชิลล์ฮอป (chill-hop), 10ปีกับรักแสนเศร้า(sad) and อารมณ์ทะเล (relaxed)
	Result from K-mean Clustering 
	- As the number of clusters (K) increases, the tightness within the cluster decreases. This effect the similarity within each cluster
	- K = 3 yield the best quality of clustering 
	Various characteristics, such as danceability, valence, and tempo, differ between each cluster 
	- Cluster 0 : low valence, low tempo average energy and danceability
	- Cluster 1 : high valence, low tempo average-high energy and high danceability
	- Cluster 2 : average-low valence, high tempo average energy and low danceability
  	Mood label vs cluster  
	- Every cluster lacked the ability to clearly distinguish one mood label from another, which means that one mood is spread across many clusters.
	- If we focus only on the majority of songs in each mood, 
	- we found that most songs from อารมณ์ทะเล (relaxed), เพลงไทยสายชิลล์ (chill-out), เป็นท้อ(discourage) and ฟังเพลินตอนทำงาน (focused) are grouped into same cluster.
	  ความคิดถึง (missed),  เพลงรักไม่เคยลืม (feeling love) and เหนื่อยนักพักก่อน (tired) are also grouped into same cluster.
	  and ร้องไห้หนักมาก (cry) and 10ปีกับรักแสนเศร้า (sad) are also grouped into same cluster.
# Discussion 
  In this project, we collect 920 Thai songs from 10 different playlists created by Spotify and their audio data from Spotify web API. 
It is worth noting that these playlists' names convey a variety of emotions which was used as the emotion label for each song in those playlists. 
We developed music emotion classification models using various machine learning techniques. Random Forest yielded 0.81 accuracy as the best performance. Moreover, 
we noticed that Random Forest worked best with only 3 or 4 emotion labels. Later, we also notice similar results by using K Mean clustering technique. 
We conclude that based on audio data, those 10 playlists have similar patterns and can be grouped into only 3 collections. 

    
    
    
    
