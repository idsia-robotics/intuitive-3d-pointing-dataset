[![DOI](https://zenodo.org/badge/268146753.svg)](https://zenodo.org/badge/latestdoi/268146753)

# Intuitive 3D Control of a Quadrotor in User Proximity with Pointing Gestures (Dataset)

The accompanying dataset and code for the ICRA 2020 publication:

B. Gromov, J. Guzzi, L. Gambardella, and A. Giusti, "Intuitive 3D Control of a Quadrotor in User Proximity with Pointing Gestures," in 2020 IEEE International Conference on Robotics and Automation (ICRA), 2020.

The dataset contains a log of user actions and states of the system collected during the user study. The subjects had to fly a nano quadcopter (Bitcraze Crazyflie 2.0) between three targets placed at different heights by using a conventional joystick interface (Logitech F710) and pointing. The pointing is reconstructed using an inertial sensor (mbientlab MetaWearR+) placed on the user's wrist.

## Authors

- Boris Gromov (ORCiD: https://orcid.org/0000-0003-2380-483X)
- Jérôme Guzzi (ORCiD: https://orcid.org/0000-0002-1263-4110)
- Luca Gambardella
- Alessandro Giusti

## Date of collection

February 2019

## Files

 1. `icra2020_data_processing.ipynb`

    The file is an IPython (Jupyter) Notebook that contains an example code to process the data. The code can be used to reproduce the results presented in the paper.

 2. `icra2020_complete_anonymized.pkl`

    The file is encoded using the standard Python `pickle` library and represents a Python dictionary with the following keys:

    - `data` A `pandas.DataFrame` indexed by time, contains the following columns:
      - `gt_x`, `gt_y`, `gt_z` Position of the quadrotor acquired with a MOCAP system;
      - `h_x`, `h_y`, `h_z` Position of the user's head acquired with a MOCAP system;
      - `p_x`, `p_y` Pointed-at location on the ground plane;

    - `moves` A `pandas.DataFrame` indexed by time, provides time indices to slice `data`. Contains the following columns:
      - `user_id` Anonymized user ID (string);
      - `session_id` Session ID (integer);
      - `interface` Type of interface used (string), either `POINTING` or `JOYSTICK`;
      - `target` Target ID (integer), see `targets` below;
      - `t0`, `t1` Time indices of the start and the end of the segment flown to `target`;
      - `duration` Time passed between `t0` and `t1`;

    - `shapes` A list of `pandas.DataFrame`. Each data frame is indexed by time and corresponds to a `POINTING` session in the `moves` data frame (see above). Each data frame has a single column `ws_shape` (string) and can take either `WORKSPACE_CYLINDER` or `WORKSPACE_XY_PLANE` value.

    - `target` A `pandas.DataFrame` indexed by the target ID. Contains corresponding `x`, `y`, and `z` coordinates of the targets.

## License

Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)
