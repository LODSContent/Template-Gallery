<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">
<div class="container">
    <div class="row" style="background-color: rgb(26,123,74) !important; width=100%; margin-bottom: 50px;">
        <div class="col-md-3"></div>
        <div class="col-md-6"
            style="color:rgb(255,255,255); font-size: 36px; vertical-align: bottom; font-family: 'Noto Sans JP', sans-serif;  text-align: center;  padding-top:60px ;">
            
                Lab Documentation
        </div>
        <div class="col-md-3" style="margin-right:-10px"><img
                src="https://lodmanuals.blob.core.windows.net/lms/CLabsInstTemplate/Skillable%20RO%20logo.png"
                " /></div>
    </div>
</div>
<style>
    div.page table {
        background-color:#ffffff
    }
</style>


<span id="toc"><h1 style="color:#1A7B4A;font-weight:bold">Table of Contents</h1></span>
  - [Virtual Machines Specifications](#virtual-machines "Virtual machines specifications")
  - [Networking Specifications](#networking "Networking specifications")
  - [Programs installed on VMs](#software "Software")
===


<span id="virtual-machines"><h1 style="color:#1A7B4A;font-weight:bold">Virtual Machines</h1></span>


||||||
|:--|:--|:--|:--|:--|
|**VMs**|**IP Addresses Assigned**|**Network**|**Link to Machine**|**Machine Type**|
|W10-Admin|192.168.10.4|LAN|[W10-Admin](https://labondemand.com/VirtualMachineProfile/173133)|Member Client|
|WS2019-DC01_NC|192.168.10.10|LAN|[WS2019-DC01_NC](https://labondemand.com/VirtualMachineProfile/173128)|Domain Controller|
|WS2019-SVR01_DM_NC|192.168.10.11|LAN|[WS2019-SVR01_DM_NC](https://labondemand.com/VirtualMachineProfile/173129)|Member Server|
|WS2019-SVR02_DM_NC|192.168.10.12|LAN|[WS2019-SVR02_DM_NC](https://labondemand.com/VirtualMachineProfile/173130)|Member Server|
|WS2019-SVR03_DM_NC|192.168.10.13|LAN|[WS2019-SVR03_DM_NC](https://labondemand.com/VirtualMachineProfile/173131)|Member Server|
|WS2019-SVR04_DM_NC|192.168.10.14|LAN|[WS2019-SVR04_DM_NC](https://labondemand.com/VirtualMachineProfile/173132)|Member Server|
|WS2019-WS1|192.168.10.15|LAN|[WS2019-WS1](https://labondemand.com/VirtualMachineProfile/174938)|Stand-Alone Server|
|W11-Admin2|192.168.10.21|LAN|[W11-Admin](https://labondemand.com/VirtualMachineProfile/178739)|Member Client|
|PfSense|192.168.10.1<br />DHCP|LAN<br />WAN|[PfSense](https://labondemand.com/VirtualMachineProfile/173127)|Router|

[Return to table of contents](#toc "Table of contents")

===
<span id="networking"><h1 style="color:#1A7B4A;font-weight:bold">LAN Network Settings</h1></span>

|||
|:--|:--|
|**Network ID**|192.168.10.0/24|
|**DNS Servers**|192.168.10.10|
|**Gateway**|192.168.10.1|

<span><h1 style="color:#1A7B4A;font-weight:bold">Network Diagram</h1></span>

!IMAGE[Hexelo network diagram](GC-Hexelo-Network.png)

[Return to table of contents](#toc "Table of contents")

===

<span id="software"><h1 style="color:#1A7B4A;font-weight:bold">Installed Software</h1></span>

## Programs Installed on all VMs: 

|Display Name|Display Version|Publisher|Install Date|     
|:-----------|:--------------|:---------|:--------|
|Microsoft Edge|94.0.992.50|Microsoft Corporation|20211016|
|Microsoft Edge Update|1.3.153.47|                                                      
|Microsoft Visual C++ 2015-2019 Redistributable (x64) - |14.29.30133 14.29.30133.0    |Microsoft Corporation|
|Microsoft Visual C++ 2015-2019 Redistributable (x86) - |14.29.30133 14.29.30133.0    |Microsoft Corporation|
|Microsoft Visual C++ 2019 X86 Additional Runtime - |14.29.30133     14.29.30133      |Microsoft Corporation      |20210920|
|Chocolatey GUI|0.19.0.0|Chocolatey|20210920|
|Python Launcher|3.9.7546.0|Python Software Foundation |20210920|
|Microsoft Visual C++ 2019 X86 Minimum Runtime - 14.29.30133|14.29.30133|Microsoft Corporation|20210920|

**Additional Programs on W11-Admin & SRV04_DM_NC**:  

Windows Terminal

[Return to table of contents](#toc "Table of contents")

===

