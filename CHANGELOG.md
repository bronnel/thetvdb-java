Change Log
==========

## 2.2.0
_2019-11-27_

* `Series`: add `poster` and `fanart` field.
* `SeriesImageQueryResult`: add `language` field.
* No longer sends `Accept` header with API version, never had any effect.

## 2.1.0
_2019-02-07_

* For the `com.uwetrottmann.thetvdb.entities` package return values and fields are now annotated nullable.

## 2.0.0
_2018-12-07_

* Support searching (looking up) series by slug.
* Produce Java 8 bytecode. For Android this requires Android Gradle Plugin 3.2.x or newer.
* For the root package (this specifically excludes entity classes) return values and fields are now non-null unless 
  otherwise annotated.

## 1.6.1
_2018-08-10_

* Add `slug` to `Series`. This can be used to build the new TheTVDB web links.
* Actually request API `2.2.0`. However, value is ignored by TheTVDB despite docs saying otherwise.

## 1.6.0
_2018-07-26_

* Drop `Episode.FullEpisode` as `/series/{id}/episodes` now also responds with full episode data. Thanks @mlaggner!
* Add `languageId` to `SeriesImageQueryResult`. Thanks @mlaggner!
* Update `retrofit` dependency to `2.4.0`.

## 1.5.0

_2017-08-11_

* Add `@Nullable` annotations through a compile-time dependency on the JSR 305 annotations. **Warning: source-incompatible for Kotlin users.**
* Update `retrofit` dependency to `2.3.0`.
* Add `firstAired` param to `episodesQuery`. Thanks @mlaggner!

## 1.4.2

_2017-05-06_

* Update `retrofit` dependency to `2.2.0`.

## 1.4.1

_2017-05-06_

* Change `Episode#lastUpdated` and `Series#lastUpdated` to `Long` to support dates beyond 2038.
* Use `Double` for `episodes/query` `dvdEpisode` parameter.
* Add details about what is returned if translations are missing to `series()` and `episodes()` call.

## 1.4.0

_2017-01-15_

* Add support for updates method. Thanks @mattkranzler5!
* Add support for series actors method. Thanks @mattkranzler5!

## 1.3.0

_2016-11-23_

* Consistently name entity and response classes.
* `Series`: Add `siteRatingCount`. Use `Integer` for `lastUpdated` (was `Long`).
* `SeriesImageQueryResult`: Add `count` to `ratingsInfo`.
* `Episode`: `lastUpdated` is returned with basic episode data, `directors` list instead of `director`, 
  full data added `siteRatingCount`, use `Integer` for `seriesId` (was `int`).
* Add `errors` field to `EpisodeResponse`, `EpisodesResponse`, `SeriesResponse`.
* Update retrofit to 2.1.0.
* Removed built-in logging support. Simply subclass `TheTvdb` and add your own logger by overriding `setOkHttpClientDefaults()`.
  See `BaseTestCase` for an example.

## 1.2.0

_2016-05-06_

* Use version 2.1.0 of the TheTVDB API.
* Update to retrofit 2.0.2.
* Add `/episodes/{id}` endpoint.

## 1.1.2

_2016-04-20_

* Add additional properties to `BaseEpisode` entity (`airedSeasonID`, `firstAired` and `language`).

## 1.1.1

_2016-04-20_

* Make `TheTvdbInterceptor` handling publicly accessible as well.

## 1.1.0

_2016-04-15_

* Rename `Series` service to `SeriesService` to avoid naming conflict with the entity `Series`.
* Make using a shared OkHttp client easier: `TheTvdbInterceptor` now only interecepts if the host is `api.thetvdb.com`.
  `TheTvdbAuthenticator` response handling is publicly accessible through its `handleRequest()` method so it can be used
  in your own authenticator implementation.

## 1.0.2

_2016-04-14_

* Do not retry `/login` requests, fail immediately if `401 Unauthorized` is returned.

## 1.0.1

_2016-04-09_

* Remove deprecated `seriesId` from `Series` entity. Would return empty string instead of integer if not available, so
  remove it altogether. 

## 1.0.0

_2016-04-08_

* Initial release supporting TheTVDB API v2.0.0 final.
* Many endpoints are still incomplete, pull requests are welcome.