A network service fuzzer that supports also binary protocols.
The fuzzer expects to get a sample of a typical payload in binary format, then it sends fuzzing requests 
to the specified host and port.

usage: fuzzer.py [-h] -t TARGET [-p PORT] [-u TIMEOUT] [-f FILENAME]
                 [-a ATTACK_TECHNIQUE] [-v] [-b PAD_BYTE]
                 [-m MAX_PADDING_LENGTH]

Parse

optional arguments:
  -h, --help            show this help message and exit
  -t TARGET, --target TARGET
                        Target host address
  -p PORT, --port PORT  Target port
  -u TIMEOUT, --timeout TIMEOUT
                        Timeout in seconds
  -f FILENAME, --filename FILENAME
                        Input file
  -a ATTACK_TECHNIQUE, --attack_technique ATTACK_TECHNIQUE
                        Attack techniques types: 0 = original payloads only, 1
                        = byte switch, 2 = length fuzzer
  -v, --verbose         set verbosity
  -b PAD_BYTE, --pad_byte PAD_BYTE
                        fuzz using this pad byte
  -m MAX_PADDING_LENGTH, --max_padding_length MAX_PADDING_LENGTH
                        max size for length fuzz




Supported attack techniques (specified using the -a argument):

0 orignal payload only -- just sends the original payload from the file.

1 byte switcher -- Goes over the payload byte by byte and replaces each byte with value o 0-255.

2 - length fuzzer -- Adds an increasing number of a bytes to the end of the payload.



example:
python fuzzer.py -t 127.0.0.1 -p 8080 -u 0.5 -f example.txt -a 1 -v
