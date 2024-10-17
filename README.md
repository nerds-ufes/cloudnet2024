
# Early Detection and Classification of Malicious Activities in Network and Cloud Services

### Conference Information
- **Event:** IEEE International Conference on Cloud Networking - IEEE CloudNet 2024
- **Location:** Rio de Janeiro, Brazil
- **Dates:** November 27–29, 2024

---

## Description

This repository contains datasets and analysis used in the research **"Early Detection and Classification of Malicious Activities in Network and Cloud Services."** The paper addresses the early detection of malicious activities across network and cloud services, with a focus on scanning activities, web-based attacks, and Tor network anomalies.

The datasets are derived from real-world network activities, anonymized to ensure privacy. IP addresses (both source and destination) have been anonymized for security reasons.

### Datasets

The datasets consist of five main categories, each focusing on different types of attacks:

| **Dataset**              | **Attack Types**                                                                                       | **Description**                                                                                                                                                                                                                               |
|--------------------------|--------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Scan Train**            | FIN, XMAS, NULL, SYN, CONNECT, ACK, UDP, Maimon                                                        | This dataset captures scanning activities using multiple techniques commonly employed by attackers to identify vulnerabilities. <br> Files: `dataset_scan_train_conn_part_1.csv` to `dataset_scan_train_conn_part_2.csv` (Connection), <br> `dataset_scan_train_flow_part_1.csv` to `dataset_scan_train_flow_part_4.csv` (Flow). |
| **Scan Test**             | FIN, XMAS, NULL, SYN, CONNECT, ACK, UDP, Maimon                                                        | Similar to Scan Train, but recorded during a separate time window to capture variations in traffic patterns. <br> Files: `dataset_scan_test_conn_part_1.csv` to `dataset_scan_test_conn_part_2.csv` (Connection), <br> `dataset_scan_test_flow_part_1.csv` to `dataset_scan_test_flow_part_3.csv` (Flow). |
| **Web Attack**            | Webscan, SQLi Tor, SQLi, XSS                                                                           | Captures malicious activities targeting web services, including SQL Injection (SQLi) and Cross-Site Scripting (XSS) attacks, as well as scans specifically targeting web vulnerabilities. <br> Files: `dataset_webattack_conn_part_1.csv` to `dataset_webattack_conn_part_4.csv` (Connection), <br> `dataset_webattack_flow_part_1.csv` to `dataset_webattack_flow_part_10.csv` (Flow). |
| **Tor Network Train**     | Tor client connection to entry node                                                                    | Anomalous traffic data gathered from the Tor network, aimed at identifying misuse patterns. <br> Files: `dataset_tor_train_part_1.csv` to `dataset_tor_train_part_20.csv`.                                                                                                             |
| **Tor Network Test**      | Tor client connection to entry node                                                                    | A second set of data from Tor network traffic, used for test and validation with the first dataset. <br> Files: `dataset_tor_test_part_1.csv` to `dataset_tor_test_part_10.csv`.                                                                                                                                       |


### Anonymization

For security and privacy, all IP addresses (source and destination) have been anonymized. 

### Dataset Structure

