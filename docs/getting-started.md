# Getting Started

To get started with Crawl3, the first step is to have Go installed. You will need Go > 1.7.
You can find out how to install Go at there website <a href="https://golang.org/doc/install" target="_blank">golang.org/docs/install</a>
and install the latest version for your operating system. Make sure that your go folders bin directory is in your path.

Once you have Go installed, you can go get the application

``` 
go get -u github.com/samjohnduke/crawl3/...
```

This installs a few applications into the $GOPATH/bin directory. These include c3-crawler c3-crawler-client, c3-schedular and c3-aggregator. 
These are the default binaries. They use the Nats message bus to communicate. The c3-crawler embeds a Nats server, as it is the only required piece. You can build your own crawler and use an external bus.
## Starting the minimal crawler 

To start the minmalist web crawler turn on the c3-crawler 

```
c3-crawler
```

To test that it works correctly run the client using the c3-crawler-client.

```
c3-crawler-client https://google.com/
```

If its all setup correctly, the client should output a list of crawl data. 

## Using the schedular and aggregator

Getting the schedular started requires only running the c3-schedular binary 

```
c3-schedular
``` 

This schedular will attempt to visit every page for added websites, when added via the
the schedular client. It will respect the website and visit pages once every 5 seconds,
per domain.

To get the aggregrator going, we have used ArangoDB for storing and quering data. Read more about this decision [here](/aggregator/)

For that we need to install the database. Instructions can be found on there [website](https://docs.arangodb.com/3.3/Manual/GettingStarted/Installing/). 

Once it has been installed, you can start the c3-aggregator 

```
c3-aggregator
```

The aggregator has a web interface that can be accessed at `localhost:7778`. You can then query the data and create reports.

Continue on to read about each of the pieces function and how to use them to build your own web crawler