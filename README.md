WA_MENU-1
=========

WA graduation project 2014 

WA_MENUAppDelegate.h
//  MyMenuWA
//
//  Created by jason.lu on 5/17/14.
//  Copyright (c) 2014 ___JASONLU2014___. All rights reserved.
//

#import <UIKit/UIKit.h>

@interface WA_MENUAppDelegate : UIResponder <UIApplicationDelegate>

@property (strong, nonatomic) UIWindow *window;

@end


//  WA_MENUAppDelegate.m
//  MyMenuWA
//
//  Created by jason.lu on 5/17/14.
//  Copyright (c) 2014 ___JASONLU2014___. All rights reserved.
//

#import "WA_MENUAppDelegate.h"

@implementation WA_MENUAppDelegate

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
    self.window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]];
    // Override point for customization after application launch.
    self.window.backgroundColor = [UIColor whiteColor];
    [self.window makeKeyAndVisible];
    return YES;
}

- (void)applicationWillResignActive:(UIApplication *)application
{
    // Sent when the application is about to move from active to inactive state. This can occur for certain types of temporary interruptions (such as an incoming phone call or SMS message) or when the user quits the application and it begins the transition to the background state.
    // Use this method to pause ongoing tasks, disable timers, and throttle down OpenGL ES frame rates. Games should use this method to pause the game.
}

- (void)applicationDidEnterBackground:(UIApplication *)application
{
    // Use this method to release shared resources, save user data, invalidate timers, and store enough application state information to restore your application to its current state in case it is terminated later. 
    // If your application supports background execution, this method is called instead of applicationWillTerminate: when the user quits.
}

- (void)applicationWillEnterForeground:(UIApplication *)application
{
    // Called as part of the transition from the background to the inactive state; here you can undo many of the changes made on entering the background.
}

- (void)applicationDidBecomeActive:(UIApplication *)application
{
    // Restart any tasks that were paused (or not yet started) while the application was inactive. If the application was previously in the background, optionally refresh the user interface.
}

- (void)applicationWillTerminate:(UIApplication *)application
{
    // Called when the application is about to terminate. Save data if appropriate. See also applicationDidEnterBackground:.
}

@end

WA_MENUViewController.m
//  MyMenu_WA
//
//  Created by jason.lu on 4/22/14.
//  Copyright (c) 2014 ___JASONLU2014___. All rights reserved.
//

#import "WA_MENUViewController.m"
#import "WA_MENUViewController.h"
#import "WA_MENUToDoItem.h"

@interface WA_MENUViewController ()

@property NSMutableArray *toDoItems;

@end

@implementation WA_MENUViewController

- (void) loadInitialData {
    XYZToDoItem *item1 = [[XYZToDoItem alloc] init];
    item1.itemName = @"Chicken Noodle Soup";
    [self.toDoItems addObject:item1];
    XYZToDoItem *item2 = [[XYZToDoItem alloc] init];
    item2.itemName = @"Chicken Lo Mein";
    [self.toDoItems addObject:item2];
    XYZToDoItem *item3 = [[XYZToDoItem alloc] init];
    item3.itemName = @"Jasmine Steamed Rice ";
    [self.toDoItems addObject:item3];
    XYZToDoItem *item4 = [[XYZToDoItem alloc] init];
    item4.itemName= @"Steamed Peas";
}

- (void)viewDidLoad
{
    [super viewDidLoad];
	self.toDoItems = [ [NSMutableArray alloc] init];
    [self loadInitialData];
}

- (void)didReceiveMemoryWarning
{
    [super didReceiveMemoryWarning];
    // Dispose of any resources that can be recreated.
}

@end

- (NSInteger) numberOfSectionsInTableView: (UTableView *) tableView
{
    //Return the number of sections.
    return 1;
    }

- (NSInteger) tableView: (UTableView *) tableView numberOfRowsInSection:(NSInteger)section
{
    // Return the number of rows in the section.
    return [self.toDoItems count];
}

- (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath
{
    static NSString *CellIdentifier = @"Monday";
    UITableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:CellIdentifier forIndexPath:indexPath];
    XYZToDoItem *toDoItem = [self.toDoItems objectAtIndex:indexPath.row];
    cell.textLabel.text = toDoItem.itemName;
    return cell;
}



