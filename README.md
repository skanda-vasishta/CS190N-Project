# CS190N-Project
Contributors: Skanda Vasishta, Viraj Zaveri, Sameer Rao, Garvin Young
## NetUnicorn Pipeline Instructions:
  1. Enter Netunicorn login credentials, define endpoint, and select a working node given the list of nodes in pipeline.ipynb.
  2. Enter filepath of target pcap file that will be created and name experiemnt.
  3. Run all cells in pipeline.ipynb. If you get this output: ```<class 'returns.result.Success'>```, your experiment was a success. 
## Instructions for dumping pcap data into CSV using tshark:
  1. Go into target directory in terminal
  2. ```echo "ts_server{ts_switch{sIP{tcp_sPort{udp_sPort{dIP{tcp_dPort{udp_dPort{ip_tot_len{ip_hdr_len{ip_proto{tcp_flags{tcp_seq{tcp_ack{tcp_hdr_len{udp_tot_len{retransmission{tcp_options_ts{tcp_options_tsecr{hostname{ssrc_id{rtp_ptype{rtp_seq{ts_rtp" >> <name_of_target_file>.csv```
  4. ```tshark -r /mnt/md0/cs190n/<whatever_filepath>/tmp/<name_of_pcap>.pcap -T fields -E separator={ -e frame.time_epoch -e eth.dst -e ip.src -e tcp.srcport -e udp.srcport -e ip.dst -e tcp.dstport -e udp.dstport -e ip.len -e ip.hdr_len -e ip.proto -e tcp.flags -e tcp.seq_raw -e tcp.ack_raw -e tcp.hdr_len -e udp.length -e tcp.analysis.retransmission -e tcp.options.timestamp.tsval -e tcp.options.timestamp.tsecr -e tls.handshake.extensions_server_name >>  <name_of_target_file>.csv```
## Model Preprocessing and Training Instructions:
  1. Include filepaths for CSV data (```df1 = pd.read_csv("<filepath>.csv", sep="{")```), which should correspond to above. Ensure you leave some data out from the training process to ensure you have a testing dataset, but this is ultimately a hyperparameter that you can decide.
  2. Run all training cells.
  3. Include filepath for testing data (```unseen_data = pd.read_csv("<filepath>.csv", sep="{")```)
  4. Run all testing cells and view subsequent results.
  5. To do the same process for the Stanford Puffer dataset, find data here: https://puffer.stanford.edu/data-description/. Convert video_sent_X.csv file into pandas dataframe using ```pd.read_csv```. Replicate data cleaning from previous steps and make model prediction.

