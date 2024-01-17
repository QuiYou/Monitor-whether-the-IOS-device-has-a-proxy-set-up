CFNetwork.framework

NSDictionary *proxySettings = (__bridge NSDictionary *)(CFNetworkCopySystemProxySettings());
NSArray *proxies = (__bridge NSArray *)(CFNetworkCopyProxiesForURL((__bridge CFURLRef _Nonnull)([NSURL URLWithString:@"http://www.baidu.com"]), (__bridge CFDictionaryRef _Nonnull)(proxySettings)));
NSLog(@"\n%@",proxies);

NSDictionary *settings = proxies[0];
NSLog(@"%@",[settings objectForKey:(NSString *)kCFProxyHostNameKey]);
NSLog(@"%@",[settings objectForKey:(NSString *)kCFProxyPortNumberKey]);
NSLog(@"%@",[settings objectForKey:(NSString *)kCFProxyTypeKey]);

if ([[settings objectForKey:(NSString *)kCFProxyTypeKey] isEqualToString:@"kCFProxyTypeNone"])
{
     NSLog(@"没代理");
}
else
{
     NSLog(@"设置了代理");
}
