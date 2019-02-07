# WhosInBot Clojure

[![Build Status](https://travis-ci.org/tonylpt/whosinbot-clojure.svg?branch=master)](https://travis-ci.org/tonylpt/whosinbot-clojure)

This is an implementation of the [WhosInBot](https://github.com/col/whos_in_bot) in Clojure.


## Prerequisites
- [Leiningen](https://leiningen.org/#install)
- [Docker Compose](https://docs.docker.com/compose/install/)


## Development
1. [Create a new Telegram bot](https://core.telegram.org/bots#creating-a-new-bot) and obtain the authorization token.
2. Copy `resources/config.template-dev.edn` to `resources/config.edn` and fill in the Telegram token.
3. Run tests:

        lein test
        
4. Start the development PostgreSQL:

        docker-compose up db
        
5. Apply database migrations:

        lein run -- --migrate
        
6. Run the app locally:

        lein run
        

## Run from JAR
1. Make sure `resources/config.edn` has the correct values.
2. Build the JAR:

        lein uberjar

    The standalone JAR will be saved at `target/uberjar/whosin.jar`.
    
3. Apply database migrations:
       
        java -jar target/uberjar/whosin.jar --migrate
 
4. Run the app:        
       
        java -jar target/uberjar/whosin.jar
        
         
## Usage
Refer to the original [WhosInBot](https://github.com/col/whos_in_bot/blob/master/README.md) for the full description.

### Basic Commands
- `/start_roll_call` - Start a new roll call
- `/start_roll_call Some cool title` - Start a new roll call with a title
- `/end_roll_call` - End the current roll call
- `/set_title Some cool title` - Add a title to the current roll call

### Attendance Commands
- `/in` - Let everyone know you'll be attending
- `/in Some random comment` - Let everyone know you'll be attending, with a comment
- `/out` - Let everyone know you won't be attending
- `/out Some excuses` - Let everyone know you won't be attending, with a comment
- `/maybe` - Let everyone know that you might be coming
- `/maybe Erm..` - Let everyone know that you might be coming, with a comment
- `/set_in_for Dave` - Let everyone know that Dave will be attending (with an optional comment)
- `/set_out_for Dave` - Let everyone know that Dave won't be attending (with an optional comment)
- `/set_maybe_for Dave` - Let everyone know that Dave might be coming (with an optional comment)
- `/whos_in` - List attendees

### Other Commands
- `/shh` - Tells WhosInBot not to list all attendees after every response
- `/louder` - Tells WhosInBot to list all attendees after every response
