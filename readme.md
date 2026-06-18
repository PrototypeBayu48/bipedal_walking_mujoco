## Acknowledgements

This project was originally built upon the capture point demonstration in [the5439workshop/Bipedal_walking_capture_point](https://github.com/the5439workshop/Bipedal_walking_capture_point). 

## How to Run

To run the code, simply run one of the files called `capture_point_...` depending on what robot you want to test. I would recomend starting with the `capture_point_2d.py`. If you understand how the minimal 2d version works, the others are simply an extension of the same principles.

Here is a list of the different simulations you can run:

*   `capture_point_2d.py`: A simple 2D biped. The best place to start.
*   `capture_point_3d.py`: A simple 3D biped.
*   `capture_point_3d_5dof_leg.py`: A 3D biped with 5-DOF legs.
*   `capture_point_3d_feet.py`: A 3D biped with feet.
*   `capture_point_robot.py`: The full robot model. You can control it with your keyboard (or an Xbox controller if you have pygame installed). Use the arrow keys to move and 'q' and 'e' to turn.

The parameters are not perfectly tuned and better performance can definilty be achived. More functions, such as rolling foot contact could be added for faster walking, or a standing controller for the robots with feet.

---

## Setup with Conda (Recommended)

It is recommended to use a `conda` environment to install the dependencies and run the project. This will ensure that the project has its own isolated environment with the correct package versions.

1.  **Create a new conda environment:**
    ```bash
    conda create --name bipedal-walking python=3.11
    ```

2.  **Activate the environment:**
    ```bash
    conda activate bipedal-walking
    ```

3.  **Install Pinocchio:**
    The `pinocchio` library is best installed from the `conda-forge` channel.
    ```bash
    conda install -c conda-forge pinocchio
    ```

4.  **Install other dependencies:**
    The rest of the packages can be installed using `pip` and the `requirements.txt` file.
    ```bash
    pip install -r requirements.txt
    ```

---

## About the Files

Each robot has its own xml file and a urdf, which yes is redunent. The urdf is only used with `pinocchio` to get the jacobian of each leg. The velocity controllers in `mujoco` can get unstable if you use to high gains, then you need to make the simulation step time smaller.

*   **`capture_point_*.py`**: These are the main simulation files.
*   **`get_jacobian_*.py`**: These files are used to get the Jacobians for the different robots.
*   **`utils.py`**: This file has a bunch of helper functions for things like checking for contact, handling controller input, and drawing things in the simulation.
*   **`xml_files/`**: This is where the MuJoCo and URDF models for the robots are stored.
*   **`meshes/`**: The 3D models for the robot parts.

If you publish any project using this code, it would be nice to have #The5439Workshop in the description, mostly to see if anyone is using it or for what.

---

## Dependencies

This project requires several python packages. It is highly recommended to install them in a `conda` environment as described in the "Setup with Conda" section.

The core dependencies are:
*   `pinocchio` (for robot kinematics)
*   `mujoco` (for physics simulation)
*   `numpy` (for numerical computation)
*   `pynput` (for keyboard control)
*   `pygame` (optional, for Xbox controller)
*   `usd-core` (optional, for recording simulations to a .usd file)
*   `Pillow` (for image processing, a dependency for some of the other libraries)

The versions used during development were:
```
python 3.11
mujoco 3.4
numpy 2.3.5
pinocchio 3.8.0
pynput
```
and if you want xbox controller, then you also will need `pygame`.
