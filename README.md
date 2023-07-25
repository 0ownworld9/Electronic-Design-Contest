# Electronic-Design-Contest
The code repository prepared for the 2023 competition, including common features of K210 and Openmv, and the preferred conditions for both.
#对于二维码识别功能，Openmv返回的是一个数组，无法进行内容的直接读取
#对于openmv来说，是可以多次修改灰度图或者RGB模式的
#默认情况下，openmv有三个文件夹，上电后会自动执行main.py文件
#寻找最大色块的代码
def find_max(blobs):
    max_size=0
    for blob in blobs:
        if blob[2]*blob[3] > max_size:
            max_blob=blob
            max_size = blob[2]*blob[3]
    return max_blob
#左右电机方向应该是相反的，一正一负。但距离PID应该是相同的
#EDGI训练模型能返回识别物体特征点的数量和个数，但无法返回大小，如何是识别相同大小的物体的话，EDGI识别效果更好，但如果是一大一小，还是YOLOV5比较好
#标志识别参考官方网页
########使用openmv自带摄像头采集训练集图片时要选中class.c才能够采集图片
#sensor模块基础配置
sensor.reset()
sensor.set_pixformat(sensor.RGB565) # or GRAYSCALE...灰度或者彩色图片
sensor.set_framesize(sensor.QVGA) # or QQVGA...实际分辨率
sensor.skip_frames(time = 2000) #跳帧保证图片处理起来比较流畅
clock = time.clock()
