# AGENTS.md

## Workspace Purpose

This ROS 2 workspace is for learning:

- TF
- URDF
- RViz
- Gazebo

The main goal is learning and understanding, not just producing finished code.

## Teaching Style

When helping in this workspace:

- Explain changes in beginner-friendly language.
- Prefer step-by-step reasoning over terse answers.
- Describe what each ROS 2 concept, file, node, launch file, or command does.
- Point out how the pieces connect: TF frames, URDF links/joints, RViz displays, Gazebo simulation, and ROS topics.
- Avoid dumping large code changes without explaining the purpose.
- When practical, show the smallest useful example first, then build on it.
- If there are multiple valid approaches, explain the tradeoff briefly.

## Running ROS 2 Projects

Prefer running projects through launch files and helper shell scripts.

A typical run script should:

```bash
#!/usr/bin/env bash
set -e

source /opt/ros/$ROS_DISTRO/setup.bash
source install/setup.bash

ros2 launch <package_name> <launch_file>.launch.py
```

Guidelines:

- Use launch files for normal project execution.
- Use `.sh` scripts to automate environment setup and launch commands.
- Source both the ROS 2 environment and the workspace before launching.
- Avoid asking the user to manually run long setup command sequences when a script can encode them.
- Do not rely on direct `ros2 run` commands unless debugging a specific node.

## Build And Verification

Use:

```bash
source /opt/ros/$ROS_DISTRO/setup.bash
colcon build --symlink-install
```

After building, source:

```bash
source install/setup.bash
```

When changing code, run the narrowest relevant check first, then run a workspace build when practical.

For packages with tests, use:

```bash
colcon test
colcon test-result --verbose
```

## Workspace Conventions

- Keep ROS 2 packages under `src/`.
- Do not edit generated `build/`, `install/`, or `log/` directories.
- Prefer focused, learning-oriented examples over large abstractions.
- Use clear file and package names that reflect the concept being learned.
- Keep launch files, RViz configs, URDF/Xacro files, and Gazebo worlds organized by package.
