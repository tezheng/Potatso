source 'https://github.com/CocoaPods/Specs.git'

platform :ios, '9.0'
use_frameworks!

def fabric
    pod 'Fabric', '~> 1.6.10'
    pod 'Crashlytics', '~> 3.8.3'
end

def library
    pod 'KissXML', '~> 5.1.2'
    pod 'KissXML/libxml_module'
    pod 'ICSMainFramework', :path => "./Library/ICSMainFramework/"
    pod 'MMWormhole', '~> 2.0.0'
    pod 'KeychainAccess’, ‘~> 2.4.0'
end

def tunnel
    pod 'MMWormhole', '~> 2.0.0'
end

def socket
    pod 'CocoaAsyncSocket', '~> 7.4.3'
end

def model
    pod 'RealmSwift’, '~> 1.1.0'
end

target "Potatso" do
    pod 'Aspects', :path => "./Library/Aspects/"
    pod 'Cartography', '~> 0.7.0'
    pod 'AsyncSwift', '~> 1.7.4'
    pod 'SwiftColor', '~> 0.3.7'
    pod 'Appirater', '~> 2.0.5'
    pod 'Eureka', '~> 1.7.0’
    pod 'MBProgressHUD', '~> 1.0.0'
    pod 'CallbackURLKit', '~> 0.2.0'
    pod 'ICDMaterialActivityIndicatorView', '~> 0.1.0'
    pod 'Reveal-iOS-SDK', '~> 1.6.2', :configurations => ['Debug']
    pod 'ICSPullToRefresh', '~> 0.4'
    pod 'ISO8601DateFormatter', '~> 0.8'
    pod 'Alamofire', '~> 3.5.1'
    pod 'ObjectMapper', '~> 1.5.0'
    pod 'CocoaLumberjack', '~> 2.4.0'
    pod 'CocoaLumberjackSwiftHelper', '~> 0.1.1'
    pod 'Helpshift', '5.6.1'
    pod 'PSOperations', '~> 2.3'
    pod 'LogglyLogger-CocoaLumberjack', '~> 2.3.2'
    tunnel
    library
    fabric
    socket
    model
end

target "PacketTunnel" do
    tunnel
    socket
end

target "PacketProcessor" do
    socket
end

target "TodayWidget" do
    pod 'Cartography', '~> 0.7.0'
    pod 'SwiftColor', '~> 0.3.7'
    library
    socket
    model
end

target "PotatsoLibrary" do
    library
    model
end

target "PotatsoModel" do
    model
end

target "PotatsoLibraryTests" do
    library
end

post_install do |installer|
    installer.pods_project.targets.each do |target|
        target.build_configurations.each do |config|
	        config.build_settings['SWIFT_VERSION'] = "2.3"
            config.build_settings['ENABLE_BITCODE'] = 'NO'
            if target.name == "HelpShift"
                config.build_settings["OTHER_LDFLAGS"] = '$(inherited) "-ObjC"'
            end
        end
    end
end

