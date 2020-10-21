# Software Engneering

## Principles

* \*\*\*\*[**Forcing Functions**](https://coderefinery.wordpress.com/2020/10/21/forcing-functions-in-software-development/) -there are some things you can do to force issues up to the surface.
  * Dig out an old or cheap phone and try to run your app on it. Any major performance bottlenecks will suddenly become obvious
  * Pretend you’re a new developer in the team1. Delete the project from your development machine, clone the source code and set it up from scratch. Gaps in the Readme file and outdated setup scripts will soon become obvious
  * Try to add support for a completely different database. Details of your current database that have leaked into your data layer abstractions will soon become obvious
  * Port a few screens from your front-end app to a different platform. For example, write a command-line interface that reuses the business and data layers untouched. “Platform-agnostic” parts of the architecture might soon be shown up as anything-but
  * Start releasing beta versions of your mobile app every week. The painful parts of your monthly release process will start to [become less painful](https://martinfowler.com/bliki/FrequencyReducesDifficulty.html)
  * Put your software into the hands of a real user without telling them how to use it. Then carefully watch how they actually use it

