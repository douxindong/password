# password
加密解密:md5加密; base64加密, base64解密; aes 加密, aes 解密;
#使用注意事项:
  使用注意事项:
  1. 在build phases中的GTMBase64.m需要设置 -fno-objc-arc
  2. 在#import "NSString+Base64.m”文件中导入   #import <Foundation/Foundation.h>
  3.在#import "GTMBase64.m”文件中添加          #import <CommonCrypto/CommonCrypto.h>

###代码
- (void)viewDidLoad {
    [super viewDidLoad];

    //要加密的字符串
    NSString *strForEn = @"需要加密字符串";
    
    //md5加密
    NSString *strEnRes = [CusMD5 md5String:strForEn];
    NSLog(@"md5 加密: %@",strEnRes);
    //md5不可逆 不能解密
    //base64加密
    NSData *dataEn = [strForEn dataUsingEncoding:NSUTF8StringEncoding];
    NSData *dataEnRes = [GTMBase64 encodeData:dataEn];
    //把加密结果转成string
    NSString *base64EnRes = [[NSString alloc] initWithData:dataEnRes encoding:NSUTF8StringEncoding];
    NSLog(@"base64加密: %@",base64EnRes);
    
    //base64解密
    NSData *resDeBase64 = [GTMBase64 decodeData:dataEnRes];
    NSString *strDeBase64 = [[NSString alloc] initWithData:resDeBase64 encoding:NSUTF8StringEncoding];
    NSLog(@"base64解密: %@",strDeBase64);


    //aes 加密
    NSString *strAESEnRes = [AESCrypt encrypt:strForEn password:@"secret"];
    NSLog(@"aes 加密: %@",strAESEnRes);
    
    //aes 解密
    NSString *strAESDeRes = [AESCrypt decrypt:strAESEnRes password:@"secret"];
    NSLog(@"aes 解密: %@",strAESDeRes);
}
###

 
