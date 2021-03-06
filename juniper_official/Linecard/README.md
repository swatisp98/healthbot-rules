# HealthBot Linecard KPI rules and playbooks

## Linecard playbooks
### Playbook name: linecard-kpis-playbook 
		> Description: "Playbook checks linecard health i.e. cpu, memory, PFE discards and CM errors"
		> Synopsis: "Linecards key performance indicators"
		> Playbook file name: linecard-kpis.playbook
		> Detals:
		 Playbook contains multiple rules which monitor linecards and notifies when
		 anomalies are found.
		 1) Rule "check-fpc-cpu" detects the line cards cpu utilization threshold
		    breaches and notifies anomalies.
		 2) Rule "check-fpc-memory" detects the line cards memory usage threshold
		    breaches and notifies anomalies.
		 3) Rule "check-cm-events" detects the cm errors and notifies anomalies
		    when error count increases.
		 4) Rule "check-pfe-discards" detects the PFE discards and notifies anomalies
		    when discard count increases.
### Playbook name: online-fpc-playbook 
		> Description: "Playbook collects online FPCs list"
		> Synopsis: "Collects online FPCs"
		> Playbook file name: online-fpc.playbook
		> Detals:
		 Playbook contains the rule which monitor online FPC
		 1) Rule "update-online-fpc" finds all the online FPCs in the chassis.

## Linecard rules

### Rule name: check-linecard-ethernet-statistics 
		> Description: "This rule collects linecard ethernet statistics periodically and notifies in case of anomalies"
		> Synopsis: "Linecard ethernet statistics kpi"
		> Rule file name: linecard-ethernet-statistics.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: linecard-ethernet-statistics.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-center-chip-wan-out 
		> Description: "Monitors the center chip wan out transmitted packets"
		> Synopsis: "Center chip wan out statistics analyzer"
		> Rule file name: wo-statistics.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: chip.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-ithrottle 
		> Description: "Monitors interrupt throttle configuration, state and usage"
		> Synopsis: "iThrottle statistics analyzer"
		> Rule file name: ithrottle.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: ithrottle.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-host-loopback-status 
		> Description: "Monitors the host loopback to detected wedges, toolkit errors"
		> Synopsis: "Host loopback analyzer"
		> Rule file name: host-loopback-status.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: task-io.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-center-chip-lookup-out 
		> Description: "This topic is to monitors and notify Center chip lookup out error"
		> Synopsis: "Center chip lookup analyzer"
		> Rule file name: lo-statistics.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: chip.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-center-chip-fabric-in 
		> Description: "Monitors the center chip fabric-in packets dropped ,error packets, received and sent packets"
		> Synopsis: "center chip fabric-in packets statistics analyzer"
		> Rule file name: fi-statistics.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: chip.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-fpc-cpu 
		> Description: "Collects system FPC CPU statistics periodically and notifies anomalies when CPU utilization exceed threshold"
		> Synopsis: "FPC CPU analyzer"
		> Rule file name: fpc-cpu-utilization.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 

			> Supported platforms: [ MX240 MX480 MX960 MX2010 MX2020 ];
			> Supported platforms: MX150;
			> Supported platforms: [ PTX5000 PTX1000 PTX10000 ];
			> Supported platforms: [ QFX10000 QFX5200 ];
			> Supported platforms: QFX5100;
			> Supported platforms: QFX5120-48Y;
			> Supported platforms: EX9200;
			> Supported platforms: EX4650;
			> Supported platforms: EX4600;

		> Supported healthbot version: 1.0.1
		> Detals:
		 Detects linecards CPU utilization threshold breaches and notifies when
		 anomalies are found.
		 Three inputs control detection
		
		   1) "fpc-slot-no" is a regular expression that matches the linecard
		      that you would like to monitor.  By default it's '0-20', which matches
		      FPC 0 to 20 linecards. Use something like '0-3' to match only specific
		      FPCs i.e. 0 to 3.
		
		   2) "fpc-cpu-high-threshold" is the threshold that causes the rule to report
		      an anomaly. By default it's 80% of CPU utilization. This rule will set
		      a dashboard color to red when FPC CPU utilization exceed high threshold
		      'fpc-cpu-high-threshold' for a period of 3 minutes.
		
		   3) "fpc-cpu-low-threshold" is the threshold that causes the rule to report
		      an anomaly. By default it's 50% of CPU utilization. This rule will set
		      a dashboard color to yellow when RE CPU utilization exceed low
		      threshold 'fpc-cpu-low-threshold' for a period of 3 minutes.
		      Otherwise color is set to green.
