# Introduction

The Crawl3 Web Crawler is a modular and distributeable web crawler capable of
fetching, extracting and storing the results. It is written in Go and has been
designed to enable extensibility without sacrificing scalability.

I wrote Crawl3 becasue I needed a platform on which to add to and extend over time,
but without having everything built into one executeable. With Crawl3, you can setup the
core and then configure components and plugins later, for maximum flexibility.

## Components

There are 3 core components. The crawler, the schedular and the aggregator. 
Each component is responsible for only it's piece, and can each be run separatly.

The __Crawler__ consists of a distributer and one of more (configurable) workers. Unlike
many web crawlers, the dispatcher only cares about the queue that it has and arranges
work to be carried out as fast as possible, without care for if that is a wise idea.

Crawlers can run over any transport (such as http or a message bus) and are the only
required piece of the puzzle. As a user of crawl3, you can do everything with just this
piece.

The __Schedular__ is responsible for managing the process of actually crawling the website.
Its main function is to send out url crawl requests to the crawler that will perform and extraction
of a webpage. By default it fires of one URL request per second and enqueues all urls found on each
page, but the schedular is designed to be extended and can take different actions.

The __Aggregator__ listens to the crawler for successful extractions and records the data. 
It provides a transformer interface for loading data as well as a query interface for getting
the data at a later point in time.

## Quick Start
With Go >= 1.7 installed, go get the application

```bash
go get -u github.com/samjohnduke/crawl3/...
```

and then run the crawler.

```bash
c3-crawler
```

To extract data from a url, use the included c3-crawler cmd client. 

```bash 
c3-crawler-client https://google.com
```

This will write to the terminal some extracted information such as on page links, microdata and 
html meta tags (for open-graph data). By writing custom extractors you can add data you want to this list.

To read more information on what is going on read the [Introduction guide](/crawler)