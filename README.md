# Satellite Aerial Image Retrieval
Download jpeg images from Bing, no credentials are required. Note that images may include annotations such as street names.

```bash
python3 ProbeMapMatching.py lat1, lon1, lat2, lon2,
```

where (lat1, lon1) is the latitude and longitude of the upper-left coordinate, and (lat2, lon2) is the latitude and longitude of the lower-right coordinate. Use QGIS with Bing layer in `EPSG:4326` to find these. The script tolerates arbitrary coordinates input, as long as the two coordinates are diagonal. The retrieved image will be stored in `.\output` folder. The name of the image will follow the 'aerialImage_{}.jpeg' ending with the retrieval level. 

1. Eiffel Tower:

```bash
python3 aerialImageRetrieval.py 48.859261 2.293362 48.856953 2.296194
```

<p align="center">
<img src="https://github.com/robmarkcole/Satellite-Aerial-Image-Retrieval/blob/master/output/Eiffel_Tower.jpeg" width="500">
</p>

2. Random London suburb:

```bash
python3 aerialImageRetrieval.py  51.388 -0.2598 51.393 -0.2538
```

<p align="center">
<img src="https://github.com/robmarkcole/Satellite-Aerial-Image-Retrieval/blob/master/output/london_suburb.jpeg" width="500">
</p>

### Source Files:
1. `tilesystem.py`:
  This module implements a set of static methods used for Bing maps tile system. All the methods in sample C# code in https://msdn.microsoft.com/en-us/library/bb259689.aspx, have been implemented by my own understanding.
2. `aerialImageRetrieval.py`:
  This module is used to retrieve satellite/aerial image. Given a bounding box, which is composed of left up corner coordinate (latitude, longitude) and right down corner coordinate (latitude, longitude). Return an aerial imagery (with maximum resolution available) downloaded from Bing map tile system. The aerial image will be strictly cropped based on the size of bounding box. Also, if the given bounding box is too large and with the maximum resolution available, the retrieval image could be too large. So I set a maximum image size (8192 * 8192 pixels), approximately 256MB, to filter too large images.

## Setup
* `python3 -m venv venv`
* `source venv/bin/activate`
* `pip install -r requirements.txt`







