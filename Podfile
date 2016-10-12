source 'https://github.com/CocoaPods/Specs.git'
platform :osx, '10.12'
inhibit_all_warnings!
use_frameworks!

target "Monolingual" do
#	pod 'Sparkle', '~> 1.14.0'
	pod 'Fabric', '~> 1.6.8'
	pod 'Crashlytics', '~> 3.8.1'
end

target "XPCService" do
	pod 'SMJobKit', '~> 0.0.15'
end

# see https://github.com/CocoaPods/CocoaPods/issues/4515
post_install do |installer|
	ignore_overriding_contains_swift(installer, 'XPCService')
end

def ignore_overriding_contains_swift(installer, target)
	target = installer.pods_project.targets.find{|t| t.name == "Pods-#{target}"}
	raise "failed to find #{target} among: #{installer.aggregate_targets}" unless target
	target.build_configurations.each do |config|
		config.build_settings['EMBEDDED_CONTENT_CONTAINS_SWIFT'] = "NO"
		config.build_settings['ALWAYS_EMBED_SWIFT_STANDARD_LIBRARIES'] = "NO"
	end
end
