# hsl_vendor
ros2 hslを使うためのvendor pkg
## install
ThirdParty-HSLの元のリポジトリ
https://github.com/coin-or-tools/ThirdParty-HSL
- cmakeの以下の部分を自分のものに変更
```CMake
ExternalProject_Add(ThirdParty-HSL
  GIT_REPOSITORY  [ThirdParty-HSLに取得したhslライブラリを追加したリポジトリURL]
  GIT_TAG         [上のリポジトリのtag]
  BUILD_IN_SOURCE   YES
  CONFIGURE_COMMAND ./configure --prefix=${CMAKE_CURRENT_BINARY_DIR}/ThirdParty-HSL_install
  BUILD_COMMAND     make
  INSTALL_COMMAND   make install

)
```
- colcon build
- 以下を.bashrcに追加
```bash
export LD_LIBRARY_PATH=$ROS_WORKSPACE/install/hsl_vendor/lib:$LD_LIBRARY_PATH
```
