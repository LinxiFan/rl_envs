# RL Envs


## DM Control

### Installation

1. Request a free "Personal Student" license from [Mujoco simulator website](https://www.roboti.us/license.html). It will be valid for one year. 

2. Install [OpenAI Gym](https://github.com/openai/gym).

3. Follow the instructions on Github to install `dm_control`: https://github.com/deepmind/dm_control

    1. If you are using Mac OS X but cannot install `dm_control` successfully, consider using [Docker](https://www.docker.com/why-docker). Think of it as a lightweight "virtual machine" that can run Ubuntu on your Mac without much overhead. Read the tutorials on how to write a `Dockerfile` and run the container.  
    
    2. You can also use [Google CoLab](https://colab.research.google.com/) that provides free access to linux and GPU. This is recommended if your laptop/desktop does not have enough computing power. 

4. Copy over `dmc_wrapper.py` in this package to your project. 


### Usage

Use the included `make_visual_benchmark()` to create a standardized DMControl Gym environment with image observation modality. Please use the default argument values. 

Important Note:

1. The returned observation is a `uint8` numpy array of the image observation. Don't forget to scale it to floats between `[0., 1.)`

2. The created environment instance has properties `observation_space` and `action_space`. Please refer to OpenAI Gym's API. Don't forget to clamp your actions to fit the allowable `action_space`.

3. All supported tasks are recorded in `dmc_wrapper.ALL_TASKS`. They can be specified either as a tuple `('cartpole', 'balance')` or as a single string `cartpole_balance`.

