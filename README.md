# trip-duration-prediction

NOTE: Folium maps are used extensively for visualization of stations, their representations used in this project and general exploratory data analysis. Since Github does not render interactive maps, click [here](https://nbviewer.org/github/meghana-holla/trip-duration-prediction/blob/main/TripDurationPrediction.ipynb) to open `TripDurationPrediction.ipynb` on nbviewer and be able to visualize them!

### Prediction of trip duration in bicycle sharing systems:

This project examines trip duration prediction in bicycle sharing systems without using trajectory data. Work done in this project is two-fold:

1. Usage of coarse-grained station representation for predictive modeling as opposed to traditionally employed fine-grained station-level representation
2. Importance of destination (drop-off/check-in) station in trip duration prediction. Conversely, how much information does source (pick-up/check-out) contribute in duration prediction?

#### Coarse-Grained Representation for Stations - A Means of Problem Simplification:
The average distance between a station and its nearest neighbor is ∼ 230 meters. Hence, the usage patterns and trends would be very similar for multiple stations. This calls for a possibility of problem simplification, where multiple nodes in a stations network could come under the same bucket. To this end, two kinds of problem simplification strategies are employed - Geographic clustering and Purpose-aware Categorization. 

Geographic Clustering: A simple and intuitive means of bringing together similar stations. This would identify possible neighborhoods and then categorize stations based on which neighborhood they fall into. 

Purpose-aware Categorization: Each bike station is assumed to serve a specific purpose based on its surroundings, i.e., a station‘s usage is heavily dependent on what is around it. Furthermore, the usage patterns of incoming and outgoing users are heavily governed by its location. This paves way for a more meaningful means of grouping stations - Purpose-aware Categorization. [Points of Interests](https://data.cityofnewyork.us/City-Government/Points-Of-Interest/rxuy-2muj) dataset is used as baseline data for deducing the major purpose of each station. Refer to the code and/or report for additional details!

One of the advantages of employing coarse-grained representation is from a system's (Eg: NYC CitiBikes) perspective. This representation makes the prediction system more change-agnostic (or adaptable to addition of newer stations). To elaborate, a new station would most certainly belong to one of existing geographic clusters and purpose categories, and new stations are more likely to be added than new POI categories or even geographic clusters.
