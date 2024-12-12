# CS190N-Project

## Instructions for dumping pcap data into CSV using tshark:
  1. Go into target directory in terminal
  2. echo "ts_server{ts_switch{sIP{tcp_sPort{udp_sPort{dIP{tcp_dPort{udp_dPort{ip_tot_len{ip_hdr_len{ip_proto{tcp_flags{tcp_seq{tcp_ack{tcp_hdr_len{udp_tot_len{retransmission{tcp_options_ts{tcp_options_tsecr{hostname{ssrc_id{rtp_ptype{rtp_seq{ts_rtp" >> <name_of_target_file>.csv
  3. tshark -r /mnt/md0/cs190n/<whatever_filepath>/tmp/<name_of_pcap>.pcap -T fields -E separator={ -e frame.time_epoch -e eth.dst -e ip.src -e tcp.srcport -e udp.srcport -e ip.dst -e tcp.dstport -e udp.dstport -e ip.len -e ip.hdr_len -e ip.proto -e tcp.flags -e tcp.seq_raw -e tcp.ack_raw -e tcp.hdr_len -e udp.length -e tcp.analysis.retransmission -e tcp.options.timestamp.tsval -e tcp.options.timestamp.tsecr -e tls.handshake.extensions_server_name >>  <name_of_target_file>.csv