### Rule name: check-cm-error-table 
		> Description: "This rule collects CM error statistics periodically and notifies in case of anomalies"
		> Synopsis: "CM error analyzer"
		> Rule file name: cm-error.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: cm-error.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-traffic-offload-engine-status 
		> Description: "Monitors  TOE packets, Asic blocks, Wedge declaration, Wedge window size, Ucode, Hostpath app status"
		> Synopsis: "TOE packets analyzer"
		> Rule file name: toe-pfe.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: toe-pfe.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-jnh-interface-statistics 
		> Description: "Monitors the jnh ifd stream"
		> Synopsis: "JNH IFD stream kpi"
		> Rule file name: jnh-ifd-stream.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: jnh-ifd-stream.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-center-chip-lookup-in 
		> Description: "Monitors center chip lookup in interrupts counters"
		> Synopsis: "Center chip lookup analyzer"
		> Rule file name: li-statistics.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: chip.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-fpc-cpu-memory-usage-srx-cluster-netconf 
		> Description: "Collects FPC CPU statistics periodically and notifies anomalies when CPU utilization exceed threshold"
		> Synopsis: "FPC CPU analyzer"
		> Rule file name: fpc-cpu-memory-state-srx-cluster-netconf.rule

		> Supported products: SRX 

			> Supported platforms: All;

		> Supported healthbot version: 1.0.1
		> Detals:
		 Detects linecards CPU utilization threshold breaches in SRX cluster device and notifies when
		 anomalies are found.
		 Three inputs control detection
		
		   1) "buffer-usage-threshold" is the threshold that causes the rule to report
		      an anomaly. By default, it's 80% of CPU utilization. This rule will set
		      a dashboard color to red when FPC CPU utilization exceed high threshold
		
		   2) "cpu-usage-threshold" is the threshold that causes the rule to report
		      an anomaly. By default, it's 80% of CPU utilization. This rule will set
		      a dashboard color to red when FPC CPU utilization exceed high threshold
		   3) "heap-usage-threshold" is the threshold that causes the rule to report
		      an anomaly. By default, it's 80% of CPU utilization. This rule will set
		      a dashboard color to red when FPC CPU utilization exceed high threshold
### Rule name: check-fpc-utilization-information 
		> Description: "Monitors FPC buffer, heap and cpu utilization"
		> Synopsis: "Linecard FPC, heap and CPU analyzer"
		> Rule file name: fpc-utilization.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: fpc-utilization.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-ithrottle-statistics 
		> Description: "Monitors throttle statistics such as adjacency ups and downs, starts and stops, disables and enables"
		> Synopsis: "Throttle statistics analyzer"
		> Rule file name: ithrottle-id.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: ithrottle.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-pci-error-counters 
		> Description: "Monitors the PCI link status"
		> Synopsis: "PCI invalid status analyzer"
		> Rule file name: pci-error.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: pci-error.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-cm-events 
		> Description: "Collects CM errors and count periodically and notifies when error count increases"
		> Synopsis: "CM error analyzer"
		> Rule file name: cm-events.rule

		> Supported products: MX 

			> Supported platforms: [ MX240 MX480 MX960 MX2010 MX2020 ];

		> Supported healthbot version: 1.0.1
		> Detals:
		 Detects CM (chassis manager) errors on linecards and notifies when anomalies
		 are found.
		 One input control detection
		
		   1) "cm-error-threshold-variable" is the threshold that causes the rule to report
		      an anomaly.  By default it's 1. This rule will set a dashboard
		      color to red when any of the CM error count increases are greater than
		      'cm-error-threshold-variable' for 3m period. If it sees any CM error count
		      increase for a period of less than 3m, it'll turn the color to yellow,
		      otherwise color is set to green.
### Rule name: check-center-chip-pt-entries 
		> Description: "Monitors the center chip packet table wan & fabric entries"
		> Synopsis: "Center chip packet statistics analyzer"
		> Rule file name: pt-statistics.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: chip.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: update-online-fpc 
		> Description:  "collects online fpc using udf and updates dependent rules sensor table"
		> Synopsis: "collects online fpc using udf and updates dependent rules sensor table"
		> Rule file name: online-fpc.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: online_fpc.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
		 These two rules are used to collect online FPCs in network device and update dependent yml files
### Rule name: check-fpc-cpu-memory-usage-netconf 
		> Description: "Collects system FPC CPU statistics periodically and notifies anomalies when CPU utilization exceed threshold"
		> Synopsis: "FPC CPU analyzer"
		> Rule file name: fpc-cpu-memory-state-netconf.rule

		> Supported products: SRX 

			> Supported platforms: All;

		> Supported healthbot version: 1.0.1
		> Detals:
		 Detects linecards CPU utilization threshold breaches and notifies when
		 anomalies are found.
		
		   1) "buffer-usage-threshold" is the threshold that causes the rule to
		       report an anomaly. By default it's 80% of CPU utilization. This
		       rule will set a dashboard color to red when FPC CPU utilization
		       exceed high threshold
		   2) "cpu-usage-threshold" is the threshold that causes the rule to report
		      an anomaly. By default it's 80% of CPU utilization. This rule will set
		      a dashboard color to red when FPC CPU utilization exceed high threshold
		   3) "heap-usage-threshold" is the threshold that causes the rule to report
		      an anomaly. By default it's 80% of CPU utilization. This rule will set
		      a dashboard color to red when FPC CPU utilization exceed high threshold
