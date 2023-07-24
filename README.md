# A simple SoupBinTCP library in C++

I originally had this as part of the NASDAQ ITCH/OUCH library, but it is an independent piece.

The idea is to provide the basic components needed for a SoupBinTCP server or client.

The library uses Boost ASIO for network connectivity. Heartbeats are set at 1 second, although easily changed.

I believe this to be fairly complete, and am using it in simulation projects. 

Try it out, and feel free to add PRs, issues, etc. Enjoy!

See [NASDAQ protocol documentation](https://www.nasdaq.com/docs/SoupBinTCP%204.0.pdf)

ToDo:
- reset timer on send (code is there, just need to implement and test)
- more tests