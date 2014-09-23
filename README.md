# ![XPRMNTL](/images/ghLogo.jpg)
XPRMNTL (read "Experimental") is an application of [Code-based Feature Flags](http://en.wikipedia.org/wiki/Feature_toggle) with a web-based configuration via a dashboard and API.

### Why is this a thing?
XPRMNTL exists for a number of problems that needed a solution:

1. Feature Flags (Intra-documentationally referred to as "Experiment" or "feature")
  - Gain: Allows us to keep all code in "master" without it being "client-facing"
  - Alternative: version control branches
2. For distributed systems
  - Gain: Allows us to keep all of our instances in sync, where memory is not shared
  - Alternative: a file in the repository that all components use for building
3. That can be quickly changed
  - Gains:
    - Allows rapid enabling/disabling of features (rapid roll-backs on error)
    - Allows gradual scaling that isn't heart-breakingly slow
  - Alternatives:
    - Deploy for changes (5 - 90min)
    - Environment variables for experiments
4. By non-technical people (optionally)
  - Gain: Allows us to wrap metrics around our experiences and allow product ownership to deliver
  - Alternatives:
    - Developer-only configuration and deployment
    - Roll-out meetings
    - After-hours development emergencies for roll-backs
  - Warnings:
    - Make sure testing is done and monitoring is in place if development isn't involved in delivery
    - This is not a use-case for technical replacements (db replacements, etc), but may be for lean startup methodologies of "Build-Measure-Learn"

## Components

### Dashboard & API
The [XPRMNTL dashboard](https://github.com/XPRMNTL/feature) is a UI for the API, which allows you to:

1. Select Github repositories to add to Experiments
2. Modify experiment configuration

The current implementation requires a Github Organization with repositories for the code and uses Github's OAuth2 strategies for authentication/authorization.

### Clients
The XPRMNTL client is a language-specific client for "announcing" your experiment configuration and getting back your experiment settings.


Currently only a Node.js client exists. I'd love to see more...

1. [Node.js Client](https://github.com/XPRMNTL/feature-client)
