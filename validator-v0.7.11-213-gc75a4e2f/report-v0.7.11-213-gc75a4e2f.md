# v0.7.11-213-gc75a4e2f

## Build Info

   - `kepler_exporter_build_info{arch="amd64", instance="kepler-metal:8888", job="metal", os="linux"}`
   - `kepler_exporter_build_info{arch="amd64", branch="main", instance="vm:9100", job="vm", os="linux", revision="bf1f62d8c580aa742d4ae90dedaff70044be9b78", version="v0.7.11"}`
## Node Info

   - `kepler_node_info{components_power_source="rapl-sysfs", cpu_architecture="Skylake", instance="kepler-metal:8888", job="metal", platform_power_source="none", source="os"}`
   - `kepler_node_info{components_power_source="estimator", cpu_architecture="Skylake", instance="vm:9100", job="vm", platform_power_source="none", source="os"}`
## Machine Specs

### Host

| Model | Sockets | Cores | Threads | Flags |
| --- | --- | --- | --- | --- |
| Intel(R) Core(TM) i7-6820HQ CPU @ 2.70GHz | 1 | 8 | 2 | `fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb pti ssbd ibrs ibpb stibp tpr_shadow flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp vnmi md_clear flush_l1d arch_capabilities` |
### VM

| Model | Sockets | Cores | Threads | Flags |
| --- | --- | --- | --- | --- |
| Intel Core Processor (Skylake, IBRS) | 2 | 2 | 1 | `fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss syscall nx pdpe1gb rdtscp lm constant_tsc rep_good nopl xtopology cpuid tsc_known_freq pni pclmulqdq vmx ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch cpuid_fault pti ssbd ibrs ibpb stibp tpr_shadow flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves arat vnmi umip md_clear flush_l1d arch_capabilities` |
## Validation Results

   - Started At: `2024-09-10 08:36:05`
   - Ended   At: `2024-09-10 08:42:52`
   - Duration  : `0:06:47`
## Validations

### Summary

