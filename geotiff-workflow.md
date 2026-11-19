# GeoTIFF and raster workflow

The general inference notebook and GeoTIFF notebook serve different input paths. The GeoTIFF notebook uses Rasterio to load raster bands and record CRS, affine transform, bounds, pixel resolution, and NoData metadata. The configured TIFF band is 1 unless changed. It standardizes data for model input, runs overlapping tiles at the training-matched 256 px scale and a 512 px context scale, maps predictions back to source-image coordinates, and suppresses duplicate detections using overlap and diameter criteria.

Per-file errors, metadata, raw tile predictions, merged candidates, and annotated images are exported by the notebook. Review those outputs for every new source; a successful image read does not prove that the source imagery is calibrated or scientifically comparable to training data.

The project notes describe an earlier failure on metadata-bearing GeoTIFF imagery and a dedicated Rasterio workflow as the attempted resolution. Do not claim universal GeoTIFF compatibility or a fully validated fix without a successful end-to-end run on the relevant input files. Tiling cost grows with image dimensions and overlap. Smaller tiles may reduce compute but may also alter crater context and prediction quality; measure the trade-off.
