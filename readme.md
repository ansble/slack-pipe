# pipe-slack

A simple util for adding slack to your CLI pipe tool chain.

## What?!

That's right! Now you can `ls -al | pipe-slack` and have the result of your `ls`
printed out in the channel you want by a bot of your choosing.

## Config

There are two ways to pass in most of the information that pipe-slack needs. The
first of them is to pass it command line arguments for channel, bot name, and 
emoji for the bot icon. That looks like this:

```
ls -al | pipe-slack my-channel my-rad-robot :robot_face:
```

The one exception here is that you still need to provide your webhook url as an
ENV var calles `SLACK_URL`. Best to just toss that in a `.zshrc`, `.bashrc`, or 
something similar right now.

While you are in there you can all specify `SLACK_CHANNEL`, `SLACK_BOT_NAME`, and
`SLACK_EMOJI` and not have to pass in anything at all. Letting you simplify the
above command to be:

```
ls -al | pipe-slack
```

Woot!

## Other things to know...

`pipe-slack` doesn't pass the pipe along. It is a sink... so it doesn't return
anything useful to the pipe. so `ls -al | pipe-slack | grep 'awesomesauce'` doesn't
really make sense.

But `ls -al | grep 'awesomesauce' | pipe-slack` just might.