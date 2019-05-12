---
layout: post
title: Create free web map application using Google services and other free and open source tech
image: /img/about_img/loc.png
---

This is a tutorial on how to create deploy a simple web application using free services from Google and other open source solutions. I created a campus map for UPLB
since it does not exist at the moment. You can access it [here](https://project001-215910.appspot.com/?fbclid=IwAR3WkYDRTz8ydS5_PPOHr7BRUstVIvZ5QnKq4XCPsmXIROvCwMGn3YO-qKc) if you want to have a look!

Let' Start!

<p>Requrements<br>Leaflet, Python Flask, Google API (StreetView, Maps), OSM data, Mapbox basemap token, locations from OSM overpass turbo API, </p>

Create a new instance in GC

Log in to GC console
virtualenv env
source env/bin/activate
git clone https://github.com/mgmanalili/uplb_campus_map_beta.git
cd uplb_campus_map
pip install -t lib -r requirements.txt

gcloud init
gcloud app deploy
select 2 for South-east asia
gcloud app browse

(not working for venv)
pip install -t lib -r requirements.txt --user	

![uplb1](/img/uplbcm1.png)
![uplb1](/img/uplbcm2.png)