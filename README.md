# Runscope Radar Docker Agent

This is light-weight Docker image for running the [Runscope Radar](https://www.runscope.com/docs/radar/agent) on-premise agent.

## Example

I don't know of a better way to do this, so if anyone can help out, pull requests welcome. I had to log in via the Runscope agent locally to get all of this information:

```
$ ./runscope-agent
```

After you log into your account, it will ask if you want to save a config file. Say yes, then you can open that file and use it to build up the appropriate Docker command.

```shell
docker run --name runscope-agent \
-e NAME=runscope-agent-test \
-e TOKEN=runscope-token \
-e AGENT_ID=agent-id \
-e TEAM_ID=team-id \
mmcc/runscope-agent"
```

There are also the optional environment variables TIMEOUT, DISCONNECT_TIMEOUT, and THREADS to let you customize the agent to your server specs. Using those would look like this:

```shell
docker run --name runscope-agent \
-e NAME=runscope-agent-test \
-e TOKEN=runscope-token \
-e AGENT_ID=agent-id \
-e TEAM_ID=team-id \
-e TIMEOUT=20 \
-e DISCONNECT_TIMEOUT=10 \
-e THREADS=32 \
mmcc/runscope-agent"
```

I took quite a few cues from the [Docker DataDog agent](https://github.com/DataDog/docker-dd-agent) when building this, so big thanks to [DataDog](http://datadog.com).
