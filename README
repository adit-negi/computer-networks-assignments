###############################################################################
#
# Author: Aniruddha Gokhale
# Institution: Vanderbilt University
# Course: CS4283/5283 Computer Networks
# Created: Fall 2022
#
# Purpose:
#
#    This directory contains ZMQ only code for client, router and server. This is for demo purposes to show how you can
#     test out the basic chaining logic that we are intending to do for our PA2.
###############################################################################

Single Machine Scenario
-----------------------------------

To test this code on a single machine (localhost), you can try one or more routers but each will need a different port.
You can test it as follows.


(1) open 4 bash shells
(2) In shell #1, run
             python3 test_server.py
     which will run the final server on port 5555

(3) In shell #2, run
             python3 test_router.py -p 4445 -P 5555
        which will run the second hop router on port 4445 and which will connect to our server

(3) In shell #3, run
             python3 test_router.py -P 4445
        which will run the first hop router on port 4444 (default)  and which will connect to our second hop on 4445

(4) In shell #4, run
             python3 test_client.py -p 4444
        which will run the client that will connect to the first hop. You will notice responses of the HelloWorld message with
        latencies printed.


Client now takes a -m message option so that you can change HelloWorld to something else. Default number of iterations is 1000.


More complicated scenario
--------------------------------------

Here, we are going to run things in Mininet so that the IP addresses are different.

(1) create a mininet topology

           sudo mn --topo=single,7 --link=tc,delay=1msec,loss=5

           (you can skip the loss part to test things without losses)

(2) Now source the commands.txt file on the Mininet prompt as follows:

           Mininet> source commands.txt

      This will deploy routers and final server on the different emulated hosts as follows:
      - final server on 10.0.0.7
      - router each on 10.0.0.3 through 10.0.0.6
      

(3) Now we manually run 3 different clients.  You can run them on the same host or different hosts of Mininet. Here we will run
      them on the same host h1

      Mininet> xterm h1 h1 h2 h2

      This will open 4 xterms as shown. On each xterm, run the following command with a different message that each
      client wants to send. Each client will connect to the next hop router running on 10.0.0.3. Start the clients one by one
      noticing increasing delays as congestion build as more clients use the same route.

      first xterm of h1:          python3 test_client.py -a 10.0.0.3 -p 4444 -m HelloClient1
      second xterm of h1:    python3 test_client.py -a 10.0.0.3 -p 4444 -m HelloClient2
      first xterm of h2:        python3 test_client.py -a 10.0.0.3 -p 4444 -m HelloClient3
      second xterm of h2:        python3 test_client.py -a 10.0.0.3 -p 4444 -m HelloClient4
      
