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
