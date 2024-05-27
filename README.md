# Login Pages HTTP Client Hints Dataset

> HTTP client hint crawling data of all login pages of the 8M Tranco list websites.

This data set contains the crawled `Accept-CH` HTTP header values on all Tranco-list-related login pages from August 2022 to December 2023. You can use the data set to reproduce our study results regarding the client hint usage on the Web.

We crawled the data from three different continents (North America: Johnstown, Ohio, USA; Europe: Frankfurt and Biere, Germany; Asia: Singapore) and two different Internet Service Providers (ISP), which were Amazon Web Services (AWS) and Deutsche Telekom (DT).

## Overview

You can find the crawling data inside the `crawl_data_redacted` folder of this repository. It is subdivided into our four different crawling regions, which are also the subfolders:

- `eu_otc`: Crawling data from Biere, Germany (Europe), using the DT ISP.
- `eu_aws`: Crawling data from Frankfurt, Germany (Europe), using the AWS ISP.
- `ap_aws`: Crawling data from Singapore (Asia), using the AWS ISP.
- `us_aws`: Crawling data from Johnstown, Ohio, USA (North America), using the AWS ISP.

Each folder includes the following files:

- `crawl_data_login_urls_only.csv`: Contains the responses from all crawled login URLs
- `crawl_data_clustered_third_party_urls_only.csv`: Contains the responses from requests to third party URLs that were initiated by the login URLs
- `crawl_data_trackerlist_urls_only.csv`: Contains the responses from requests to third-party URLs that were identified as trackers and initiated by the login URLs.

### General

Each data set file contains the following columns:

| Column                            | Data Type | Description                                                                                                                                                                                   | Example                            |
| --------------------------------- | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------- |
| date                              | Timestamp | Point in time when the URL was crawled                                                                                                                                                        | 2023-03-03 14:45:25.525            |
| login_url                         | String    | Uniform Resource Locator (URL) of the login URL that should be crawled                                                                                                                        | https://www.example.com/login.html |
| login_url_hostname                | String    | Hostname belonging to the crawled login URL                                                                                                                                                   | www.example.com                    |
| url                               | String    | The actual URL that was crawled. In case it differs from `login_url`, it indicates a third party request.                                                                                     | https://www.example.com/index.html |
| url_hostname                      | String    | Hostname belonging to the URL                                                                                                                                                                 | www.example.com                    |
| _Accept-CH Values (many columns)_ | Integer   | The column name shows the corresponding value that was present in the `Accept-CH` HTTP Header (e.g., `sec-ch-ua-platform`). Its value shows whether this value was present (`1`) or not (`0`) | 1 - 0                              |

## Data Creation

We used the [Tranco List from June 21st, 2022](https://tranco-list.eu/list/GZP2K/full) and visited all 8M hostnames of this list with a crawler bot to identify their login pages. We then crawled the login pages on a monthly basis and recorded the `Accept-CH` HTTP header sent by each website. For technical reasons, we had crawling gaps of one (October 2022) and two months (October/November 2023). However, the impact should be minimal (see Publication).

## Publication

You can find more details on our conducted study in the following
journal article:

[A Privacy Measure Turned Upside Down? Investigating the Use of HTTP Client Hints on the Web] (2024)<br>
_Stephan Wiefling, Marian Hönscheid, and Luigi Lo Iacono_.<br>
19th International Conference on Availability, Reliability and Security (ARES '24), Vienna, Austria

[A Privacy Measure Turned Upside Down? Investigating the Use of HTTP Client Hints on the Web]: https://nbn-resolving.org/urn:nbn:de:hbz:1044-opus-83218 

#### Bibtex

```.bibtex
@inproceedings{Wiefling_A_2024,
  author = {Wiefling, Stephan and Hönscheid, Marian and {Lo Iacono}, Luigi},
  title  = {{A Privacy Measure Turned Upside Down? Investigating the Use of HTTP Client Hints on the Web}},
  booktitle = {19th {International} {Conference} on {Availability}, {Reliability} and {Security}},
  series = {{ARES} '24},
  location = {Vienna, Austria},
  doi = {10.1145/3664476.3664478},
  publisher = {ACM},
  month = aug,
  year   = {2024}
}
```

## Note

The login URLs are redacted in the data for ethical reasons. For researchers following ethical standards, we also provide our data set of login page URLs on request. Please contact das@h-brs.de using your University email address for this purpose.

## License

This data set and the contents of this repository are licensed under the
[Creative Commons Attribution 4.0 International (CC BY 4.0)] license.
See the [LICENSE](LICENSE) file for details. If the data set is used
within a publication, the following paper has to be cited as
the source of the data set:

Stephan Wiefling, Marian Hönscheid, and Luigi Lo Iacono: A Privacy Measure Turned Upside Down? Investigating the Use of HTTP Client Hints on the Web. In: 19th International Conference on Availability, Reliability and Security (ARES '24), Vienna, Austria (2024). doi: [10.1145/3664476.3664478](https://doi.org/10.1145/3664476.3664478)

[Creative Commons Attribution 4.0 International (CC BY 4.0)]: https://creativecommons.org/licenses/by/4.0/
[Tranco List from June 21st, 2022]: https://tranco-list.eu/list/GZP2K/full
