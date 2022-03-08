# Original optical setup

The table below lists the set of components reported in the original pyPhotometry manuscript, that can be used with the acquisition board for red/green two colour photometry experiments.

For assembly instructions see the [hardware user guide](../user-guide/hardware.md#assembly-instructions).

| Name                                                 | Quantity | Part                                                   | Supplier |
| ---------------------------------------------------- | -------- | ------------------------------------------------------ | -------- |
| Photoreciever                                        | 2        | Newport 2151 with lensed FC adapter                    | Doric    |
| 465nm   LED                                          | 1        | CLED_465                                               | Doric    |
| 560nm   LED                                          | 1        | CLED_560                                               | Doric    |
| Minicube                                             | 1        | FMC5_E1(450-490)_F1(500-540)_E2(550-580)_F2(600-680)_S | Doric    |
| Fiber patchcord:  LED - Minicube                     | 2        | MFP_200/220/LWMJ-0.48_0.3m_FCM-FCM                     | Doric    |
| Fiber patchcord:  Minicube - Photoreciever           | 2        | MFP_600/630/LWMJ-0.48_0.3m_FCM-FCM                     | Doric    |
| Fiber   patchcord: Rotary-sample                     | 1        | MFP_200/220/900-0.48_1m_FCM-MF1.25                     | Doric    |
| Pigtailed   rotary joint                             | 1        | FRJ_1x1_PT_200/230/LWMJ-0.48_1m_FCM_0.2m_FCM           | Doric    |
| FC-FC adapter                                        | 1        | ADAPTER_FC style 2                                     | Doric    |
| Optical breadboard 150x300mm metric                  | 1        | MB1530F/M                                              | Thorlabs |
| M6 - M3   thread adapter                             | 4        | MSA6/M                                                 | Thorlabs |
| Clamp   for minicube                                 | 1        | CL3/M                                                  | Thorlabs |
| Clamp for photodetector                              | 2        | MSC2 Clamping Fork for 1/4"-20 (M6) Cap Screw          | Thorlabs |
| Pillar   for photodetector                           | 2        | TRP14/M Ø12 mm Pedestal Pillar   Post                  | Thorlabs |
| M6 screw   12mm                                      | 4        | SH6MS12                                                | Thorlabs |
| USB A -   micro B cable 1.8m                         | 1        | 121-3251                                               | RS       |
| BNC   cable 0.3m: Photoreciever to acquisition board | 2        | 886-0706                                               | RS       |
| M3 screw   10mm                                      | 4        | 660-4636                                               | RS       |
| M3   spacer 3mm                                      | 4        | 161-3676                                               | RS       |
| M6 x   45mm                                          | 2        | 468-0133                                               | RS       |

# Updated optical setup

Since the pyPhotometry manuscript was published Doric have updated their line of Photometry equipment, introducing minicubes with integrated LEDs and Photodetectors.  We have not tested these ourselves but from the information online it looks like they are a simpler and more convenient solution than the original optical setup which likely also gives better signal quality.  Below is a list of components for a red/green two-color system using the updated components. 

| Description                                                  | Supplier | supplier part number                                        | Quanitity  |
| ------------------------------------------------------------ | -------- | ----------------------------------------------------------- | ---------- |
| Mini-cube with integrated LEDs and photodetectors            | Doric    | ilFMC5-G2_E1(460-490)_F1(500-540)_E2(555-570)_F2(580-680)_S | 1          |
| Pigtailed fiber optic rotary joint                           | Doric    | FRJ_1x1_PT_200-0.57_1m_FCM_0.15m_FCM                        | 1          |
| Rotary joint holder                                          | Doric    | Holder_FRJ_Small                                            | 1          |
| FC_FC adapter                                                | Doric    | ADAPTER_FC                                                  | 1          |
| Fiber patch cord 1m  (rotary to sample)                      | Doric    | MFP_200/230/900-0.57_1m_FC-MF1.25(F)_LAF                    | 1          |
| pyPhotometry board                                           | OEPS     | pyPhotometry                                                | 1          |
| BNC cable 1m                                                 | Farnell  | 2911072                                                     | 2          |
| M8 cable for LEDs 1m                                         | Farnell  | 3238565                                                     | 2          |

