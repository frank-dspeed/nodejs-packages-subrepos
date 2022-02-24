# Example that Demos how to send Voicemails via Tropo API

This app is designed to replace your GSM phone's voicemail. Instead of a
phone-based voicemail inbox, messages are transcribed and emailed with a link
to the audio file.

## Tropo migration timeline
Tropo stated that the wind-down of their services and support began in October 2018 and would continue in phases. Tropo has notified all of their contracted customers, and their developer program and credit card customers have received or should expect a notification covering timelines and next steps.

To migrate your communication applications without any interruption, we recommend migrating your logic to Twilio as soon as possible. This guide details how to migrate from Tropo's SMS or Voice APIs to Twilio.

## Requirements

* [Heroku](http://heroku.com) account
* <s>Tropo http://www.tropo.com account</s>
* [Twilio](http://www.twilio.com) account
* FTP server with HTTP access
* GSM phone with call forwarding

## Setup

### Heroku
```
    git clone git@github.com:titanous/tropo-voicemail.git
    cd tropo-voicemail
    heroku create
    heroku addons:add sendgrid:free
    heroku config:add EMAIL=you@email.com
    heroku config:add VOICEMAIL_URL=http://yourserver.com/voicemail/
    git push heroku master
```

### <s>Tropo</s>

Create a new application on Tropo, and point it to a new Hosted File with the
contents of `tropo-voicemail.rb`. Make sure you change the constants at the top
of the file to be real values. The FTP URL may not match the HTTP URL given
above (you may need a `public_html`).

You now have two options. If you are in the US, then you can add a free USA
Domestic number. Note that you probably want a number in your local calling
area. If you aren't in the US or couldn't find a local number on Tropo, then you
should get a SIP DID from a company like [Voip.ms](http://voip.ms/) and forward
it to the Tropo SIP URI.

### Cell Phone

The last step is to use some GSM feature codes to setup conditional call
forwarding. Dial each of these numbers on your cell phone and press Send:

    *67*TROPO_PHONE_NUMBER# (forward if busy)
    *61*TROPO_PHONE_NUMBER# (forward if not answered)
    *62*TROPO_PHONE_NUMBER# (forward if out of reach)

The phone should show a message after each that says something about the
conditional call foward being set. If for any reason you need to disable these
forwards, use these codes:

    ##67#
    ##61#
    ##62#

## Copyright
(c) ECMAScript Version - 2010+ Frank Lemanschik; Licensed under the https://github.com/frank-dspeed/licenses / license, see `LICENSE`
(c) Inital Ruby Version - 2010 Jonathan Rudenberg; Licensed under the MIT license, see `LICENSE`
