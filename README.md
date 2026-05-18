# Project Azazel  
Project Azazel is the name I've given my personal homelabbing project. Built to address my needs surrounding things such as storage space, media hosting services, and a technical environment to call my own, Project Azazel is meant to do all of that and more, with scalability in mind so that as my needs grow, so too will Azazel. This repository will serve as personal documentation as well as a public resource for those who are interested in homelabbing themselves
  
## Overview  
This project originally began as a way to repurpose parts leftover from upgrading my PC. I wanted to give those parts a second life outside of sitting in a random drawer or a landfill. Now it's become a passion project that includes the following:  
- Network attached storage  
- Media hosting  
- Remote access and monitoring  
- Subnetting, DNS, and DHCP configurations  
- Power redundancy  
- Data backups and redundancy  
- Network booting for testbenches  
- More to come as my needs grow  
  
## Rack Layout  
From top to bottom, my server includes the following:  
- 1U PDU  
- 1U 24 port patch panel  
- 1U fanless managed switch (TP-Link SG2428LP)  
- 2U drawer unit  
- 1U UPS (CyberPower CP700PFCRM1U)  
- 4U server chassis (Sliger CX-4712)  
  
## The Server; Azazel  
### Hardware  
- Intel Core i7 12700KF  
- ASRock B760 Pro RS/D4  
- RTX 3070  
- 48GB DDR4 RAM  
- 7TB of HDD storage, single redundancy (similar to RAID 5) 
- 500GB of NVMe storage for array caching in a mirrored configuration (similar to RAID 1). 
- SFP+ NIC for 10Gbps transfer speeds directly connected to my main PC  
- LSI SAS 9300-8i HBA for reliable high speed reads/writes to and from the array

Disclaimer: The CPU and GPU selected for this build are not the most power-efficient choices for my intended workload. However, these components were repurposed from a previous system upgrade to reduce costs and avoid unnecessary electronic waste. That being said, it also adds plenty of overhead should I decide to explore VMs or LLMs
  
### Software/Services  
- Unraid OS  
- Plex and Jellyfin for media hosting  
- Tailscale for remote access  
- iVentoy to host network booting
- Gmail-based server event notifications with archival alert logging
  
### Data Loss Prevention  
- Previously mentioned redundancy in my array and cache  
- External USB 3.0 SSD to store backups of:  
  - My main PC's boot drive (automatic, monthly)  
  - Unraid's boot USB (automatic, monthly)  
  - Appdata folder on the cache SSD (automatic, monthly)  
  - Recovery database  
  - Data recovery map
- The recovery database is a database built in SQLite that includes information on how to rebuild my data or configurations that either have no decent backup solution or none at all, including:  
  - All media including titles, release years, resolutions, and sub libraries  
  - Drive records including brand names, drive types, models, serial numbers, storage capacities, roles, in-system location, usage status (active or inactive), condition on acquisition, and installation date  
  - ISO file records including the kernel, OS name, version, and a download link
- The data recovery map is a markdown file that outlines in detail the following:  
  - Headers to categorize data recovery paths  
  - Multiple access routes should one of the NICs go down  
  - Steps to take to recover that data once the backup location has been reached
  
## The Network  
Due to the limitation of not having access to the main router in the house be it physical or administrative, I've been forced to get creative. Thus, my networking situation is as follows:  
- WiFi 7 router as the head of my personal subnet with a WiFi uplink to the main router  
- 24 port managed switch featuring gigabit speeds and 4 SFP ports  
- Custom CAT6a ethernet cables for all devices in my bedroom, terminated at a patch panel within the rack  
- Internal domain names for my PC and server for reliable server access  
  
## Living Space Accommodations  
Since my rack will be residing in my bedroom for the foreseeable future, I've taken the following measures to ensure I can still live comfortably  
- Fanless switch  
- Quiet UPS  
- 4U chassis to allow plenty of room for 120mm fans, which are vastly quieter than traditional server fans  
- 3D printed shrouds to cover any lights, such as the light on my PDU power switch for example  
- Disk spindown in Unraid to reduce heat produced by the array  
- CPU undervolt to limit heat output  

## To Conclude...
As of today, this is as far as this project has gone. However, that's not to say I'm finished. Azazel has been specifically designed to grow alongside me, so stay tuned for any and all future upgrades that Azazel has yet to receive
