# vocabulary_app
One can never truly learn enough, especially with languages. Even after years and years of perfecting my English skills I often find myself looking up words and expressions when reading books or articles. While immediate searches are useful, I felt the need to devise a method to gather these newfound terms and track my progress of language comprehension. This approach offers me a collection of words to review and eventually commit to memory. Simultaneously, it serves as a subtle nudge to delve into more challenging reads to enrich my vocabulary.

The developed platform uses the following components:

- Google Sheets
- Google Sheets API
- One Python Service
- Two Java Services
- gRPC
- Firebase
- An android app
- Docker
- Google Cloud's Container Registry
- Google Cloud's Compute Engine
- Big Query
- Google's Data Studio


# Overview
To generate the data the platform needs I input new words I encounter in my reading material into a Google Sheet. Every X minutes, a Python service interacts with the Google Sheet API to fetch the day's entries. This service then communicates via gRPC with a Java backend that temporarily holds these words and stores them (a copy) in BigQuery. A second Java application checks with the first one every X minutes to count new word entries. If no new words have been added, an Android app I developed sends a reminder about the lack of new word entries. But if I've added words to the Google Sheet, the app sends a congratulatory notification. These notifications are powered by Firebase Cloud Messaging. 
The three services are bundled in a Docker image stored in Google Cloud's Container Registry. This image runs on a standard Compute Engine instance. For data analysis, I execute a few queries on BigQuery and visualize the results using Google's Data Studio.

