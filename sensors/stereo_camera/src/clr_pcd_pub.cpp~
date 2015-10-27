#include "ros/ros.h"
#include <sensor_msgs/PointCloud2.h>
#include <pcl_conversions/pcl_conversions.h>
#include <pcl/point_cloud.h>
#include <pcl/point_types.h>


void point_cloud_color_callback(const sensor_msgs::PointCloud2::ConstPtr& msg)  
{                                                                                
    pcl::PointCloud<pcl::PointXYZRGB> cloud;                                   
   
    pcl::fromROSMsg(*msg, cloud);
  
    ros::NodeHandle r;
   
    ros::Publisher  chatter_pub = r.advertise<pcl::PointXYZRGB>("/sensors/organized_color_point_cloud", 1);

    chatter_pub.publish(cloud);
}


int main(int argc, char **argv)
{
  ros::init(argc, argv, "clr_pcd_pub");
  
  ros::NodeHandle n;

  ros::Subscriber sub=n.subscribe("/multisense/organized_image_points2_color",1,point_cloud_color_callback);

  ros:: spin();
  
  return 0;
}
