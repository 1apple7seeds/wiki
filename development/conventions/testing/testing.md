# Testing

# Testing and Linting in ROS
## Running `roslint` with catkin
Before merging into the main repository `roslint` is ran on all merge requests. Unless all errors are resolved the merge request will be rejected. To test if your changes would pass the `roslint` test locally:
- Add the following lines to your `CMakelists.txt`:

```CMake
roslint_python()  # pep8 linting
roslint_cpp()     # ROS wrapper of Google's cpplint
```
- Build target `roslint`:
  - with `catkin_make`: `catkin_make roslint_<package_name>`
  - with `catkin_tools`: `catkin build --no-deps <package_name> --make-args roslint_<package_name>`
- If build fail copy and execute the gray line that looks something like the following to see more detailed errors:

```
cd <package_source_directory>; catkin build --get-env <package_name> | catkin env -si  /usr/bin/make roslint --jobserver-fds=6,7 -j; cd -
```
![2017-05-06-205659_900x152_scrot](2017-05-06-205659_900x152_scrot.png)

## Running Unit Tests
```bash
catkin run_tests --this --no-deps
```

# References
[ROS Wiki Article](http://wiki.ros.org/UnitTesting)

Referred links:

- [gtest for C++](https://github.com/google/googletest)
- [unittest for Python](https://docs.python.org/2/library/unittest.html)
- [rostest for ROS](http://wiki.ros.org/rostest)

Mockups:

- [C++](https://github.com/google/googletest/tree/master/googlemock)
- [Python](https://docs.python.org/3/library/unittest.mock.html)
- [ROS](http://wiki.ros.org/mock_objects)