| Name | MSE | MAPE | Pass / Fail |
| --- | --- | --- | --- |
| [node-rapl - kepler-package](#node-rapl---kepler-package) | 0.44 | 2.31 | PASS |
| [platform - absolute](#platform---absolute) | 3116.73 | 1877.99 | PASS |
| [package - absolute](#package---absolute) | 2872.41 | 4682.08 | PASS |
| [core - absolute](#core---absolute) | 2965.53 | 13225.01 | PASS |
| [platform - dynamic](#platform---dynamic) | 92.46 | 100.00 | PASS |
| [package - dynamic](#package---dynamic) | 59.66 | 100.00 | PASS |
| [core - dynamic](#core---dynamic) | 46.42 | 100.00 | PASS |
| [dram - dynamic](#dram---dynamic) | 0.00 | 100.00 | PASS |
| [platform - idle](#platform---idle) | 3936.43 | 9671.42 | PASS |
| [package - idle](#package---idle) | 3508.86 | 73767.53 | PASS |
| [core - idle](#core---idle) | 3518.03 | 1977100.00 | PASS |
| [dram - idle](#dram---idle) | 203.27 | 181190.61 | PASS |
### Details

#### node-rapl - kepler-package


**Queries**:
   - Actual  (node-rapl) : [`sum( rate( node_rapl_package_joules_total[20s] ) )`](artifacts/node-rapl-node_rapl_package_joules_total--absolute.json)
   - Predicted (kepler-package) : [`sum( rate( kepler_node_package_joules_total{ job="metal", }[20s] ) )`](artifacts/kepler-package-kepler_node_package_joules_total--absolute.json)

**Results**:
   - MSE  : `0.44`
   - MAPE : `2.31 %`

**Charts**:
![node-rapl - kepler-package](images/node-rapl-vs-kepler-package-node_rapl_kepler_package.png)
#### platform - absolute


**Queries**:
   - Actual  (metal) : [`sum( rate( kepler_process_platform_joules_total{ job="metal", pid="2433120", }[20s] ) )`](artifacts/metal-kepler_process_platform_joules_total--absolute.json)
   - Predicted (vm) : [`sum( rate( kepler_node_platform_joules_total{ job="vm", }[20s] ) )`](artifacts/vm-kepler_node_platform_joules_total--absolute.json)

**Results**:
   - MSE  : `3116.73`
   - MAPE : `1877.99 %`

**Charts**:
![platform - absolute](images/metal-vs-vm-platform_absolute.png)
#### package - absolute


**Queries**:
   - Actual  (metal) : [`sum( rate( kepler_process_package_joules_total{ job="metal", pid="2433120", }[20s] ) )`](artifacts/metal-kepler_process_package_joules_total--absolute.json)
   - Predicted (vm) : [`sum( rate( kepler_node_package_joules_total{ job="vm", }[20s] ) )`](artifacts/vm-kepler_node_package_joules_total--absolute.json)

**Results**:
   - MSE  : `2872.41`
   - MAPE : `4682.08 %`

**Charts**:
![package - absolute](images/metal-vs-vm-package_absolute.png)
#### core - absolute


**Queries**:
   - Actual  (metal) : [`sum( rate( kepler_process_core_joules_total{ job="metal", pid="2433120", }[20s] ) )`](artifacts/metal-kepler_process_core_joules_total--absolute.json)
   - Predicted (vm) : [`sum( rate( kepler_node_core_joules_total{ job="vm", }[20s] ) )`](artifacts/vm-kepler_node_core_joules_total--absolute.json)

**Results**:
   - MSE  : `2965.53`
   - MAPE : `13225.01 %`

**Charts**:
![core - absolute](images/metal-vs-vm-core_absolute.png)
#### platform - dynamic


**Queries**:
   - Actual  (metal) : [`rate( kepler_process_platform_joules_total{ job="metal", pid="2433120", mode="dynamic", }[20s] )`](artifacts/metal-kepler_process_platform_joules_total--dynamic.json)
   - Predicted (vm) : [`rate( kepler_node_platform_joules_total{ job="vm", mode="dynamic", }[20s] )`](artifacts/vm-kepler_node_platform_joules_total--dynamic.json)

**Results**:
   - MSE  : `92.46`
   - MAPE : `100.00 %`

**Charts**:
![platform - dynamic](images/metal-vs-vm-platform_dynamic.png)
#### package - dynamic


**Queries**:
   - Actual  (metal) : [`rate( kepler_process_package_joules_total{ job="metal", pid="2433120", mode="dynamic", }[20s] )`](artifacts/metal-kepler_process_package_joules_total--dynamic.json)
   - Predicted (vm) : [`rate( kepler_node_package_joules_total{ job="vm", mode="dynamic", }[20s] )`](artifacts/vm-kepler_node_package_joules_total--dynamic.json)

**Results**:
   - MSE  : `59.66`
   - MAPE : `100.00 %`

**Charts**:
![package - dynamic](images/metal-vs-vm-package_dynamic.png)
#### core - dynamic


**Queries**:
   - Actual  (metal) : [`rate( kepler_process_core_joules_total{ job="metal", pid="2433120", mode="dynamic", }[20s] )`](artifacts/metal-kepler_process_core_joules_total--dynamic.json)
   - Predicted (vm) : [`rate( kepler_node_core_joules_total{ job="vm", mode="dynamic", }[20s] )`](artifacts/vm-kepler_node_core_joules_total--dynamic.json)

**Results**:
   - MSE  : `46.42`
   - MAPE : `100.00 %`

**Charts**:
![core - dynamic](images/metal-vs-vm-core_dynamic.png)
#### dram - dynamic


**Queries**:
   - Actual  (metal) : [`rate( kepler_process_dram_joules_total{ job="metal", pid="2433120", mode="dynamic", }[20s] )`](artifacts/metal-kepler_process_dram_joules_total--dynamic.json)
   - Predicted (vm) : [`rate( kepler_node_dram_joules_total{ job="vm", mode="dynamic", }[20s] )`](artifacts/vm-kepler_node_dram_joules_total--dynamic.json)

**Results**:
   - MSE  : `0.00`
   - MAPE : `100.00 %`

**Charts**:
![dram - dynamic](images/metal-vs-vm-dram_dynamic.png)
#### platform - idle


**Queries**:
   - Actual  (metal) : [`rate( kepler_process_platform_joules_total{ job="metal", pid="2433120", mode="idle", }[20s] )`](artifacts/metal-kepler_process_platform_joules_total--idle.json)
   - Predicted (vm) : [`rate( kepler_node_platform_joules_total{ job="vm", mode="idle", }[20s] )`](artifacts/vm-kepler_node_platform_joules_total--idle.json)

**Results**:
   - MSE  : `3936.43`
   - MAPE : `9671.42 %`

**Charts**:
![platform - idle](images/metal-vs-vm-platform_idle.png)
#### package - idle


**Queries**:
   - Actual  (metal) : [`rate( kepler_process_package_joules_total{ job="metal", pid="2433120", mode="idle", }[20s] )`](artifacts/metal-kepler_process_package_joules_total--idle.json)
   - Predicted (vm) : [`rate( kepler_node_package_joules_total{ job="vm", mode="idle", }[20s] )`](artifacts/vm-kepler_node_package_joules_total--idle.json)

**Results**:
   - MSE  : `3508.86`
   - MAPE : `73767.53 %`

**Charts**:
![package - idle](images/metal-vs-vm-package_idle.png)
#### core - idle


**Queries**:
   - Actual  (metal) : [`rate( kepler_process_core_joules_total{ job="metal", pid="2433120", mode="idle", }[20s] )`](artifacts/metal-kepler_process_core_joules_total--idle.json)
   - Predicted (vm) : [`rate( kepler_node_core_joules_total{ job="vm", mode="idle", }[20s] )`](artifacts/vm-kepler_node_core_joules_total--idle.json)

**Results**:
   - MSE  : `3518.03`
   - MAPE : `1977100.00 %`

**Charts**:
![core - idle](images/metal-vs-vm-core_idle.png)
#### dram - idle


**Queries**:
   - Actual  (metal) : [`rate( kepler_process_dram_joules_total{ job="metal", pid="2433120", mode="idle", }[20s] )`](artifacts/metal-kepler_process_dram_joules_total--idle.json)
   - Predicted (vm) : [`rate( kepler_node_dram_joules_total{ job="vm", mode="idle", }[20s] )`](artifacts/vm-kepler_node_dram_joules_total--idle.json)

**Results**:
   - MSE  : `203.27`
   - MAPE : `181190.61 %`

**Charts**:
![dram - idle](images/metal-vs-vm-dram_idle.png)
