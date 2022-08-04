# Conda Recipe
build locally like this:  
1. Download the 3 files `build.sh`, `meta.yaml` and `conda_build_config.yaml` 
2. create and activate a suitable conda environment (e.g. anaconda3)
3. install conda-build 
```bash
conda install conda-build
```
5. Download Mac-SDK and extract it to a folder of your chosing (here we use /opt/)
wget https://github.com/phracker/MacOSX-SDKs/releases/download/11.3/MacOSX11.3.sdk.tar.xz
sudo tar -xf MacOSX11.3.sdk.tar.xz -C /opt/
6. Adapt location of Mac-SDK in `conda_build_config.yaml` if you changed `/opt/` to something else
4. build locally (assuming you are in the directory where the two files are)
```bash
conda-build .
```

If succesful you get output like:
```bash
anaconda upload \
    /Users/runner/miniconda/envs/madtest/conda-bld/osx-64/madtequila-1.0-h2c9ce9a_0.tar.bz2
anaconda_upload is not set.  Not uploading wheels: []
{
  "madtequila-1.0-h2c9ce9a_0": {
    "recipe": {
      "CONDA_BUILD_SYSROOT": "/opt/MacOSX11.3.sdk",
      "cxx_compiler": "clangxx",
      "numpy": "1.16",
      "target_platform": "osx-64"
    }
  }
}
```

7. Send me the madness-1.0...tar.gz file and I'll put it on the cloud

6. install locally (optional) 
```bash
conda install --use-local madness
```
If you installed locally you need to install dependencies yourself
```bash
conda install numpy mpich boost
```
