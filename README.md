# Caldor Fire Burn Scar Analysis Using Remote Sensing

## Project Overview

This project analyzes burn scars from the **2021 Caldor Fire in California** using satellite imagery and remote sensing techniques. Landsat imagery and Google Earth Engine were used to detect vegetation loss and map burn severity following the wildfire.

The Caldor Fire was one of the most destructive wildfires in California during the 2021 wildfire season. The fire burned across the Sierra Nevada mountains between Sacramento and South Lake Tahoe and caused significant ecological and economic damage.

---

## Wildfire Background

The Caldor Fire burned from **August 14 to October 21, 2021**, lasting **69 days**.

Key statistics from the wildfire include:

- **221,775 acres burned**
- **1,005 structures destroyed**
- **782 residential homes destroyed**
- **203 minor structures destroyed**
- **18 businesses destroyed**
- **21 non-fatal injuries reported**
- Fire spread across **El Dorado, Alpine, and Amador counties**

Firefighting response included:

- **15,000 firefighters**
- crews from **five states**
- **10 helicopters used for suppression**

The total cost to extinguish the fire was approximately **$271 million**.

Understanding the spatial impact of fires like the Caldor Fire can help support wildfire response planning, environmental monitoring, and ecosystem recovery efforts.

---

## Study Area

Sierra Nevada mountain range between **Sacramento and South Lake Tahoe, California**.

---

## Data Sources

Satellite imagery used in this analysis:

Landsat 8 Collection 2 Tier 1  
Date: August 5, 2021 (Pre-fire)

Landsat 9 Collection 2 Tier 1  
Date: November 21, 2021 (Post-fire)

Imagery sources:

- USGS Earth Explorer  
- Google Earth Engine  

Bands used in the analysis:

1 Coastal Aerosol  
2 Blue  
3 Green  
4 Red  
5 Near Infrared  
6 Shortwave Infrared 1  
7 Shortwave Infrared 2

---

## Methodology

### Image Preprocessing

To improve the ability to detect vegetation changes in the post-fire image, bands were adjusted using the following combination:

- **Band 5 (Near Infrared)**
- **Band 4 (Red)**
- **Band 3 (Green)**

This band combination highlights vegetation health and allowed burned vegetation areas to be clearly identified.

---

## Supervised Classification

Two classification approaches were tested:

- Minimum Distance Classification
- Random Forest Classification

Land cover classes included:

- Water
- Forest
- Bare Soil / Urban
- Deforestation
- Bare Rock / Snow

Random Forest classification produced **higher classification accuracy** and better representation of the burn scar.

---

## Classification Results

| Classification Method | Overall Accuracy | Kappa |
|----------------------|------------------|------|
| Minimum Distance (Pre-Fire) | 0.95 | 0.92 |
| Random Forest (Pre-Fire) | **0.97** | **0.95** |
| Minimum Distance (Post-Fire) | 0.60 | 0.46 |
| Random Forest (Post-Fire) | **0.86** | **0.79** |

The Random Forest classification better captured the deforestation patterns caused by the wildfire.

---

## Burn Severity Detection

To further analyze burn scars, the **Normalized Burn Ratio (NBR)** was calculated.

NBR equation: 
NBR = (NIR - SWIR2)/(NIR + SWIR2)

Where:

- NIR = Near Infrared band
- SWIR2 = Shortwave Infrared band 2

The difference in burn ratio was then calculated using:
dNBR = NBR_before - NBR_after

Higher dNBR values indicate greater burn severity.

---

## Satellite Imagery

### Pre-Fire True Color Image

![Before Fire](maps/True_Color_Before.jpeg)

### Post-Fire True Color Image

![After Fire](maps/True_Color_After.jpeg)

---

## Random Forest Classification

### Pre-Fire Classification

![RF Before](maps/Random_fc_before.jpeg)

### Post-Fire Classification

![RF After](maps/Random_fc_After.jpeg)

---

## Burn Severity Map

The difference in normalized burn ratio highlights areas where vegetation was destroyed by the wildfire.

![Burn Severity](maps/IMG_0294.jpeg)

---

## Key Findings

- Large areas of forest were destroyed by the Caldor Fire.
- Random Forest classification produced more reliable results than minimum distance classification.
- The dNBR method successfully identified burn severity zones across the study area.
- Snow cover in the post-fire imagery caused some classification noise but did not affect burn scar identification.

---

## Applications

This workflow demonstrates how remote sensing can support:

- wildfire damage assessment
- forest recovery monitoring
- environmental impact analysis
- disaster response planning

Satellite-based burn scar detection provides a cost-effective method for evaluating wildfire impacts over large geographic areas.

---

## Author

John Hartshorn
Foothill College
Geographic Information Systems Technology

