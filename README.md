# alexa-wolfram-alpha

An example Alexa Skill to query Wolfram Alpha, written in Python.

## Dependencies

- An [AWS account](https://console.aws.amazon.com/console/home)
- A (free) [Wolfram Alpha API
  AppID](https://developer.wolframalpha.com/portal/apisignup.html)

## Quick Start

1. Create an [AWS Lambda](https://console.aws.amazon.com/console/home) function
   using alexa-wolfram-alpha.py as the code
   - You can follow the [official Amazon
     instructions](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/developing-an-alexa-skill-as-a-lambda-function)
     to give you a hand
   - You **must** put your Wolfram Alpha AppID into the `ask_wolfram_alpha`
     function, currently line 119
   - You *should* uncomment the block in the `lambda_handler` function and
     insert your `applicationId` to only allow requests coming from your
     `applicationId`
   - You can use `test_event.json` as your test template
1. Create a new [Alexa
   Skill](https://developer.amazon.com/edw/home.html#/skill/create) using
   `intent_schema.json` and `sample_utterances.txt`
1. **Don't publish** the skill (because it includes your personal Wolfram Alpha
   API AppID), leave it in development mode
1. Test that it's working from the web interface during the creation of the
   skill
1. Test that it's working with your Echo

## Development

Feel free to fork and hack on this, but keep in mind that the code in the repo
shouldn't include your AppID. Unfortunately, it looks like there's no particularly simple way
to set / get this kind of value from the AWS environment -- open an issue if
I'm wrong about this.

The `setup.cfg` file is just in case you have a [homebrew](http://brew.sh/)
installed python2 and want to include other 3rd party libraries in your code,
in which case you have to upload a zip of your code as the lambda function. To
do so, from your root directory do something like:

1. `pip2 install LIBRARY_NAME -t .`
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
