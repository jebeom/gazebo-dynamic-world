# gazebo-dynamic-world

You can control how the obstacle moves (where and how much it moves over time) by modifying the contents of the animated_box_1.cc file.

Then, your CMakeLists.txt file should include the following content. 
```
add_library(animated_box_1 SHARED animated_box_1.cc)
target_link_libraries(animated_box_1 ${GAZEBO_LIBRARIES})
```
If you have renamed the **animated_box_1.cc file** or added a **new animated_box.cc file**, you **need to update the CMakeLists.txt file** accordingly.


After that, build the project. You will find the libanimated_box_1.so file in the build directory.

Finally, You can implement a dynamically moving box in Gazebo by adding the following code to your Gazebo world file.

```
   </model>
    <model name="box1">
      <pose> 2 1 0 0 0 0</pose>
      <link name="link">
        <collision name="collision">
          <geometry>
            <box>
              <size>0.4 0.4 0.4</size>
            </box>
          </geometry>
        </collision>
        <visual name="visual">
          <geometry>
            <box>
              <size>0.4 0.4 0.4</size>
            </box>
          </geometry>
        </visual>
      </link>
      <plugin name="push_animate_1" filename="libanimated_box_1.so"/>
    </model>   
```

