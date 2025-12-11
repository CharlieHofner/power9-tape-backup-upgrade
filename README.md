# power9-tape-backup-upgrade
Rapid upgrade from IBM TS3100 to TS4300 tape library for Power 9 environment. Self-installed in 9 days (Feb 2025), 40 LTO-8 tapes, and integrated Iron Mountain weekly vaulting.

# IBM TS4300 Tape Library Upgrade Project

**Project Owner/Author**: Charlie Hofner  
**LinkedIn**: [LinkedIn](https://www.linkedin.com/in/charlie-hofner/)  
**Timeline**: Ordered February 5, 2025; Installed and operational by February 14, 2025  

This project upgraded a failed IBM TS3100 legacy tape library (used for IBM Power 9 backups) with a modern TS4300 base model (3573-L8U, 3U rack-mount). The upgrade addressed mechanical failures (e.g., motor/gear issues causing tape magazine jams) and significantly enhanced capacity, reliability, and disaster recovery capabilities for a 2-week onsite rotation with weekly offsite vaulting.

## Key Components and Capacity
- **Tape Library**: IBM TS4300 base module (up to 40 data cartridge slots + 5-slot I/O station)
- **Tapes Purchased**: 40 IBM LTO Ultrium 8 tapes (12 TB native / up to 30 TB compressed each, assuming 2.5:1 compression)
  - Total native capacity: ~480 TB
- **Cleaning Tapes**: Two universal LTO cleaning cartridges (one placed at the end of each 20-slot magazine)
- **Media**: Official IBM-branded Ultrium 8 for optimal compatibility and error rates

## Backup Rotation and Offsite Strategy
The CTO specified a **2 business week** (10 backup days) onsite retention before rotation. Combined with **weekly pickups by Iron Mountain**, this implements a robust 3-2-1 backup strategy:
- Weekly driver swaps ensure tapes are quickly moved offsite
- Typical active rotation uses ~10–14 tapes (dailies + weeklies), leaving 26+ as spares/hot swaps/offsite sets
- Pushing to 3 weeks would require ~15–20 tapes, well within the library's capacity (38 data slots when reserving 2 for cleaning)

Iron Mountain offsite storage provides critical disaster recovery protection against building-level incidents (fire, flood, theft, etc.). The closure of the Port Washington, NY branch shifted vaulting to New Jersey, increasing delivery times due to distance and traffic from the Hauppauge, NY office (approximately one hour east of Manhattan). This extended recovery timeline has been noted in DR planning.

Backup operations leverage BRMS on IBM i, with Iron Mountain's barcode tracking integrating seamlessly with TS4300 labels.

## Self-Installation and Cost Savings
The installation was performed in-house, avoiding external managed services fees (typically $1,000+ for rack-and-stack). Key steps included:
- Racking the 3U unit with included rails
- Cabling (power, SAS/FC, Ethernet)
- Power-on and robotic calibration (~10 minutes)
- Firmware update (initially provided on DVD; copied to USB for application)
- IP configuration and initial setup via the Operator Panel LCD
- Completion of setup wizard, magazine loading, and Library Verify test

The DVD-delivered firmware highlighted legacy practices common in air-gapped tape environments, but future updates can be performed securely over the web UI using downloads from Lenovo/IBM Fix Central.

## Cleaning Tape Management Best Practices
- Cleaning tapes placed at the end of each magazine for easy identification
- **Recommendation**: Enable Auto Clean in the web UI (Actions → System → Auto Clean → Enable) for automatic drive maintenance
- **Optional Enhancement**: Mark dedicated cleaning slots in the web UI to hide them from hosts and prevent accidental overwrite
- Monitor remaining cleans via the web GUI and replace based on usage rather than fixed intervals

## Outcome
The TS4300 + Iron Mountain solution delivers a modern, reliable, and secure tape backup environment—positioned for years of service with improved performance over the legacy TS3100. The rapid timeline (ordered February 5, operational by February 14, 2025) and DIY installation further maximized value and minimized downtime.

This upgrade ensures continued high-reliability backups for the IBM Power 9 environment while strengthening disaster recovery posture.
