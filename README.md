# asterisk.agi.io

Asterisk AGI for NodeJS

## Install

```
npm install asterisk.agi.io
```

### Usage

```javascript
require('dotenv').config();

var aio = require('asterisk.agi.io'),
    agi = null;

const PORT = process.env.PORT || 4573;

agi = aio.agi(PORT):

agi.on('error', function(err){
    throw err;
});

agi.on('listening', function(){
    console.log(`AGI Listening on port ${PORT}`);
});

agi.on('close', function(){
    console.log('close');
});

agi.on('connection', function(call){

    call.on('hangup', function(){
        console.log('hangup');
    });

    call.on('error', function(err){
        throw err;
    });

    call.on('close', function(){
        console.log('close');
    });

    // Answer the channel
    call.command('Answer', function(code, result, data){

        // Say Digits Sample
        call.command('Say Digits "1234" ""', function(code, result, data){

            // Say Number Sample
            call.command('Say Number "9876" ""', function(code, result, data){

                call.command('HangUp', function(){
                    // Hangup the channel
                });

            });

        });

    });

});
```

### Fork from Original Repository

This project is a fork of [asterisk.io](https://github.com/zmarius81/asterisk.io). 
Only the 'agi' implementation was utilized for this project.