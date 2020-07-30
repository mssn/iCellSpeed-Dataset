###############################################################################
#   iCellSpeed Dataset Release (MobiCom'20)
#
#   MI-LAB: http://http://milab.cs.purdue.edu/
#
###############################################################################

This README is used to introduce our released datasets by our MobiCom'20 work:
“iCellSpeed: Increasing Cellular Data Speed with Device-Assisted Cell
Selection”.

We have conducted measurement study in several cities including Lafayette/West
Lafayette (IN), Austin (TX) and Los Angeles (CA) with four top-tier US
carriers: AT&T, T-Mobile, Verizon and Sprint. We run our experiments through
MI-LAB testbed (http://milab.cs.purdue.edu/).

In particular, we run three distinct types of experiments for three purposes:

(I) Network downlink speed test at static locations and while driving along
specific routes. We pick about 30 locations and 10 routes at different cities
and let the mobile devices run heavy traffic flows (here, downloading a 500MB
file from the lab server).

(II) Network cell deployement measurements. We drove along all main roads
across West Lafayette, IN and let mobile devices run light traffic flows (Ping
Google every second).

(III) Evaluation of iCellSpeed. We let mobile devices run file downloading,
DASH video streaming and Zoom video conferencing.

Both type-I and type-II experiments are performed via the ApplicationOnTheGo
task in MI-LAB (with specific configuration for 500MB file downloading) and was
primarily performed from Aug 25 2019 to March 13, 2020. For type-I, at every
static location spot, we conducted experiment in both default networking
settings and controlled networking settings with iCellSpeed or swiching
airplane mode for comparison.  For type-II, most experiment traces are
collected under default networking settings except particular routes with
iCellSpeed enabled or switching airplane mode.

As a result, we have three datasets:

D1) type-I experiments in the static/driving tests (heavy load tasks via
ApplicationOnTheGo).
D2) type-II experiments in the driving tests (light load tasks via MMLabv2).
Note, we have already released results colected before 2020 in our
HotMobile2020 dataset release. Here, we release the extra experiment collected
on March, 2020 using Sprint at Lafayette, IN.
D3) type-II evluation experiments (file downloading, DASH video streaming and
Zoom video conferencing).

Two datasets (D1 and D2) in our MobiCom’20 dataset contains logs collected
in the experiments for 921.4 hours and over 11,066 Km.


1) Structure of files

├── D1_driving
│   ├── West Lafayette
│   │   ├── data_310120.csv
│   │   ├── data_310260.csv
│   │   ├── data_310410.csv
│   │   └── data_311480.csv
│   ├── Lafayette
│   │   ├....
│   ├── LosAngeles
│   │   ├....
│   ├── Austin
│       ├....
│
├── D1_static
│   ├── West Lafayette
│   │   ├── ATT
│   │   │   ├── location_01
│   │   │   │   ├── default
│   │   │   │   │   ├── data_***_001.csv
│   │   │   │   │   ├── data_***_002.csv
│   │   │   │   │   ├....
│   │   │   │   │
│   │   │   │   ├── control
│   │   │   │   │   ├── data_***_001.csv
│   │   │   │   │   ├── data_***_002.csv
│   │   │   │   │   ├....
│   │   │   ├....
│   │   │
│   │   ├── T-Mobile
│   │   │   │   ├....
│   │   └── Verizon
│   │       ├── ...
│   ├── Lafayette
│   │   ├....
│   ├── LosAngeles
│   │   ├....
│   ├── Austin
│       ├....
├── D2_light
│   ├── Lafayette
│       ├─── data_310120.csv
├── D3_evaluation
│   ├── eval_file_download
│   │   ├── ATT
│   │   │   ├── location_01
│   │   │   │   ├── default
│   │   │   │   │   ├── ***.csv
│   │   │   │   │
│   │   │   │   ├── control
│   │   │   │   │   ├── ***.csv
│   │   │   ├....
│   │   │
│   ├── eval_dash
│   │   ├── ATT
│   │   │   ├── location_01
│   │   │   │   ├── vbr_default
│   │   │   │   │   ├── ***.csv
│   │   │   │   │
│   │   │   │   ├── vbr_control
│   │   │   │   │   ├── ***.csv
│   │   │   │   │
│   │   │   │   ├── cbr_4K_default
│   │   │   │   │   ├── ***.csv
│   │   │   │   │
│   │   │   │   ├── cbr_4K_control
│   │   │   │   │   ├── ***.csv
│   │   │   │   │
│   │   │   ├....
│   │   │
│   ├── eval_zoom
│   │   ├── ATT
│   │   │   ├── location_17
│   │   │   │   ├── default
│   │   │   │   │   ├── ***.csv
│   │   │   │   │
│   │   │   │   ├── control
│   │   │   │   │   ├── ***.csv

