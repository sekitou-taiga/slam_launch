# インストール
以下の手順でKarto_SLAMをインストールする  
~~~ 
$ cd ~/catkin_ws/src
$ git clone https://github.com/ros-perception/slam_karto
$ git clone https://github.com/ros-perception/open_karto
$ cd ..
$ catkin build
~~~

## [LaserRangeScan contains 540 range readings, expected 541]が表示される場合

open_karto/include/karto.hを編集する.
~~~
void Update()
{
  m_NumberOfRangeReadings = static_cast<kt_int32u>(math::Round((GetMaximumAngle() -
                                                                GetMinimumAngle())
                                                                / GetAngularResolution()) + 1);
}
~~~
を以下のように変える.
~~~
void Update()
{
  m_NumberOfRangeReadings = static_cast<kt_int32u>(math::Round((GetMaximumAngle() -
                                                                GetMinimumAngle())
                                                                / GetAngularResolution()));
}
~~~