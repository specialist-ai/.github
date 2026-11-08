<p>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="logo-dark.svg">
    <img src="logo.svg" alt="Specialist" height="64">
  </picture>
</p>

Specialist is a research project at UC Berkeley. It lets you collect robot training data with nothing more than a handheld gripper and a few printed tags. A consumer 360° camera on each gripper records the task. After the session, the reconstruction pipeline turns each recording into a metric 6-DoF trajectory and gripper opening.

The robot carries an actuated gripper with the same fingers and camera position as the handheld one. Policies that learn only from handheld demonstrations run on the robot without retargeting. We open-source the full stack, from the gripper hardware to the policy on the robot.

[Website](https://specialist-ai.github.io/) · [Build guide](https://specialist-ai.github.io/specialist-docs/) · Paper (coming soon)

---

<table>
  <thead>
    <tr>
      <th align="center">Category</th>
      <th align="center">Repository</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"><b>Hardware</b></td>
      <td>
        <a href="https://github.com/specialist-ai/specialist_description">specialist_description</a><br>
        This package holds the URDF, MJCF and xacro models of both grippers, made from the Onshape CAD. MuJoCo and ROS 2 can load them directly.
      </td>
    </tr>
    <tr>
      <td align="center"><b>Data Collection</b></td>
      <td>
        <a href="https://github.com/specialist-ai/specialist">specialist</a><br>
        The reconstruction pipeline turns each recording into a metric 6-DoF trajectory and gripper opening. It runs after the session, so nothing needs to run while you collect.
      </td>
    </tr>
    <tr>
      <td rowspan="3" align="center"><b>Learning &amp; Simulation</b></td>
      <td>
        specialist_lerobot (coming soon)<br>
        This plugin brings the Specialist policy to the LeRobot ecosystem.
      </td>
    </tr>
    <tr>
      <td>
        specialist_bc (coming soon)<br>
        This repository trains a policy by behavior cloning on the reconstructed sessions. It exports each checkpoint to ONNX, and a C++ runtime runs it on the robot with TensorRT.
      </td>
    </tr>
    <tr>
      <td>
        <a href="https://github.com/specialist-ai/specialist_sim">specialist_sim</a><br>
        This simulated capture rig records demonstrations and evaluates policies in MuJoCo. It comes with two tasks, LEGO sorting and pick-and-place.
      </td>
    </tr>
    <tr>
      <td rowspan="4" align="center"><b>Robot Control</b></td>
      <td>
        <a href="https://github.com/specialist-ai/specialist_arm">specialist_arm</a><br>
        This stack runs the policy on a robot arm that carries the actuated gripper. It supports the I2RT YAM and the Franka Panda, and the same commands also run in MuJoCo.
      </td>
    </tr>
    <tr>
      <td>
        <a href="https://github.com/specialist-ai/specialist_sdk">specialist_sdk</a><br>
        This driver runs the actuated gripper from C++ or Python. A background thread drives the servo and applies the safety guards.
      </td>
    </tr>
    <tr>
      <td>
        <a href="https://github.com/specialist-ai/feetech_driver">feetech_driver</a><br>
        This minimal Linux driver talks to Feetech serial-bus servos, such as the STS3215 in the actuated gripper. It has a C++ library and Python bindings.
      </td>
    </tr>
    <tr>
      <td>
        <a href="https://github.com/specialist-ai/insta360_driver">insta360_driver</a><br>
        This reader streams one fisheye lens of the Insta360 X3 over USB with low latency. It can also publish the images to ROS 2.
      </td>
    </tr>
  </tbody>
</table>
