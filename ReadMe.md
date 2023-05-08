
# 说明

## 1.s3event-trigger-tencentapigw
    s3存储桶有文件上传，触发调用腾讯api网关接口，接口附带存储桶文件cdn地址和文件路径；接口调用失败，将cdn地址和文件路径写入dynamoDB，发discord消息

## 2.syncfilefroms3tocos
    腾讯api网关被调用，取出s3存储桶文件的cdn地址和文件路径，下载文件
    
## 3.retrysyncfile
    aws eventbridge 定时查看数据库中失败同步到腾讯云的记录，重试调用腾讯云api网关接口；重试成功或者430错误删除记录

## 4.resource-creator
    创建dynamoDB的yml配置，数据库表用于记录失败存储桶文件的url

# 上线配置说明
## 1.s3event-trigger-tencentapigw
robot_url：discord机器人频道
robot_thread：discord机器人子区
table：失败记录的dynamoDB数据库表名
dynamodb_region：aws服务所在区域

apigwUrl:腾讯云api网关地址
cdnUrl：s3存储桶cdn

## 2.syncfilefroms3tocos
uploadfile中cosurl设置腾讯云存储桶url

## 3.retrysyncfile
robot_url：discord机器人频道
robot_thread：discord机器人子区
table：失败记录的dynamoDB数据库表名
dynamodb_region：aws服务所在区域

profile:认证文件配置节段


