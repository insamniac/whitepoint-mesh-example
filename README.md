
### Using OpenDroneMap with ROV video


1. Create a sample project from this template.
```bash
git clone https://github.com/insamniac/whitepoint-mesh-example.git example1
cd example1
```


2. Find a section of video we want to use

GP010036.MP4  05:15 - 05:20



3. Extract frames and crop the bottoms (the camera is in the way)
    | (this can be skipped if you want to use the supplied images)
```bash
ffmpeg -i ../GP010036.MP4 -ss 05:15 -t 00:00:05 -vf "crop=in_w:in_h-384:0:0,fps=3" -qscale:v 1 images/frame%05d.jpg
```


4. Run ODM!

```bash
docker run -it --rm -v "$(pwd)/images:/code/images" -v "$(pwd)/ortho:/code/odm_orthophoto" -v "$(pwd)/textures:/code/odm_texturing" opendronemap/odm
```



5. Install meshlab
```bash
sudo apt-get install meshlab
meshlab
```


6. Your Turn!

- How do we make better meshes? 
- How can we combine them?
- [Camera Calibration|https://github.com/OpenDroneMap/CameraCalibration.git]




