################################################################################
# README                                                                       #
#                                                                              #
# Description: This file serves as a README and documentation for project2     #
#                                                                              #
#                                                                              #
################################################################################




[TOC-1] Table of Contents
--------------------------------------------------------------------------------

        [TOC-1] Table of Contents
        [DES-2] Description of Files
        [RUN-3] How to Run




[DES-2] Description of Files
--------------------------------------------------------------------------------

Here is a listing of all files associated with Recitation 1 and what their'
purpose is:

                    Makefile            - Contains rules for make
                    readme.txt       	- Current document 
		    peer.c		- The main file
	  	    bt_parser.[c,h]	- Parse configuration files
		    chunk.[c,h]		- Generate chunks based on provided files
		    ctr_send_recv.[c,h] - Contains all recv and send related functions, and related data structure, congestion control and flow control functions are also in this file
		    client.c		- client sample
		    debug.[c,h]		- Utility debug functions
		    input_buffer.[c,h]  - Parse user input
		    list.[c,h]		- List library	
		    make_chunks.c	- Generate chunks
		    nodes.map		- Include ip and port of all peers
		    packet.[c,h]	- Generate various kinds of packets
		    processs_udp.[c,h]  - Process udp input and output based on the packet 
		    peer.c		- Main file
		    problem2-peer.txt	- File contains the resulting window size
		    process_udp.[c,h] 	- Contains functions related to processing inbound and outbound packets of different types
		    readme.txt		- Readme file
		    server.c		- Sample server
		    sha.[c,h]		- Hash functions
		    spiffy.[c,h]	- Simulate environment with packet loss
		    test_input_buffer.c	- Test input buffer
		    tests.txt		- Contains the tests done 
		    topo.map		- Include topology of peers
		    vulnerabilities.txt	- Details the vulnerabilities of the code

Design:
    Each peer keeps a list of data window and a list of flow windows. When the peer sends a chunk of data another peer, it create a data window and enlist it. A flow window is created when the peer downloads a chunk from another peer. Congestion control and flow control are done by manipulating all sorts of indices in the data structure of data window and flow window. 
    Each time the sock of a peer is selected, it reads/writes one single packet, which is a packet from/to the peer with oldest connection with this peer. 
    Congestion control is done according to the requiremnts of handout. Flow control fixes the window size to be 10, which might limit the transmitions speed.


[RUN-3] How to Run
--------------------------------------------------------------------------------

Building code by running make:

                    make

Running code by inputing:

		    peer -p <peer-list-file> -c <has-chunk-file> -m <max-downlaods>
			 -i <peer-identity>  -f <master-chunk-file> -d <debug-mode>
		// debug mode is hard coded to 0xff, i.e. all debug info. are printed

