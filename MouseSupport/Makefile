# lipoplastic setup for armv6 + arm64 compilation
export TARGET := iphone:clang
export THEOS_PLATFORM_SDK_ROOT_armv6 = /Applications/Xcode-4.4.1.app/Contents/Developer
export SDKVERSION_armv6 = 5.1
export TARGET_IPHONEOS_DEPLOYMENT_VERSION = 3.0
export TARGET_IPHONEOS_DEPLOYMENT_VERSION_arm64 = 7.0
export ARCHS = armv6 arm64

THEOS_PACKAGE_DIR_NAME=debs

include $(THEOS)/makefiles/common.mk

TWEAK_NAME = MouseSupport
MouseSupport_FILES = Tweak.xm
MouseSupport_CFLAGS = -I. -I.. -I../3rdParty
MouseSupport_LDFLAGS = -L../.theos/_/usr/local/lib/ -lhidsupport
MouseSupport_FRAMEWORKS = UIKit QuartzCore CoreGraphics
MouseSupport_PRIVATE_FRAMEWORKS = GraphicsServices
MouseSupport_LIBRARIES = substrate

include $(THEOS_MAKE_PATH)/tweak.mk
