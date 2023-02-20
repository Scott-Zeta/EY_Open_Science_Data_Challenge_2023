# Goal?
Build a binary classification to recognize rice or non-rice.

# Indication tools
## NDVI (Normalized Difference Vegetation Index) (Optical)
NDVI (Normalized Difference Vegetation Index) = (NIR-Red) / (NIR+Red)
NIR is the reflectance value of the near-infrared band and RED is the reflectance value of the red band. And always between -1 to 1

This is an Indication about how "green" is a ground surface. close to 1 means well green and posssible well plants growth. Close to zero means barren/unhealthy/mature. Negative possible without plants(water, urban, snow)

So different plants can have different NDVI pattern in a year.
Sentinel-2 NDVI varies considerably for different crop types. Forests are stable and have high NDVI values. In the case of rice, it is easy to see its variability for double cropping cycles (2 per year, yellow line) and single cropping cycle (1 per year, grey line).

## RVI (Radar Vegetation Index) (Radar)
The Sentinel-1 data contains two basic polarization "bands", ```VV``` and ```VH```, with the first letter indicating the transmitted polarisation and the latter the received polarisation. 
The ```VV``` and ```VH``` bands give us surface backscatter at any location. This backscatter tells us about the "structure" of the crop, such as its growth progress from small plants to large plants, and then to bare soil after harvesting.

RVI (Radar Vegetation Index) = sqrt (1- VV / (VV+VH)) * 4 * (VH / (VV + VH))
is similar with NDVI, RVI observation can through the Cloud, but can be sensitive with the topography, where VH is the backscatter value in the VH polarization band and VV is the backscatter value in the VV polarization band.