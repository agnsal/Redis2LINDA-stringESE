# Redis2LINDA-stringESE
This package is composed of two parts:
- Redis2LINDA.py is a Python program that allows to send messages from Redis to DALI MAS agents (via Linda), in a special encoding
- stringESE.pl is a Prolog library that allows DALI MAS agents to decode messages that come from Redis (via Linda)

##Redis2LINDA.py##
You can modify these lines to configure Redis2LINDA.py:
- pubsub.subscribe('LINDAchannel') -> The program listens to a Redis channel called "LINDAchannel" (you can change the name of the channel)
- L.send_message('masa', "redis(" + atomic + ")") -> "masa" is the name of the agent that receive the message. masa will receive any Redis message like it would do with a send_message() with the body in this form: redis(<content_of_message>). Then, the agent can have inside the event redisE(<content_of_message>) to react when Redis messages arrive.

##stringESE.pl##
- To allow agents to decode Redis messages content, you have to compile the file stringESE.pl inside the agents that receive Redis messages.
- To decode the content of a Redis message, you have to write this line in the agents code: pulisciStringa(<content_of_message>,<result_variable_name>).

##Do you need to send messages from MAS to Redis too?##
See also redis_client.pl: https://github.com/AAAI-DISIM-UnivAQ/RedisClient
