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

## Conclusion
As discussed previously, it is possible to use optical and radar data to track these growing stages over time. Optical data will tell us about the "greenness" of the plant and radar data will tell us about the "structure" of the plant. For example, peak "greenness" occurs before full plant maturity as the rice grain is formed prior to harvest. In the case of "structure", which can be measured with radar data, we are able to see differences in scattering at the various growth stages. Early stages might see less scattering due to reflections from background soil or flooded fields. The peak flowering stage may see maximized scattering due to dense foliage, whereas, the ripening stage prior to harvest may see a drop in scattering due to rice tassel formation and "layover" of the plant. In the end, there will be differences between the optical and radar phenology, but it is still possible to relate this data to the growth stages and build a good yield model. 

## What should you do? What do you get?
Level 1, Finding rice crops
1. consider the time series variations in satellite data bands or statistical combinations of bands
2. carefully decide how many pixels should be include in a window
3. clouds data should be filtered in Sentinel-2(optical).

1. location of rice crops and the locations of non-rice crops(forest, other vegetation, water)
2. Sample Notebook for Landsat, Sentinel-2(Optical), Sentinel-1(Radar)