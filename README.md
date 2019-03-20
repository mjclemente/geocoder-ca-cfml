# Geocoder.ca CFML
A CFML wrapper for the [Geocoder.ca API](https://geocoder.ca/?premium_api=1), used for address geocoding in the United States and Canada.

*Feel free to use the issue tracker to report bugs or suggest improvements!*

### Acknowledgements

This project builds on a CFML API framework built by [jcberquist](https://github.com/jcberquist). Consequently, it is also licensed under the terms of the MIT license.

## Table of Contents

- [Geocoder.ca CFML](#geocoderca-cfml)
    - [Acknowledgements](#acknowledgements)
  - [Table of Contents](#table-of-contents)
  - [Quick Start](#quick-start)
  - [Reference Manual](#reference-manual)
- [Questions](#questions)
- [Contributing](#contributing)

## Quick Start
Looking to quickly locate some addresses; here it is.

```cfc
geo = new geocoderca.geocoderca( authCode = 'xxx' );

zipInfo = geo.locate( '95014' ).data;

writeDump( var='#zipInfo#' );
```

Note that you can also provide the `authCode` via the `GEOCODERCA_AUTH_CODE` environment variable. The `authCode` is not required to use the API/wrapper, but there are restrictions/limitations to the free tier.

## Reference Manual
While the API itself can return output as JSON, JSONP, or XML, this wrapper is current hardcoded to use JSON. The available parameters and their descriptions are outlined in the [API documentation](https://geocoder.ca/?premium_api=1).

#### `locate( required string input, struct params = {} )` <!-- omit in toc -->
Passes the `input` in as the API's `locate` param. As the docs explain, this "may be a street address, an intersection, a zip code, an ip address or any other combination of location entities. For example 330 metcalfe ottawa or metcalfe & wellington ottawa"

Params may be passed in as a struct of options, or as named arguments, i.e., you may can format calls as `geo.locate( input = 'M5H 3W4', showcountry = 1 )`

#### `scantext( required string input, struct params = {} )` <!-- omit in toc -->
Passes the `input` in as the API's `scantext` param. As the docs explain, this is "free form text containing locations. For example: This and That and the Other street in Porters Lake Nova Scotia". Honestly, I've had a hard time figuring out the point of the functionality, and it doesn't seem to behave consistently. But here it is.

Params may be passed in as a struct of options, or as named arguments, i.e., you may can format calls as `geo.scantext( input = 'This and That and the Other street in Porters Lake Nova Scotia', geoit = 'csv' )`

#### `geocode( struct params = {} )` <!-- omit in toc -->
A general wrapper for manually using all api parameters. You can manually pass the parameters from the API documentation into this method to use the API.

# Questions
For questions that aren't about bugs, feel free to hit me up on the [CFML Slack Channel](http://cfml-slack.herokuapp.com); I'm @mjclemente. You'll likely get a much faster response than creating an issue here.

# Contributing
:+1::tada: First off, thanks for taking the time to contribute! :tada::+1:

Before putting the work into creating a PR, I'd appreciate it if you opened an issue. That way we can discuss the best way to implement changes/features, before work is done.

Changes should be submitted as Pull Requests on the `develop` branch.
