# Install Python

  * Download and install Anaconda Python from <https://www.continuum.io/anaconda>


# Setting up CUDA

  * Install Visual Studio 2015 Community Edition (CE) or higher

  * If you have an Nvidia GPU, install the following two libraries:
    1. CUDA SDK and Toolkit
    2. cuDNN Library

  * Add location of `cl.exe` to PATH
    * Create a system variable (e.g. CL_PATH -> C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin)
      * Add %CL_PATH% to PATH

  * Add location of `nvcc.exe` to PATH
    * Create s system variable (e.g. CUDA_PATH -> C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0)
      * Add %CUDA_PATH%\bin to PATH

  * Because Theano requires paths without spaces, we need to copy files from cuDNN install to a path w/o spaces
    1. Create an "include" folder in your home directory (e.g. C:/Users/n097912/CUDA/include)
    2. Copy files from C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\include to folder created in Step 1
    3. Create an "lib" folder in your home directory (e.g. C:/Users/n097912/CUDA/lib64)
    4. Copy files from C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0\lib\x64 to folder created in Step 3

  * (Optional) Install NVIDIA Nsight Visual Studio Edition


# Create a virtual environment using Python 2.7

  * See <https://conda.io/docs/user-guide/getting-started.html#managing-environments> for reference
  * Create conda environment
    ```
    conda create --name deepqrl python=2.7
    ```
  * Activate conda environment
   ```
   activate deepqrl
   ```


# OpenCV

  * Download and run the OpenCV 3.2 installer (which just extracts OpenCV to the folder of your choosing)
  * Add the OpenCV bin dir to PATH
  * Copy the cv2.pyd folder to the site-packages directory in your Anaconda environment


# Theano

  * Install requirements and optional packages

    ```
    conda install numpy scipy mkl-service libpython <m2w64-toolchain> <nose> <nose-parameterized> <sphinx> <pydot-ng>
    ```

  * Install Theano

    ```
    conda install theano
    ```

  * Configure Theano to use the CUDA SDK
    * Example .theanorc file contents:
      ```
      [global]
      floatX = float32
      device = gpu

      [dnn]
      include_path=C:/Users/n097912/CUDA/include
      library_path=C:/Users/n097912/CUDA/lib64
      ```


# Lasagne

  * Install the latest version for compatiblity with the latest version of Theano (see <https://github.com/aigamedev/scikit-neuralnetwork/issues/235>)

    ```
    pip install --upgrade https://github.com/Lasagne/Lasagne/archive/master.zip
    ```

# Pylearn2

  * Install pylearn2 package

    ```
    conda install pylearn2
    ```

# Arcade Learning Envirnoment    

  * Follow the instructions from Islandman93's port to build with Visual Studio: <https://github.com/Islandman93/Arcade-Learning-Environment>