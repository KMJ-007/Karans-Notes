---
title: "Indoor Navigation using AR"
date: "2023-03-31"
tags: ["project", "Indoor Navigation"]
---

![bg](images/project/indoorAR/bg.png)

We were actually very happy by getting lost in the big campus, our campus is small but it looks maze because of it's architecture, but all weren't happy by getting lost in campus, some stranger were visiting for the first time, some students were getting late for their classes, in fact i have seen some professors getting lost, 

We had opportunity to solve this problem in hackathon, from many other problems which were too easy(like building simple chatbot, hostel management system, etc) we chose this problem, we were very excited, because we cared about it!

## Some Failed/alternative paths

We started with the thought by thinking this was going to be easy one, but after doing we realise it is going to take lot of time in research, 

Our first approach was creating a React-Native app, even after building a mvp for startup, only thing which i hate about react-native is environment setup, we were planning to use [viro-react]("https://github.com/viromedia/viro"),our team member already knew it, but problem was, even after dealing with environment setup issue, we manage to do it, and viro react was outdated, the last commit was on feb 21.

To make indoor navigation, there are mainly three ways,

1. Using BLE beacons
2. Using Wifi
3. Using GPS

## BLE beacons

BLE beacons works on bluetooth low energy technology, if you remember apple air tags, they work on ble, they constantly emit the signal, and we can detect them using our phone, we can use this to detect the location of the user, but the problem is, we need to install beacons in every room, and we need to calibrate them, and we need to calibrate them again and again, because they are not static, if our area which want to cover is small then ble beacons good, but when the campus is big, then it is not feasible, and it is not scalable, and it is not cost effective, so we decided to not use ble beacons.

![airTag](images/project/indoorAR/AirTag_Tile.jpg)

## Wifi

This is the most common way to do indoor navigation, we can use wifi to detect the location of the user, and guiding the user on the basis of that navigating the user, and in mostly big size campus, it is very common to have central wifi system, and this works the best compare to ble beacons and gps, whole application can be deployed on local area network, and after that there will be no need of internet, but guess what, they didn't allow us to access wifi, so had no other option than to use gps.

![wifi](images/project/indoorAR/wifi_indoor.jpeg)

## GPS

We used GPS for this, but the problem with GPS in closed environment is, it is not accurate, the signal constantly jumps if you are surrounded by concrete wall, for example, if you have wifi router at your home, and you put simple aluminum foil on top of it, you will notice the boost, and sometimes your phone signals also fluctuate when you are in closed surrounding, if we had got access to wifi system then we wouldn't have chosen this way, but we didn't have any other option, so we decided to use GPS, and we were very happy with the result, we were able to navigate the user, and we were able to detect the approx location.


## How we did it

<iframe width="560" height="315" src="https://www.youtube.com/embed/ynXAIiwd_1E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

We thought to use graph database, [Neo4j]("https://neo4j.com/") was the thing we come across this, cypher query language has step curve to learn, because it can provide custom query, like shortest path between two node, geo near by, in radius of, all kind of complex query which will be required, graph database will handle it, but didn't choose it, and i will explain why we didn't choose it.

## Spatial indexing

Then i come across Spatial indexing, basically Spatial indexing is a way to organize information based on where things are located in space. It's like organizing a library based on where the books are on the shelves. This makes it easier to find the information you need quickly.

For example, imagine you have a map of your city and you want to find all the restaurants within a certain area. Spatial indexing helps the computer quickly find all the restaurants in that area by organizing the information based on their location on the map.

Spatial indexing is used in many different applications like mapping, location-based services, and computer vision. It's an important tool for managing and analyzing spatial data efficiently.

almost all database supports Spatial indexing, and that's why we didn't choose Neo4j database

Mongodb also [supports]("https://www.mongodb.com/docs/v2.6/applications/geospatial-indexes/") Spatial indexing, and we already have worked with Mongodb, so we decided to use Mongodb, and we were very happy with the result, we were able to navigate the user, and we were able to detect the approx location.

and one tool which helped a lot was [geoJson]("https://geojson.io/#map=2/0/20"), we used it get whole polygon and marker location with exact latitude and longitude,

## architecture

![indoor_architecture.jpeg](images/project/indoorAR/indoor_architecture.jpeg)

as you can see in architecture diagram, we have one admin panel, where admin can upload the map, and can add the location, and can add the marker, and can add the polygon, and can add the path, and can add the building, and can add the waypoint between the two buildings connecting the path, 

admin panel is connected with backend, and backend is connected to the database, which handles all the database read write, all endpoints are define there, Spatial indexing and geo near query, also happens there

backend is also connected with the web app, which is used by the user, to calculate the distance between two lat & lan, we use Haversine formula

To calculate if the user reached the location, we constantly watch its location, and if the user is in the radius of 10 meter, then we show the user that he has reached the location, and ar.js given marker automatically increase the size, and that's how our whole app works

if you have any question, feel free to ask, i will be happy to answer


[github repp](https://github.com/knowOne08/directionCompass)

and we won special Appreciation prize!!!!

![win](images/project/indoorAR/winning.jpeg)