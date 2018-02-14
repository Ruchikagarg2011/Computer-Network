# Computer-Network

Client using customized protocol on top of UDP protocol for sending information to the server.
One client connects to one server.

Procedure:
Client sends five packets (Packet 1, 2, 3, 4, 5) to the server.
The server acknowledges with ACK for the correct packet from client by sending five ACKs.
Client then sends another five packets (Packet 1, 2, 3, 4, 5) to the server, emulating one correct packet and four packets with errors.
The server acknowledges with ACK for the correct packet from client, and with corresponding Reject sub codes for packets with errors.
The client will start an ack_timer at the time the packet is sent to server, if the ACK (Acknowledge) for each packet has not been received during ack_timer period by client before expiration of timer then client should retransmit the packet that was sent before.
The timer can be set at 3 seconds (recommended) and a retry counter should be used for resending the packet. If the ACK for the packet does not arrive before the timeout, the client will retransmit the packet and restart the ack_timer, and the ack_timer should be reset for a total of 3 times.
If no ACK was received from the server after resending the same packet 3 times, the client should generate the following message and display on screen:
“Server does not respond”.

Reject error handling with sub code:
Case-1: An error message should be displayed on the screen when the received packet at server is not in sequence with expected packet from client; an error message should be generated by server and sent to client.
Case-2: The server receives a packet which its length field does not match the length of data in the payload field, an error message should be generated by server and sent to the client.
Case-3: The server receives a packet which does not have the End of Packet Identifier an error message should be generated by server and sent to the client
