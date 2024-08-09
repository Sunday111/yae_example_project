# YAE Example

This is an example on how to set up a project that uses YAE as CMake files generator and dependency manager.

## Project structure

### `yae_project.json`

This file describes your project. `make_project_files.py` generator script will look for `*.module.json` in the directory specified by `modules_dir` property and genrate all necessary `CMakeLists.txt` files to build the project. It will also clone github dependencies, specified by your modules into the directory specified by `cloned_dependencies_dir` property.

## Build

I use clang-19 but it might also work on earlier versions.

```bash
git clone https://github.com/Sunday111/yae_example_project
python3 ./deps/yae/scripts/make_project_files.py --project_dir=./yae_example_project/
cmake -S ./yae_example_project -B ./yae_example_project/build
cmake --build ./yae_example_project/build
```