The **Scan** and **Web Attack** datasets are divided into two distinct files:
1. **Connection Data** - Generated using [Zeek](https://zeek.org/), this file contains connection-level information.
2. **Flow Data** - Generated using the [FlowMeter module for Zeek](https://github.com/zeek-flowmeter/zeek-flowmeter), developed through the [CICFlowmeter](https://github.com/ahlashkari/CICFlowMeter) project, this file contains detailed flow statistics.

You can merge these two files using the `uid` field, which uniquely identifies each session across both files.

### Dataset Attributes

The datasets contain different sets of attributes depending on the type of data being recorded (Connection, Flow, or Tor).

#### **Connection (Conn) Attributes**
The following attributes are included in the connection-level datasets (Scan and Web Attack):

- `ts`, `uid`, `id_orig_h`, `id_orig_p`, `id_resp_h`, `id_resp_p`, `proto`, `service`, `duration`, `orig_bytes`, `resp_bytes`, `conn_state`, `local_orig`, `local_resp`, `missed_bytes`, `history`, `orig_pkts`, `orig_ip_bytes`, `resp_pkts`, `resp_ip_bytes`, `tunnel_parents`, `scan_type`, `y`

#### **Flow Attributes**
The following attributes are included in the flow-level datasets (Scan and Web Attack):

- `uid`, `flow_duration`, `fwd_pkts_tot`, `bwd_pkts_tot`, `fwd_data_pkts_tot`, `bwd_data_pkts_tot`, `fwd_pkts_per_sec`, `bwd_pkts_per_sec`, `flow_pkts_per_sec`, `down_up_ratio`, `fwd_header_size_tot`, `fwd_header_size_min`, `fwd_header_size_max`, `bwd_header_size_tot`, `bwd_header_size_min`, `bwd_header_size_max`, `flow_FIN_flag_count`, `flow_SYN_flag_count`, `flow_RST_flag_count`, `fwd_PSH_flag_count`, `bwd_PSH_flag_count`, `flow_ACK_flag_count`, `fwd_URG_flag_count`, `bwd_URG_flag_count`, `flow_CWR_flag_count`, `flow_ECE_flag_count`, `fwd_pkts_payload_min`, `fwd_pkts_payload_max`, `fwd_pkts_payload_tot`, `fwd_pkts_payload_avg`, `fwd_pkts_payload_std`, `bwd_pkts_payload_min`, `bwd_pkts_payload_max`, `bwd_pkts_payload_tot`, `bwd_pkts_payload_avg`, `bwd_pkts_payload_std`, `flow_pkts_payload_min`, `flow_pkts_payload_max`, `flow_pkts_payload_tot`, `flow_pkts_payload_avg`, `flow_pkts_payload_std`, `fwd_iat_min`, `fwd_iat_max`, `fwd_iat_tot`, `fwd_iat_avg`, `fwd_iat_std`, `bwd_iat_min`, `bwd_iat_max`, `bwd_iat_tot`, `bwd_iat_avg`, `bwd_iat_std`, `flow_iat_min`, `flow_iat_max`, `flow_iat_tot`, `flow_iat_avg`, `flow_iat_std`, `payload_bytes_per_second`, `fwd_subflow_pkts`, `bwd_subflow_pkts`, `fwd_subflow_bytes`, `bwd_subflow_bytes`, `fwd_bulk_bytes`, `bwd_bulk_bytes`, `fwd_bulk_packets`, `bwd_bulk_packets`, `fwd_bulk_rate`, `bwd_bulk_rate`, `active_min`, `active_max`, `active_tot`, `active_avg`, `active_std`, `idle_min`, `idle_max`, `idle_tot`, `idle_avg`, `idle_std`, `fwd_init_window_size`, `bwd_init_window_size`, `fwd_last_window_size`, `bwd_last_window_size`

#### **Tor Attributes**
The following attributes are included in the Tor-related datasets:

- `ts`, `id_orig_h`, `id_orig_p`, `id_resp_h`, `id_resp_p`, `version`, `cipher`, `curve`, `server_name`, `resumed`, `last_alert`, `next_protocol`, `established`, `ssl_history`, `sni_matches_cert`, `validation_status`, `scan_type`, `y`


### Merging Conn and Flow Data

In the Scan and Web Attack datasets, the connection data and flow data can be merged using the `uid` attribute. This unique identifier is consistent across both files, allowing the connection information (such as IP addresses and ports) to be linked with the flow-level statistics (such as packet counts and transmission speeds).

For example, to merge the connection and flow data, you can use the following command in Python:

```python
merged_data = conn_data.merge(flow_data, on='uid')
```


## Excluded Features

Several features were excluded from the analysis for the following reasons:

| **Feature**                     | **Reason**                      |
|----------------------------------|----------------------------------|
| `ts`                             | Timestamp                        |
| `uid`                            | Unique identifier                |
| `id_orig_h`                      | Bias                             |
| `id_resp_h`                      | Bias                             |
| `tunnel_parents`                 | Unique identifier                |
| `scan_type`                      | Scan target                      |
| `y`                              | Binary target                    |
| `id_orig_p`                      | Bias                             |
| `id_resp_p`                      | Bias                             |
| `flow_duration`                  | Time-related                     |
| `fwd_iat_max`                    | Time-related                     |
| `fwd_iat_tot`                    | Time-related                     |
| `fwd_iat_min`                    | Time-related                     |
| `fwd_iat_avg`                    | Time-related                     |
| `fwd_iat_std`                    | Time-related                     |
| `bwd_iat_max`                    | Time-related                     |
| `bwd_iat_tot`                    | Time-related                     |
| `bwd_iat_min`                    | Time-related                     |
| `bwd_iat_avg`                    | Time-related                     |
| `bwd_iat_std`                    | Time-related                     |
| `flow_iat_max`                   | Time-related                     |
| `flow_iat_tot`                   | Time-related                     |
| `flow_iat_avg`                   | Time-related                     |
| `flow_iat_std`                   | Time-related                     |
| `flow_iat_min`                   | Time-related                     |
| `active_tot`                     | Time-related                     |
| `active_min`                     | Time-related                     |
| `active_max`                     | Time-related                     |
| `active_avg`                     | Time-related                     |
| `active_std`                     | Time-related                     |
| `idle_max`                       | Time-related                     |
| `idle_tot`                       | Time-related                     |
| `idle_std`                       | Time-related                     |
| `idle_min`                       | Time-related                     |
| `idle_avg`                       | Time-related                     |
| `payload_bytes_per_second`       | Transmission speed               |
| `down_up_ratio`                  | Transmission speed               |
| `fwd_bulk_rate`                  | Transmission speed               |
| `bwd_bulk_rate`                  | Transmission speed               |
| `fwd_pkts_per_sec`               | Transmission speed               |
| `bwd_pkts_per_sec`               | Transmission speed               |
| `flow_pkts_per_sec`              | Transmission speed               |
| `local_orig`                     | Bias                             |
| `local_resp`                     | Bias                             |
| `fwd_init_window_size`           | Bias                             |
| `bwd_init_window_size`           | Bias                             |
| `fwd_last_window_size`           | Bias                             |
| `bwd_last_window_size`           | Bias                             |
| `duration`                       | Time-related                     |
| `orig_ip_bytes`                  | Bias                             |
| `resp_ip_bytes`                  | Bias                             |
| `fwd_pkts_tot`                   | Duplicate                        |
| `bwd_pkts_tot`                   | Duplicate                        |

---

## Citation

If you use this dataset or find it helpful, please cite our paper presented at the IEEE International Conference on Cloud Networking 2024.
