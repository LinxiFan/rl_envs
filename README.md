# RL Envs

## Atari Games Suite

1. Please follow the official installation instructions from [OpenAI Gym](https://github.com/openai/gym#installation) with Atari support. The following command should suffice:

    ```bash
    pip install 'gym[atari]'
    ```
   
   You also need to install OpenCV for python. If you use Anaconda, you can run:
   
   ```bash
   conda install -c conda-forge opencv
   ```

2. Copy `atari_wrapper.py` in this repo to your project. It is self-contained.

3. The relevant environment creation function is `make_atari_benchmark(game, train)`. `game` specifies the Atari game ID (e.g. `"enduro", "pong", "beam_rider"`). Set `train=True` for training and `train=False` for evaluation report. The only difference between training and evaluation is reward clipping. 

## DM Control

[Please ignore this section]

### Installation

1. Request a free "Personal Student" license from [Mujoco simulator website](https://www.roboti.us/license.html). It will be valid for one year. 

2. Install [OpenAI Gym](https://github.com/openai/gym).

3. Follow the instructions on Github to install `dm_control`: https://github.com/deepmind/dm_control

    1. If you are using Mac OS X but cannot install `dm_control` successfully, consider using [Docker](https://www.docker.com/why-docker). Think of it as a lightweight "virtual machine" that can run Ubuntu on your Mac without much overhead. Read the tutorials on how to write a `Dockerfile` and run the container.  
    
    2. You can also use [Google CoLab](https://colab.research.google.com/) that provides free access to linux and GPU. This is recommended if your laptop/desktop does not have enough computing power. 

4. Copy over `dmc_wrapper.py` in this package to your project. 

5. Set the `ENTRYPOINT` variable in `dmc_wrapper.py` to point to your project module path.


### Usage

Use the included `make_visual_benchmark()` to create a standardized DMControl Gym environment with image observation modality. Please use the default argument values. 

Important Note:

1. The returned observation is a `uint8` numpy array of the image observation. Don't forget to scale it to floats between `[0., 1.)`

2. The created environment instance has properties `observation_space` and `action_space`. Please refer to OpenAI Gym's API. Don't forget to clamp your actions to fit the allowable `action_space`.

3. All supported tasks are recorded in `dmc_wrapper.ALL_TASKS`. They can be specified either as a tuple `('cartpole', 'balance')` or as a single string `cartpole_balance`.

