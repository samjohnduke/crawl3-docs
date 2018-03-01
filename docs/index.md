# Introduction

The Crawl3 Web Crawler is a modular and distributeable web crawler capable of 
fetching, extracting and storing the results. It is written in Go and has been 
designed to enable extensibility without sacrificing scalability. 

## Components

There are 3 core components. The crawler, the schedular and the aggregator. 
Each component is responsible for only it's piece, and can each be run separatly.

The Crawler consists of a distributer and one of more (configurable) workers. Unlike
many web crawlers, the dispatcher only cares about the queue that it has and arranges
work to be carried out as fast as possible, without care for if that is a wise idea. 

The Schedular is responsible for managing the 

The Aggregator 