### Rule name: check-fpc-memory 
		> Description: "Collects system FPC memory statistics periodically and notifies anomalies when heap and buffer utilization exceed threshold"
		> Synopsis: "FPC memory analyzer"
		> Rule file name: fpc-memory-utilization.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 

			> Supported platforms: [ MX240 MX480 MX960 MX2010 MX2020 ];
			> Supported platforms: MX150;
			> Supported platforms: [ PTX5000 PTX1000 PTX10000 ];
			> Supported platforms: [ QFX10000 QFX5200 ];
			> Supported platforms: QFX5100;
			> Supported platforms: QFX5120-48Y;
			> Supported platforms: EX9200;
			> Supported platforms: EX4650;
			> Supported platforms: EX4600;

		> Supported healthbot version: 1.0.1
		> Detals:
		 Detects linecards memory utilization threshold breaches and notifies when
		 anomalies are found.
		 Five inputs control detection
		
		   1) "fpc-slot-no" is a regular expression that matches the linecard
		      that you would like to monitor.  By default it's '0-20', which matches
		      FPC 0 to 20 linecards. Use something like '0-3' to match only specific
		      FPCs i.e. 0 to 3.
		
		   2) "fpc-buffer-high-threshold" is the threshold that causes the rule to
		      report an anomaly. By default it's 80% of memory buffer utilization.
		      This rule will set a dashboard color to red when FPC memory buffer
		      utilization exceed high threshold 'fpc-buffer-high-threshold' for a
		      period of 3 minutes.
		
		   3) "fpc-buffer-low-threshold" is the threshold that causes the rule to
		      report an anomaly. By default it's 50% of memory buffer utilization.
		      This rule will set a dashboard color to yellow when FPC memory buffer
		      utilization exceed low threshold 'fpc-buffer-low-threshold' for a
		      period of 3 minutes.
		   4) "fpc-heap-high-threshold" is the threshold that causes the rule to
		      report an anomaly. By default it's 80% of memory heap utilization.
		      This rule will set a dashboard color to red when FPC memory heap
		      utilization exceed high threshold 'fpc-heap-high-threshold' for a
		      period of 3 minutes.
		
		   5) "fpc-heap-low-threshold" is the threshold that causes the rule to
		      report an anomaly. By default it's 50% of memory heap utilization.
		      This rule will set a dashboard color to yellow when FPC memory heap
		      utilization exceed low threshold 'fpc-heap-low-threshold' for a
		      period of 3 minutes.
### Rule name: check-jnh-exceptions 
		> Description: "Monitors the jnh exception packets"
		> Synopsis: "JNH packet drop analyzer"
		> Rule file name: jnh-exceptions.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: jnh-exceptions.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-fpc-threads 
		> Description: "Monitors the CPU utilization by FPC threads"
		> Synopsis: "Linecard CPU usage analyzer"
		> Rule file name: fpc-threads.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: fpc-threads.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-pfe-discards 
		> Description: "Collects packet forwarding engine hardware discard statistics  and notifies when discard count increases"
		> Synopsis: "Packet forwarding engine hardware discard statistics analyzer"
		> Rule file name: check-pfe-discards.rule

		> Supported products: MX 

			> Supported platforms: All;

		> Supported healthbot version: 2.0.1
		> Detals:
		 Detects PFE discards and notifies when anomalies are found.
		 One inputs control detection
		
		   1) discard-count, is the threshold that causes the rule to report
		      an anomaly.  By default it's 1. This rule will set a dashboard
		      color to red when *all* the discards are greater than
		      'discard-count' for 75s. otherwise color is set to green.
### Rule name: check-center-chip-fabric-in-errors 
		> Description: "Monitors the center chip cell fabric-in cell timeouts,crc error packets,late cells,error cells and malloc drops"
		> Synopsis: "Center chip cell statistics analyzer"
		> Rule file name: fi-error.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: chip.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-center-chip-host-path 
		> Description: "Monitors the center chip hostpath drops"
		> Synopsis: "Center chip hostpath analyzer"
		> Rule file name: host-drops.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: chip.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
### Rule name: check-fpc-cpu-scheduler-info 
		> Description: "Monitors FPC CPU utilization"
		> Synopsis: "FPC CPU statistics analyzer"
		> Rule file name: scheduler-info.rule

		> Supported products: MX 
		> Supported products: PTX 
		> Supported products: QFX 
		> Supported products: EX 
		> Supported products: ACX 
		> Supported products: SRX 

			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
			> Supported platforms: All;
		> Helper files: scheduler-info.yml;
		> Supported healthbot version: 1.0.1
		> Detals:
