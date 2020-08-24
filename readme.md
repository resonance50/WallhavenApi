# Wallhaven API for Python

[![pipeline status](https://gitlab.com/goblenus/WallhavenApi/badges/master/pipeline.svg)](https://gitlab.com/goblenus/WallhavenApi/commits/master)
[![Coverage Status](https://coveralls.io/repos/github/Goblenus/WallhavenApi/badge.svg?branch=master)](https://coveralls.io/github/Goblenus/WallhavenApi?branch=master)
[![codecov](https://codecov.io/gh/Goblenus/WallhavenApi/branch/master/graph/badge.svg)](https://codecov.io/gh/Goblenus/WallhavenApi)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/Goblenus/WallhavenApi/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/Goblenus/WallhavenApi/?branch=master)
[![Dependency Status](https://www.versioneye.com/user/projects/57b99484fc1827003bff971d/badge.svg?style=flat-square)](https://www.versioneye.com/user/projects/57b99484fc1827003bff971d)

Feel free to add an issue.

## Description

Implementation of https://wallhaven.cc/help/api (the official one)

## Dependencies

```sh
# pip install -r requirements.txt
```

## Quick Documentation

Import WallhavenApi package:

```python
import wallhavenapi
```

Initialize WallhavenApi:

```python
wallhaven_api= wallhavenapi.WallhavenApiV1()
```

If you have an account on **[Wallhaven](https://wallhaven.cc)**, you can use [api key](https://wallhaven.cc/settings/account) to access all available wallpapers:

```python
wallhaven_api = wallhavenapi.WallhavenApiV1(api_key="some_api_key")
```

## Methods

### WallhavenApiV1

* api_key {String} - your **[Wallhaven](https://wallhaven.cc)** [api key](https://wallhaven.cc/settings/account)
* verify_connection {Bool} - check ssl cert
* base_url {String} - **[Wallhaven](https://wallhaven.cc)** base api url
* timeout {Tuple(Int, Int)} - http request timeout
* requestslimit_timeout {Tuple(Int, Int)} - try to handle 429 http error. The first Int - how many times to do request, the second - delay (in seconds) between requests.

### WallhavenApiV1.search - Accessing Wallpaper information

* q {String} - query (used to filter by user, tags, ids and [so on...](https://wallhaven.cc/help/api#search))
* categories {String|List[String]} - walpaper category (located in wallhavenapi.Category)
* purities {String|List[String]} - walpaper purity (located in wallhavenapi.Purity)
* sorting {String} - how to sort results (located in wallhavenapi.Sorting)
* order {String} - sort order (located in wallhavenapi.Order)
* top_range {String} - sorting MUST be set to 'toplist' (located in wallhavenapi.TopRange)
* atleast {Typle(Int,Int)} - minimum resolution
* resolutions {Typle(Int,Int)|List[Typle(Int,Int)]} - exact wallpaper resolutions
* ratios {Typle(Int,Int)|List[Typle(Int,Int)]} - aspect ratios
* colors {String} - color to search (located in wallhavenapi.Color)
* page {Int} - page for pagination

### WallhavenApiV1.is_walpaper_exists - Check wallpaper existence by id

* wallpaper_id {String} - wallpaper id (can be obtained by WallhavenApiV1.search)

### WallhavenApiV1.download_wallpaper - Download wallpaper to file (or get data) by id

* wallpaper_id {String} - wallpaper id (WallhavenApiV1.search)
* file_path {String} - path to file
* chunk_size {Int} - chunked buffer for downloading

### WallhavenApiV1.tag - Get tag information

* tag_id {String} - tag id (can be obtained by WallhavenApiV1.search)

### WallhavenApiV1.settings - Get user settings

It works only if api_key is set

### WallhavenApiV1.collections - get collections by user name

* user_name {String} - user name

### WallhavenApiV1.collection_wallpapers - get wallpapers by user collection id

* user_name {String} - user name
* collection_id {Int} - user collection id (can obtained by `WallhavenApiV1.collections`)
* page {Int} - page

### WallhavenApiV1.my_collections - get collections of api_key user

It works only if api_key is set
