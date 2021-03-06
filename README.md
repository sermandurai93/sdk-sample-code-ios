## Synopsis

Publicly available sample apps of InMobi providing simple integration steps. InMobi will add the latest SDK along with the change logs for the release.

## Installation steps for iOS Apps 

The following environment is required to run the Sample apps

    Xcode 9.0
    InMobi SDK 7.x
    iOS 8.0 and above
    
For AdsDemo project make sure you have the latest version of pod installed after that you need to simply do
    cd /{pathToSampleAppsDirectory}/InMobiAdsDemo
    pod init
    pod install
   
Three sample apps are provided as per Ad Formats

    BannerSample
    InterstitialSample
    NativeSample

The latest InMobi iOS SDK is available in the InMobi folder along with its change logs.

To run the sample apps, open any of the Ad Format's .xcodeproj file with Xcode 9.0. For example, to run a Banner's sample, open the BannerSample.xcodeproj in the BannerSample folder and run via Xcode.

## License

These sample apps are provided under MIT license. For more information, please see the LICENSE file. For information about InMobi SDK's license, please see the InMobi folder.

## Change logs

Build 7.1.1 [20/Apr/2018]
-------------
- Fixed a remote crash which can happen due to config update.

###Build 7.1.0 [06/Apr/2018]
-------------

- Added support for GDPR compliance
- Added skip callback to Native Ads
- Removed support for iOS 7 devices. SDK will not initialise if the device is below iOS 8 [iOS 8 is deprecated as of v7.0.0]
- Fixed a crash in carousel ads
- Performance improvement by offloading certain tasks to the background threads
- Bug Fixes

- APIs Added
	* IMSDK class
	 + +(void)initWithAccountID:(NSString *)accountID consentDictionary: (NSDictionary*) consentDictionary;
	 + +(void) updateGDPRConsent:(NSDictionary *)consentDictionary;

	* IMCommonConstants class
	 + #define IM_GDPR_CONSENT_AVAILABLE @"gdpr_consent_available"

	* IMNativeDelegate class
	 + -(void)userDidSkipPlayingMediaFromNative:(IMNative*)native;

- APIs Removed
	* IMSDK class
	 - +(void)setNationality:(NSString*)nationality
	 - +(void)setEthnicity:(IMSDKEthnicity)ethnicity;
	 - +(void)setHouseholdIncome:(IMSDKHouseholdIncome)income;
	 - +(void)setIncome:(unsigned int)income;

	* IMCommonConstants class
	 - -typedef NS_ENUM (NSInteger, IMSDKEthnicity) {
 		kIMSDKEthnicityHispanic = 1,
     		kIMSDKEthnicityCaucasian,
     		kIMSDKEthnicityAsian,
     		kIMSDKEthnicityAfricanAmerican,
     		kIMSDKEthnicityOther
 		};
 
 	- -typedef NS_ENUM(NSInteger, IMSDKHouseholdIncome) {
     		kIMSDKHouseholdIncomeBelow5kUSD = 1,
     		kIMSDKHouseholdIncomeBetween5kAnd10kUSD,
     		kIMSDKHouseholdIncomeBetween10kAnd15kUSD,
     		kIMSDKHouseholdIncomeBetween15kAnd20kUSD,
     		kIMSDKHouseholdIncomeBetween20kAnd25kUSD,
     		kIMSDKHouseholdIncomeBetween25kAnd50kUSD,
     		kIMSDKHouseholdIncomeBetween50kAnd75kUSD,
     		kIMSDKHouseholdIncomeBetween75kAnd100kUSD,
     		kIMSDKHouseholdIncomeBetween100kAnd150kUSD,
     		kIMSDKHouseholdIncomeAbove150kUSD
 		};

###Build 7.0.5 [27/Dec/2017]
-------------
- Bug Fixes

###Build 7.0.4 [1/Dec/2017]
-------------
- Support for iPhone X
- Bug Fixes

###Build 7.0.3 [11/Nov/2017]
-------------
- Bug Fixes

###Build 7.0.2 [10/Nov/2017]
-------------
- Bug Fixes & Performance Improvements

###Build 7.0.1 [27/Sept/2017]
-------------
- Bug Fixes

###Build 7.0.0 [15/Sept/2017]
-------------
- Bug Fixes
- Better Metrics collection
- Changes to support iOS 11
- Remove support for iOS 7
- Deprecating support for iOS 8
- Brand new Native Ad solution:
      * Native ads can now support videos, carousel and static Ad types
      * Prefetching Native Ads for better load times
      * Better way to customize the Ad to match the App’s native environment
- Interactive Video Ad Experience:
      * Brand new video Ad experience to increase user engagement in Interstitial Ad Format
- Rich End Cards:
      * Engaging end-cards are now supported via Rich-Media End-cards
- Support for GIF images
- Performance improvements