2) Dataset release and its Descriptions (data*.csv)

-------------------------------------------------------------------------------
Dataset 1 heavy_load: static/driving experiment
-------------------------------------------------------------------------------

This is the dataset for driving/static tests. The mobile device keeps
downloading a large file from our lab server. We record its serving cells set
and instant throughput (per second).

Data file format:
grid_lat:                           latitude of grid (precision 0.0005)
grid_lon:                           longitude of grid (precision 0.0005)
pcell_cid:                          physical cell ID of PCell
pcell_freq:                         downlink earfcn of PCell
scell_1_cid:                        physical cell ID of SCell1
scell_1_freq:                       downlink earfcn of SCell1
scell_2_cid:                        physical cell ID of SCell2
scell_2_freq:                       downlink earfcn of SCell2
scell_3_cid:                        physical cell ID of SCell3
scell_3_freq:                       downlink earfcn of SCell3
seconds_since_epoch:                datetime in epoch format
throughput:                         bits per secound
past_seconds_since_rrc_request:     past seconds since device receives an RRC
                                    request

-------------------------------------------------------------------------------
Dataset 2 light_load experiments
-------------------------------------------------------------------------------

This is the dataset to learn the serving cell set in the drive tests. It runs a
mice flow (keeps pinging Google), rather than the heavy file downloading to
save the data usage. All the recorded data is the same as D2, except that no
throughput is recorded.

Data file format:
grid_lat:                           latitude of grid (precision 0.0005)
grid_lon:                           longitude of grid (precision 0.0005)
pcell_cid:                          physical cell ID of PCell
pcell_freq:                         downlink earfcn of PCell
scell_1_cid:                        physical cell ID of SCell1
scell_1_freq:                       downlink earfcn of SCell1
scell_2_cid:                        physical cell ID of SCell2
scell_2_freq:                       downlink earfcn of SCell2
scell_3_cid:                        physical cell ID of SCell3
scell_3_freq:                       downlink earfcn of SCell3
seconds_since_epoch:                datetime in epoch format
past_seconds_since_rrc_request:     past seconds since device receives an RRC
                                    request

-------------------------------------------------------------------------------
Dataset 3 evaluation experiments
-------------------------------------------------------------------------------

This is the dataset to evaluate the performance improvement of iCellSpeed.

Eval_DASH_CBR file format:
Stall/Play:                         Ratio of stall/play during video playing
                                    per pause (when player buffer is empty)

Eval_DASH_VBR file format:
Video bit rate:                     Video bit rate (kbps) selected by Bitmovin
                                    Player (608, 878, 1228, 1628, 2128, 3128,
                                    4728, 6128, 8728, 11728, 50128)

Eval_Zoom Data file format:
send latency:                       latency of video frames sent out
receive latency:                    latency of video frames received
send jitter:                        jitter of video frames sent out
receive jitter:                     jitter of video frames received
send resolution:                    resolution of video frames sent out
receive resolution:                 resolution of video frames received

