# Syndesi communication

The syndesi communication protocol is request-reply based. All commands are issued from the host to the device(s). 

(((image)))

Each frame contains a 1-byte header and then, based on the values of the header, either :

- An error code (2 bytes)
- A payload length (2 bytes) followed by a payload

(((image)))

The content of each payload is determined by an interpreter, used by the host and the device. Each host/device can have multiple interpreters to provide the necessary functionnalities.

The most basic interpreter is the "raw interpreter". It simply puts a user array of bytes inside the request and expects another array in return (from the host perspective).

Other interpreters can be created by the user.