# alexa-wolfram-alpha

An example Alexa Skill to query Wolfram Alpha, written in Python (3.6).

## Dependencies

- An [AWS account](https://console.aws.amazon.com/console/home)
- A (free) [Wolfram Alpha API
  AppID](https://developer.wolframalpha.com/portal/apisignup.html)

## Quick Start

1. Create an [AWS Lambda](https://console.aws.amazon.com/console/home) function
   using `alexa-wolfram-alpha.py` as the code
   - You can follow the [official Amazon
     instructions](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/developing-an-alexa-skill-as-a-lambda-function)
     to give you a hand
   - Put your Wolfram Alpha AppID into an environment variable called "WOLFRAM_ID" and also put your Alexa Skill Identifier in an environement variable called "SKILL_ID". For help view the [documentation](http://docs.aws.amazon.com/lambda/latest/dg/env_variables.html)
   - You can use `test_event.json` as your test template
   - Consider extending the timeout beyond the default of 3 seconds (I raised mine to 10, which is likely excessive, but eliminated some sporadic errors e.g. [#1](https://github.com/n8henrie/alexa-wolfram-alpha/issues/1))
1. Create a new [Alexa
   Skill](https://developer.amazon.com/edw/home.html#/skill/create) using
   `intent_schema.json` and `sample_utterances.txt`
1. Test that it's working from the web interface during the creation of the
   skill
1. Test that it's working with your Echo

## Development

Feel free to fork and hack on this.

The `setup.cfg` file is just in case you have a [homebrew](http://brew.sh/)
installed python and want to include other 3rd party libraries in your code,
in which case you have to upload a zip of your code as the lambda function. To
do so, from your root directory do something like:

1. `pip install LIBRARY_NAME -t .`
1. `zip -r $(date +%s)-alexa-wolfram-alpha.zip .`

Also, take a look at [Amazon's official sample code for a lambda-based Alexa Skill
in Python](https://gist.github.com/n8henrie/3db1205331d0f6195b01), named
`alexa-skills-kit-color-expert-python`. (I found it very helpful to reference
but couldn't find an easy way to view the source online, so I copied it to a
GitHub Gist.)

## Acknowledgements

- <https://github.com/astrobleem/askwolfram> :: A similar project in PHP that
  helped me figure out what the intent schema and sample utterances should look
  like