[TXT-5] The content of file problem2-peer.txt
--------------------------------------------------------------------------------
1	         8	    2
1	         9	    3
1	         9	    4
1	        10	    5
1	        10	    6
1	        10	    7
1	        11	    8
1	        11	    9
1	        12	   10
1	        12	   11
1	        12	   12
1	        13	   13
1	        13	   14
1	        14	   15
1	        14	   16
1	        15	   17
1	        15	   17
1	        15	   18
1	        15	   18
1	        16	   18
1	        16	    1
1	        16	    2
1	        17	    2
1	        17	    1
1	        18	    1
1	        18	    1
1	        19	    1
1	        19	    1
1	        20	    1
1	        20	    1
1	        20	    2
1	        20	    2
1	        21	    2
1	        22	    2
1	        22	    2
1	        23	    3
1	        23	    3
1	        24	    3
1	        24	    3
1	        24	    3
1	        25	    3
1	        25	    3
1	        26	    4
1	        26	    4
1	        27	    4
1	        27	    4
1	        28	    4
1	        28	    4
1	        28	    4
1	        29	    5
1	        29	    5
1	        30	    5
1	        30	    5
1	        31	    5
1	        31	    5
1	        31	    5
1	        32	    6
1	        32	    6
1	        33	    6
1	        33	    6
1	        34	    6
1	        34	    6
1	        34	    6
1	        35	    7
1	        35	    7
1	        36	    7
1	        36	    7
1	        36	    7
1	        37	    7
1	        37	    7
1	        38	    8
1	        38	    8
1	        39	    8
1	        39	    8
1	        39	    8
1	        40	    8
1	        40	    8
1	        41	    9
1	        41	    9
1	        42	    9
1	        42	    9
1	        42	    9
1	        43	    9
1	        43	    9
1	        44	   10
1	        44	   10
1	        44	   10
1	        45	   10
1	        45	   10
1	        46	   10
1	        46	    1
1	        46	    2
1	        46	    3
1	        47	    4
1	        47	    5
1	        48	    5
1	        48	    5
1	        49	    5
1	        49	    5
1	        49	    5
1	        50	    1
1	        51	    1
1	        51	    1
1	        51	    1
1	        52	    2
1	        52	    2
1	        53	    2
1	        53	    2
1	        54	    2
1	        54	    1
1	        55	    1
1	        55	    1
1	        56	    2
1	        56	    2
1	        57	    2
1	        57	    2
1	        58	    2
1	        58	    2
1	        59	    3
1	        59	    3
1	        60	    3
1	        60	    3
1	        61	    3
1	        61	    3
1	        61	    3
1	        62	    4
1	        62	    4
1	        63	    4
1	        63	    4
1	        64	    4
1	        64	    4
1	        64	    4
1	        65	    5
1	        65	    5
1	        66	    5
1	        66	    5
1	        67	    5
1	        67	    5
1	        68	    6
1	        68	    6
1	        68	    6
1	        69	    6
1	        69	    6
1	        70	    6
1	        70	    6
1	        70	    6
1	        71	    7
1	        71	    7
1	        72	    7
1	        72	    7
1	        73	    7
1	        73	    7
1	        73	    7
1	        74	    8
1	        74	    8
1	        75	    8
1	        75	    8
1	        76	    8
1	        76	    8
1	        76	    8
1	        77	    9
1	        77	    9
1	        78	    9
1	        78	    9
1	        78	    9
1	        79	    9
1	        79	    9
1	        80	   10
1	        80	   10
1	        81	   10
1	        81	    1
1	        81	    2
1	        81	    3
1	        82	    4
1	        82	    5
1	        83	    5
1	        83	    5
1	        83	    5
1	        84	    5
1	        84	    5
1	        85	    1
1	        86	    1
1	        86	    1
1	        86	    1
1	        87	    2
1	        87	    2
1	        88	    2
1	        88	    2
1	        88	    2
1	        89	    1
1	        90	    1
1	        90	    1
1	        91	    2
1	        91	    2
1	        92	    2
1	        92	    2
1	        93	    2
1	        93	    2
1	        94	    3
1	        94	    3
1	        95	    3
1	        95	    3
1	        95	    3
1	        96	    3
1	        96	    3
1	        97	    4
1	        97	    4
1	        98	    4
1	        98	    4
1	        98	    4
1	        99	    4
1	        99	    4
1	       100	    5
1	       100	    5
1	       101	    5
1	       101	    5
1	       102	    5
1	       102	    5
1	       102	    5
1	       103	    6
1	       103	    6
1	       104	    6
1	       104	    6
1	       104	    6
1	       105	    6
1	       105	    6
1	       106	    7
1	       106	    7
1	       107	    7
1	       107	    7
1	       108	    7
1	       108	    7
1	       108	    7
1	       109	    8
1	       109	    8
1	       110	    8
1	       110	    8
1	       110	    8
1	       111	    8
1	       111	    8
1	       112	    9
1	       112	    9
1	       112	    9
1	       113	    9
1	       113	    9
1	       114	    9
1	       114	    9
1	       115	   10
1	       115	   10
1	       115	   10
1	       116	   10
1	       116	    1
1	       116	    2
1	       117	    3
1	       117	    4
1	       118	    5
1	       118	    5
1	       118	    5
1	       119	    5
1	       119	    5
1	       120	    5
1	       120	    1
1	       121	    1
1	       121	    1
1	       122	    1
1	       122	    1
1	       122	    2
1	       123	    2
1	       123	    2
1	       123	    2
1	       124	    2
1	       125	    1
1	       125	    1
1	       125	    1
1	       126	    2
1	       126	    2
1	       127	    2
1	       128	    2
1	       128	    2
1	       129	    3
1	       129	    3
1	       129	    3
1	       130	    3
1	       130	    3
1	       131	    3
1	       131	    3
1	       132	    4
1	       132	    4
1	       133	    4
1	       133	    4
1	       133	    4
1	       134	    4
1	       134	    4
1	       135	    5
1	       135	    5
1	       136	    5
1	       136	    5
1	       136	    5
1	       137	    5
1	       137	    5
1	       138	    6
1	       138	    6
1	       139	    6
1	       139	    6
1	       139	    6
1	       140	    6
1	       140	    6
1	       141	    7
1	       141	    7
1	       142	    7
1	       142	    7
1	       142	    7
1	       143	    7
1	       143	    7
1	       144	    8
1	       144	    8
1	       145	    8
1	       145	    8
1	       145	    8
1	       146	    8
1	       146	    8
1	       147	    9
1	       147	    9
1	       147	    9
1	       148	    9
1	       148	    9
1	       149	    9
1	       149	    9
1	       149	    9
1	       150	   10
1	       150	   10
1	       151	   10
1	       151	    1
1	       151	    2
1	       152	    3
1	       152	    4
1	       152	    5
1	       153	    5
1	       153	    5
1	       154	    5
1	       154	    5
1	       154	    5
1	       155	    1
1	       156	    1
1	       156	    1
1	       157	    1
1	       157	    1
1	       157	    2
1	       157	    2
1	       158	    2
1	       158	    2
1	       159	    2
1	       160	    1
1	       160	    1
1	       160	    1
1	       161	    2
1	       161	    2
1	       162	    2
1	       162	    2
1	       163	    2
1	       163	    2
1	       164	    3
1	       164	    3
1	       165	    3
1	       165	    3
1	       166	    3
1	       166	    3
1	       167	    4
1	       167	    4
1	       167	    4
1	       168	    4
1	       168	    4
1	       169	    4
1	       169	    4
1	       170	    5
1	       170	    5
1	       170	    5
1	       171	    5
1	       171	    5
1	       172	    5
1	       172	    5
1	       173	    6
1	       173	    6
1	       173	    6
1	       174	    6
1	       174	    6
1	       175	    6
1	       175	    6
1	       176	    7
1	       176	    7
1	       176	    7
1	       177	    7
1	       177	    7
1	       178	    7
1	       178	    7
1	       179	    8
1	       179	    8
1	       179	    8
1	       180	    2
1	       180	    3
1	       181	    4
1	       181	    5
1	       181	    6
1	       182	    7
1	       182	    8
1	       183	    9
1	       183	   10
1	       184	   11
1	       184	   12
1	       184	   13
1	       185	   14
1	       185	   15
1	       186	   16
1	       186	   17
1	       187	   18
1	       187	   18
1	       187	   19
1	       187	    1
1	       187	    2
1	       188	    3
1	       189	    3
1	       189	    1
1	       189	    1
1	       190	    1
1	       190	    1
1	       191	    1
1	       191	    1
1	       191	    1
1	       191	    1
1	       191	    2
1	       192	    2
1	       193	    2
1	       193	    2
1	       194	    3
1	       194	    3
1	       195	    3
1	       195	    3
1	       195	    3
1	       196	    3
1	       196	    3
1	       197	    4
1	       197	    4
1	       198	    4
1	       198	    4
1	       199	    4
1	       199	    4
1	       199	    4
1	       200	    5
1	       200	    5
1	       201	    5
1	       201	    5
1	       202	    5
1	       202	    5
1	       202	    5
1	       203	    6
1	       203	    6
1	       204	    6
1	       204	    6
1	       205	    6
1	       205	    6
1	       205	    6
1	       206	    7
1	       206	    7
1	       207	    7
1	       207	    7
1	       208	    7
1	       208	    7
1	       208	    7
1	       209	    8
1	       209	    8
1	       210	    8
1	       210	    8
1	       211	    8
1	       211	    8
1	       211	    8
1	       212	    9
1	       212	    9
1	       213	    9
1	       213	    9
1	       213	    9
1	       214	    9
1	       214	    9
1	       215	   10
1	       215	   10
1	       215	   10
1	       216	   10
1	       216	   10
1	       217	   10
1	       217	    1
1	       217	    2
1	       218	    3
1	       218	    4
1	       218	    5
1	       219	    5
1	       219	    5
1	       220	    5
1	       220	    5
1	       220	    5
1	       221	    1
1	       222	    1
1	       222	    1
1	       223	    1
1	       223	    1
1	       223	    2
1	       223	    2
1	       224	    2
1	       224	    2
1	       225	    2
1	       225	    1
1	       226	    1
1	       226	    1
1	       227	    2
1	       227	    2
1	       228	    2
1	       228	    2
1	       229	    2
1	       229	    2
1	       230	    3
1	       230	    3
1	       231	    3
1	       231	    3
1	       232	    3
1	       232	    3
1	       233	    4
1	       233	    4
1	       233	    4
1	       234	    4
1	       234	    4
1	       235	    4
1	       235	    4
1	       236	    5
1	       236	    5
1	       236	    5
1	       237	    5
1	       237	    5
1	       238	    5
1	       238	    5
1	       239	    6
1	       239	    6
1	       239	    6
1	       240	    6
1	       240	    6
1	       241	    6
1	       241	    6
1	       242	    7
1	       242	    7
1	       242	    7
1	       243	    7
1	       243	    7
1	       244	    7
1	       244	    7
1	       245	    8
1	       245	    8
1	       245	    8
1	       246	    8
1	       246	    8
1	       247	    8
1	       247	    8
1	       247	    8
1	       248	    9
1	       248	    9
1	       249	    9
1	       249	    9
1	       249	    9
1	       250	    9
1	       250	    9
1	       251	   10
1	       251	   10
1	       252	   10
1	       252	    1
1	       252	    2
1	       252	    3
1	       253	    4
1	       253	    5
1	       254	    5
1	       254	    5
1	       255	    5
1	       255	    5
1	       255	    5
1	       256	    1
1	       257	    1
1	       257	    1
1	       257	    1
1	       258	    2
1	       258	    2
1	       259	    2
1	       259	    2
1	       260	    2
1	       260	    1
1	       261	    1
1	       261	    1
1	       262	    2
1	       262	    2
1	       263	    2
1	       263	    2
1	       264	    2
1	       264	    2
1	       265	    3
1	       265	    3
1	       266	    3
1	       266	    3
1	       267	    3
1	       267	    3
1	       267	    3
1	       268	    4
1	       268	    4
1	       269	    4
1	       269	    4
1	       270	    4
1	       270	    4
1	       271	    5
1	       271	    5
1	       271	    5
1	       272	    5
1	       272	    5
1	       273	    5
1	       273	    5
1	       274	    6
1	       274	    6
1	       274	    6
1	       275	    6
1	       275	    6
1	       276	    6
1	       276	    6
1	       277	    7
1	       277	    7
1	       277	    7
1	       278	    7
1	       278	    7
1	       279	    7
1	       279	    7
1	       279	    7
1	       280	    8
1	       280	    8
1	       281	    8
1	       281	    8
1	       282	    8
1	       282	    8
1	       282	    8
1	       283	    9
1	       283	    9
1	       284	    9
1	       284	    9
1	       284	    9
1	       285	    9
1	       285	    9
1	       286	   10
1	       286	   10
1	       287	   10
1	       287	    1
1	       287	    2
1	       287	    3
1	       288	    4
1	       288	    5
1	       289	    5
1	       289	    5
1	       289	    5
1	       290	    5
1	       290	    5
1	       291	    1
1	       292	    1
1	       292	    1
1	       292	    1
1	       293	    2
1	       293	    2
1	       294	    2
1	       294	    2
1	       294	    2
1	       295	    1
1	       296	    1
1	       296	    1
1	       297	    2
1	       297	    2
1	       298	    2
1	       298	    2
1	       299	    2
1	       299	    2
1	       300	    3
1	       300	    3
1	       301	    3
1	       301	    3
1	       301	    3
1	       302	    3
1	       302	    3
1	       303	    4
1	       303	    4
1	       304	    4
1	       304	    4
1	       305	    4
1	       305	    4
1	       305	    4
1	       306	    5
1	       306	    5
1	       307	    5
1	       307	    5
1	       308	    5
1	       308	    5
1	       308	    5
1	       309	    6
1	       309	    6
1	       310	    6
1	       310	    6
1	       311	    6
1	       311	    6
1	       311	    6
1	       312	    7
1	       312	    7
1	       313	    7
1	       313	    7
1	       314	    7
1	       314	    7
1	       314	    7
1	       315	    8
1	       315	    8
1	       316	    8
1	       316	    8
1	       317	    8
1	       317	    8
1	       317	    8
1	       318	    9
1	       318	    9
1	       319	    9
1	       319	    9
1	       319	    9
1	       320	    9
1	       320	    9
1	       321	   10
1	       321	   10
1	       321	   10
1	       322	   10
1	       322	   10
1	       323	   10
1	       323	    1
1	       323	    2
1	       324	    3
1	       324	    4
1	       324	    5
1	       325	    5
1	       325	    5
1	       326	    5
1	       326	    5
1	       326	    5
1	       327	    1
1	       328	    1
1	       328	    1
1	       329	    1
1	       329	    1
1	       329	    2
1	       329	    2
1	       330	    2
1	       330	    2
1	       331	    2
1	       332	    1
1	       332	    1
1	       332	    1
1	       333	    2
1	       333	    2
1	       334	    2
1	       334	    2
1	       335	    2
1	       335	    2
1	       336	    3
1	       336	    3
1	       337	    3
1	       337	    3
1	       338	    3
1	       338	    3
1	       339	    4
1	       339	    4
1	       339	    4
1	       340	    4
1	       340	    4
1	       341	    4
1	       341	    4
1	       342	    5
1	       342	    5
1	       342	    5
1	       343	    5
1	       343	    5
1	       344	    5
1	       344	    5
1	       345	    6
1	       345	    6
1	       345	    6
1	       346	    6
1	       346	    6
1	       347	    6
1	       347	    6
1	       348	    7
1	       348	    7
1	       348	    7
1	       349	    7
1	       349	    7
1	       350	    7
1	       350	    7
1	       351	    8
1	       351	    8

