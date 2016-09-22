# password
加密解密:md5加密; base64加密, base64解密; aes 加密, aes 解密;
#使用注意事项:
  使用注意事项:
  1. 在build phases中的GTMBase64.m需要设置 -fno-objc-arc
  2. 在#import "NSString+Base64.m”文件中导入   #import <Foundation/Foundation.h>
  3.在#import "GTMBase64.m”文件中添加          #import <CommonCrypto/CommonCrypto.h>
 
