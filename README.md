# AutoreleasePool

我的博文[《Objective-C Autorelease Pool 的实现原理》](http://blog.leichunfeng.com/blog/2015/05/31/objective-c-autorelease-pool-implementation-principle/)的完整配套代码。

``` objc
__weak NSString *string_weak_ = nil;

- (void)viewDidLoad {
    [super viewDidLoad];
    
    // 场景 1
    NSString *string = [NSString stringWithFormat:@"leichunfeng"];
    string_weak_ = string;
    
    // 场景 2
//    @autoreleasepool {
//        NSString *string = [NSString stringWithFormat:@"leichunfeng"];
//        string_weak_ = string;
//    }
    
    // 场景 3
//    NSString *string = nil;
//    @autoreleasepool {
//        string = [NSString stringWithFormat:@"leichunfeng"];
//        string_weak_ = string;
//    }
    
    NSLog(@"string: %@", string_weak_);
}

- (void)viewWillAppear:(BOOL)animated {
    [super viewWillAppear:animated];
    NSLog(@"string: %@", string_weak_);
}

- (void)viewDidAppear:(BOOL)animated {
    [super viewDidAppear:animated];
    NSLog(@"string: %@", string_weak_);
}
```