- APIs Added
    * IMNative class
     + -(UIView*)primaryViewOfWidth:(CGFloat)width;
     + @property (nonatomic, strong, readonly) NSString* customAdContent;
     + @property (nonatomic, strong, readonly) NSString* adTitle;
     + @property (nonatomic, strong, readonly) NSString* adDescription;
     + @property (nonatomic, strong, readonly) UIImage* adIcon;
     + @property (nonatomic, strong, readonly) NSString* adCtaText;
     + @property (nonatomic, strong, readonly) NSString* adRating;
     + @property (nonatomic, strong, readonly) NSURL* adLandingPageUrl;
     + @property (nonatomic, readonly) BOOL isAppDownload;
     + -(BOOL)isReady;
     + -(void)reportAdClickAndOpenLandingPage;


  * IMNativeDelegate
    + -(void)native:(IMNative*)native rewardActionCompletedWithRewards:(NSDictionary*)rewards;
    + -(void)native:(IMNative*)native didInteractWithParams:(NSDictionary*)params;
    + -(void)nativeDidFinishPlayingMedia:(IMNative*)native;

- APIs Removed
  * IMNativeStrands class
   + @interface IMNativeStrands : NSObject
   + @property (nonatomic, weak) id<IMNativeStrandsDelegate>delegate;
   + @property (nonatomic, strong) NSString* keywords;
   + @property (nonatomic, strong) NSDictionary* extras;
   + -(instancetype)initWithPlacementId:(long long)placementId position:(NSInteger)position;
   + -(instancetype)initWithPlacementId:(long long)placementId;
   + -(void)load;
   + -(UIView*)strandsView;
   + - (void)recycleView;
   + - (CGSize)strandsViewSize;

 * IMNativeStrandsDelegate protocol
    + @interface IMNativeStrands : NSObject
    + -(void)nativeStrandsDidFinishLoading:(IMNativeStrands*)nativeStrands;
    + -(void)nativeStrands:(IMNativeStrands*)nativeStrands didFailToLoadWithError:(IMRequestStatus*)error;
    + -(void)nativeStrandsWillPresentScreen:(IMNativeStrands*)nativeStrands;
    + -(void)nativeStrandsDidPresentScreen:(IMNativeStrands*)nativeStrands;
    + -(void)nativeStrandsWillDismissScreen:(IMNativeStrands*)nativeStrands;
    + -(void)nativeStrandsDidDismissScreen:(IMNativeStrands*)nativeStrands;
    + -(void)userWillLeaveApplicationFromNativeStrands:(IMNativeStrands*)nativeStrands;
    + -(void)nativeStrandsAdImpressed:(IMNativeStrands*)nativeStrands;
    + -(void)nativeStrandsAdClicked:(IMNativeStrands*)nativeStrands;

 * IMNative class
    + @property (nonatomic, strong, readonly) NSString* adContent;
    + +(void)bindNative:(IMNative*)native toView:(UIView*)view;
    + +(void)unBindView:(UIView*)view;
    + -(void)reportAdClick:(NSDictionary*)params;
    + -(void)reportAdClickAndOpenLandingURL:(NSDictionary*)params;

###Build 6.1.2 [03/Mar/2017]
-------------
- Bug Fixes

###Build 6.1.1 [14/Feb/2017]
-------------
- Bug Fixes

###Build 6.1.0 [06/Feb/2017]
-------------
- Added support for in-feed video ads
- Fixed a typo in IMSDKHouseholdIncome enum
- Now Interstitial ad formats can have transparent background
- Bug Fixes

###Build 6.0.1 [23/Nov/2016]
-------------
- Added Auto close support for Native Fullscreen ads
- Minor enhancements for customization in Video ads
- Crash in scrollable asset fixed
- Bug Fixes
- Removed dependencies on EventKit and EventKitUI frameworks

###Build 6.0.0 [19/Sep/2016]
-------------
- Fully compliant with iOS 10
- Deprecating support for iOS 7
- Integrates as a drag-drop replacement framework
- Added support for WKWebview
- Brand new video solution:
	* Drag-drop library upgrade for existing SDK 5xx.
	* High render rates
	* Stall free video experience
	* No Java Script
	* Enormous data savings for users
	* Better security and monetization
- Added support for easier integration.
- Added support for better debugging.
- Support for IPV6.
- Bug fixes
	* Fixed an issue where the Interstitial Ad disappears
	* Fixed an issue where the endcard doesn't show in some cases for fullscreen Native Video.
- A new delegate method introduced in IMInterstitialDelegate to indicate fetch completion of the ad.
- A new delegate method have been introduced in IMNative to indicate impression tracking of the ad view.
- Two new delegate methods have been introduced in IMNativeStrandsDelegate to indicate impression tracking of the ad view and click of the ad view.
- Removed support for IMStrandTableViewAdapter
