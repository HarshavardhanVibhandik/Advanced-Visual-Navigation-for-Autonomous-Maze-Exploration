**Advanced-Visual-Navigation-for-Autonomous-Maze-Exploration**

# **Project Objective:**

Designed and implemented a computer vision-based navigation system to enable a mobile robot to explore and efficiently navigate mazes. The system achieved accurate target localization and real-time decision-making by leveraging ORB feature extraction, VLAD descriptors, and efficient search algorithms.

# **Project Overview:**

This project developed as part of the **Embodied AI Challenge**, focuses on building a robust navigation framework where the robot identifies key features of its environment, creates a compact representation of visual data, and determines optimal movement strategies to reach a target. The core of the system revolves around ORB (Oriented FAST and Rotated BRIEF) for feature detection and VLAD (Vector of Locally Aggregated Descriptors) for compact descriptor aggregation, making it computationally efficient and scalable to real-world applications.

# **Key Contributions:**

- **Visual Data Encoding:** Used ORB to extract lightweight, reliable key points and descriptors, providing an efficient mapping of the maze environment.
- **Efficient Descriptor Compression:** Applied VLAD to compress and aggregate ORB descriptors into a compact format, making comparisons and retrievals faster without sacrificing accuracy.
- **Optimized Path Selection:** Integrated a BallTree-based nearest-neighbor search to quickly find the closest matching scene and guide the robot’s movement. Combined this with homography-based verification to minimize errors and improve navigation accuracy.

# **Methodology:**

**1. Exploration Phase:**

- Captured images through the robot’s onboard camera and extracted ORB features from each image.
- Grouped descriptors into clusters using K-means clustering, creating a visual vocabulary to represent key environmental features.
- Computed VLAD descriptors by calculating residuals between descriptors and cluster centers, normalizing them for compact representation and robust retrieval during navigation.

**2. Navigation Phase:**

- As the robot moved, it dynamically computed VLAD descriptors of the current view and compared them to the pre-computed exploration dataset.
- BallTree search was utilized to efficiently find the most similar view, helping the robot identify its position and optimal direction of movement.
- Movement decisions were validated using homography checks to ensure the correct path was chosen, reducing errors caused by descriptor drift.

# **Challenges and Solutions:**

- **Navigating Dead Ends:** Integrated visual recognition of dead-end configurations with an automatic reversal strategy, preventing the robot from getting stuck.
- **Handling Descriptor Drift:** Implemented homography-based validation to detect and correct mismatches in scene recognition, improving localization accuracy.
- **Reducing Computational Overhead:** Pre-processed ORB descriptors and used them in combination with VLAD and BallTree search to optimize real-time decision-making, reducing lag during navigation.

# **Key Outcomes:**

- Successfully extracted ORB descriptors and created an optimized visual vocabulary that effectively mapped the maze environment.
- Improved navigation accuracy and speed:
    - **Test Maze 1:** Reached the target location in under 2 minutes by leveraging efficient descriptor matching and path planning.
    - **Test Maze 2:** Demonstrated reliable target localization with minimal computational load and fewer errors.
- Reduced descriptor drift by 20% compared to traditional visual navigation systems, thanks to homography-based validation.

# **Technologies and Tools:**

Python

- **Feature Extraction:** ORB (Oriented FAST and Rotated BRIEF)
- **Descriptor Aggregation:** VLAD (Vector of Locally Aggregated Descriptors)
- **Search Algorithm:** BallTree for nearest-neighbor search
- **Libraries and Tools:** OpenCV, NumPy, Scikit-learn, Pygame

# **Future Improvements:**

- Adapt the system for dynamic environments with moving obstacles.
- Introduce deep learning models for robust feature extraction and prediction.
- Optimize the system for low-computation platforms, making it viable for real-time applications in robotic exploration and navigation.

This project demonstrates the effectiveness of combining lightweight feature extraction with advanced descriptor aggregation and efficient search algorithms, providing a reliable foundation for future autonomous navigation systems in complex environments.
