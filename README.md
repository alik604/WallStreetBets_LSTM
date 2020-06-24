<!-- [![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url] -->

[![LinkedIn][linkedin-shield]](https://www.linkedin.com/in/alik604/)



<!-- TABLE OF CONTENTS -->
## Table of Contents

* [About the Project](#about-the-project)
  * [Built With](#built-with)
* [Getting Started](#getting-started)
  * [Prerequisites](#prerequisites)
  * [Installation](#installation)
* [Roadmap](#roadmap)
* [Contributing](#contributing)
* [License](#license)
* [Contact](#contact)




<!-- ABOUT THE PROJECT -->
## About The Project

The simultaneous rise in social media and discount brokerages has spurred the proliferation of online communities dedicated to investing and trading on the stock market. The most popular of these communities is the subreddit r/wallstreetbets (WSB). At over 1 million active subscribers, it is the fourth most popular subreddit at this time. Bloomberg Businessweek recently featured the subreddit in an article describing the message boards ability to reshape the options market and spark stock rallies. With such a large following and arguable influence, the question arises as to whether sentiment on the site can be successfully used as a predictor of stock performance.


### Data
Stock Data:
Wharton Research Data Services (WRDS), a division of the Wharton School of Business at the University of Pennsylvania, is a highly-regarded source in academic research and has a dedicated quality control analyst at the NYSE. Once granted access to their database, we were able to create a hourly stock price dataset from their consolidated Millisecond Trade and Quote (TAQ) dataset. Our dataset consists of hourly stock prices for Amazon, SPY,  Boeing, SPY (S&P), and Tesla from Jan-01-2017 to Nov-31-2019. The selection criteria was most mentions for 2019 with Amazon and SPY surpassing the other 3.

r/wallstreetbets data from reddit:
Pushshift is the largest publicly-available Reddit dataset containing both comments and submissions. We use Pushshift Comments dataset for r/wallstreetbets from Jan-01-2017 to Nov-31-2019.

GloVe - Global Vectors for Word Representation:
GloVe is an unsupervised learning algorithm for obtaining word vector representations from a word corpus. The GloVe project has several publicly available pre-trained word vector datasets. We chose to use the Magnitude versions of GloVe Twitter (2 billion tweets containing 27 billion tokens, with a vocabulary size of 1.2 million) for 25-dimensional word embeddings and GloVe Common Crawl (web archive containing 840 billion tokens, with a vocabulary size of 2.2 million) for 300-dimensional word embeddings.
Link : https://nlp.stanford.edu/projects/glove/

### Methods
We embedded each comment by averaging the word vectors of each word in the comment to form a document vector. This generated 2 embeddings, a 25-dimensional embedding and a 300-dimensional embedding using the respective GloVe datasets.

This CPU-bound task alone takes several days on a single machine for one successful run. To speed up this computation, we parallelized the task with ~60 "idle" Computing Science Instructional Laboratory (CSIL) machines with 12 CPU cores each. In addition to the standard document vectors, we appended score, gildings, and word count of each post as additional features.

The word vectors were then aggregated over hours and days separately creating 2 final datasets GloVe datasets, which was then joined with our stock ticker prices.  

### Results
From our investigation we found that time series forecasting is aided by an increased granularity to the data. The LSTM architectures we tested benefited from both a finer stock price aggregation, and also from a shorter sequence length. The latter is particularly interesting because many technical indicators use a sequence length of about 30 time-steps. In terms of baselining, we found our LSTM to be competitive against some non neural network based models we evaluated.  

### Future work
In terms additional impairments which can be directly added to our work, there is both benefit to be gained with both more tuning and data. On the tuning side, more hyperparameter optimization could be conducted and a more powerful model such as a LSTM with attention may be employed. While on the data front, additional features sure as technical indicators, namely the relative strength index, as well as key securities’ features such as dividends, volume, business sector, could all be potentially beneficial.

Averaging the constituent word vectors of a document to form a document vector is a primitive approach which loses information about word order and importance. Future work should explore the use of a trainable neural network document vector model such as Doc2Vec which extends word vectors to documents in a more sophisticated fashion.

A future document model could be trained specifically on finance-related news and social media and could incorporate special handling of stock tickers such as “TSLA.” Such a finance-specialized model could provide better results.

### Built With

* [GloVe](https://nlp.stanford.edu/projects/glove/)
* [WRDS](https://wrds-www.wharton.upenn.edu/pages/about/)
* [Pushshift](https://pushshift.io/)
* [TensorFlow 2](https://www.tensorflow.org/)



<!-- GETTING STARTED -->
## Getting Started

To get a local copy up and running follow these simple steps.

### Prerequisites

This is an example of how to list things you need to use the software and how to install them.
* Install dependencies
```sh
common ML packages
```

### Runing

1. Clone the repo
```sh
git clone https://github.com/alik604/This_repo.git
```
2. Open notebook
```sh
jupyter notebook
```


<!-- ROADMAP -->
## Roadmap

See the [open issues](https://github.com/alik604/repo/issues) for a list of proposed features (and known issues).



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.



<!-- CONTACT -->
## Contact

[Khizr Ali Pardhan](https://github.com/alik604/Readme) - [Email](kpardhan@sfu.ca) - [@alik604](https://twitter.com/alik604)

David Pham - [Email](dpa35@sfu.ca) 

Winfield Chen







<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=flat-square
[contributors-url]: https://github.com/othneildrew/Best-README-Template/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=flat-square
[forks-url]: https://github.com/othneildrew/Best-README-Template/network/members
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=flat-square
[stars-url]: https://github.com/othneildrew/Best-README-Template/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/Best-README-Template.svg?style=flat-square
[issues-url]: https://github.com/othneildrew/Best-README-Template/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=flat-square
[license-url]: https://github.com/othneildrew/Best-README-Template/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=flat-square&logo=linkedin&colorB=555
