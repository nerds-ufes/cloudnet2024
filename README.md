
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

---

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
