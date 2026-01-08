# Install location of module
MODDESTDIR := /lib/modules/$(KVER)/kernel/drivers/net/wireless/

# Filename of finished module
MODULE_NAME := 8723du

# Default architecture and cross-compile prefix (empty means native build)
ARCH :=
CROSS_COMPILE :=

##################### Optimization Flags ##########################
ccflags-y += $(USER_EXTRA_CFLAGS)
ccflags-y += -O2 -fno-pic -fno-pie -fno-jump-tables
#ccflags-y += -Wall -Wextra -Werror -pedantic
#ccflags-y += -Wshadow -Wpointer-arith -Wcast-qual -Wstrict-prototypes -Wmissing-prototypes
ldflags-y += --strip-all -O3

##################### Compile-time Warnings #######################
ccflags-y += -Wno-missing-include-dirs -Wno-missing-prototypes -Wno-missing-declarations
ccflags-y += -Wno-unused-variable -Wno-unused-value -Wno-unused-label -Wno-unused-parameter
ccflags-y += -Wno-unused -Wno-unused-function -Wno-unused-const-variable
ccflags-y += -Wno-implicit-function-declaration -Wno-implicit-fallthrough
ccflags-y += -Wno-missing-format-attribute -Wno-format-truncation
ccflags-y += -Wno-incompatible-pointer-types
ccflags-y += -Wno-misleading-indentation
ccflags-y += -Wno-old-style-declaration
ccflags-y += -Wno-discarded-qualifiers
ccflags-y += -Wno-implicit-fallthrough
ccflags-y += -Wno-cast-function-type
ccflags-y += -Wno-ignored-attributes
ccflags-y += -Wno-stringop-overread
ccflags-y += -Wno-sizeof-array-div
ccflags-y += -Wno-enum-conversion
ccflags-y += -Wno-uninitialized
ccflags-y += -Wno-empty-body
ccflags-y += -Wno-attributes
ccflags-y += -Wno-date-time
ccflags-y += -Wno-address
ccflags-y += -Wno-undef
ccflags-y += -Wno-vla

############## CLANG/LLVM  #################
ifeq ($(CC), clang)
ccflags-y += -Wno-uninitialized -Wno-enum-conversion -Wno-fortify-source
ccflags-y += -Wno-invalid-source-encoding -Wno-tautological-pointer-compare
ccflags-y += -Wno-tautological-overlap-compare -Wno-pointer-bool-conversion
ccflags-y += -Wno-misleading-indentation -Wno-self-assign -Wno-header-guard
endif

################# GCC ######################
ifeq ($(CC), gcc)
ccflags-y += -Wno-date-time     # Fix compile error && warning on gcc 4.9 and later
ccflags-y += -Wno-address -Wframe-larger-than=1648 -Wno-cast-function-type
ccflags-y += -Wno-enum-int-mismatch -Wno-stringop-overread -Wno-enum-conversion
ccflags-y += -Wno-int-in-bool-context -Wno-missing-prototypes -Wno-missing-declarations
endif

############# SOURCE & HEADERS #############
export TopDIR ?= $(shell pwd)

src := $(PWD)/drivers/staging/rtl8723du/

ccflags-y += -I$(src)/hal/phydm -I$(src)/hal -I$(src)/platform  -I$(src)/include -I$(src)/hal/btc

########################## AUTOCFG ############################
CONFIG_AUTOCFG_CP = n
########################## Features ###########################
CONFIG_AP_MODE = y
CONFIG_P2P = y
CONFIG_MP_INCLUDED = y
CONFIG_CONCURRENT_MODE = n
CONFIG_POWER_SAVING = y
CONFIG_IPS_MODE = default
CONFIG_LPS_MODE = default
CONFIG_USB_AUTOSUSPEND = n
CONFIG_HW_PWRP_DETECTION = n
CONFIG_BT_COEXIST = y
CONFIG_WAPI_SUPPORT = n
CONFIG_EFUSE_CONFIG_FILE = y
CONFIG_EXT_CLK = n
CONFIG_TRAFFIC_PROTECT = n
CONFIG_LOAD_PHY_PARA_FROM_FILE = y
CONFIG_TXPWR_BY_RATE = y
CONFIG_TXPWR_BY_RATE_EN = y
CONFIG_TXPWR_LIMIT = y
CONFIG_TXPWR_LIMIT_EN = n
#CONFIG_RTW_CHPLAN = 0xFF
CONFIG_RTW_CHPLAN = 0x7F
CONFIG_RTW_ADAPTIVITY_EN = disable
CONFIG_RTW_ADAPTIVITY_MODE = normal
CONFIG_SIGNAL_SCALE_MAPPING = n
CONFIG_80211W = y
CONFIG_REDUCE_TX_CPU_LOADING = n
CONFIG_BR_EXT = y
CONFIG_TDLS = n
CONFIG_WIFI_MONITOR = n
CONFIG_MCC_MODE = n
CONFIG_APPEND_VENDOR_IE_ENABLE = n
CONFIG_RTW_NAPI = y
CONFIG_RTW_GRO = y
CONFIG_RTW_NETIF_SG = y
CONFIG_RTW_IPCAM_APPLICATION = n
CONFIG_RTW_REPEATER_SON = n
CONFIG_ICMP_VOQ = n
CONFIG_IP_R_MONITOR = n  #arp VOQ and high rate
# user priority mapping rule : tos, dscp
CONFIG_RTW_UP_MAPPING_RULE = tos
CONFIG_RTW_MBO = n
CONFIG_SEC_AMSDU_MODE = non-spp   # AMSDU in security network
########################## Debug ##############################
CONFIG_RTW_DEBUG = n
CONFIG_RTW_LOG_LEVEL = 3 # default log level is _DRV_INFO_ = 2
CONFIG_PROC_DEBUG = n # enable /proc/net/rtlxxxx/ interfaces
######################## Wake On Lan ###########################
CONFIG_WOWLAN = n
#bit3: ARP enable, bit2: deauth, bit1: unicast, bit0: magic pkt.
CONFIG_WAKEUP_TYPE = 0xf
#CONFIG_WAKEUP_TYPE = 0x7
CONFIG_WOW_LPS_MODE = default
#bit0: disBBRF off, #bit1: Wireless remote controller (WRC)
CONFIG_SUSPEND_TYPE = 0
CONFIG_WOW_STA_MIX = n
CONFIG_GPIO_WAKEUP = n
CONFIG_WAKEUP_GPIO_IDX = default
CONFIG_HIGH_ACTIVE_DEV2HST = n
CONFIG_ONE_PIN_GPIO = n
CONFIG_HIGH_ACTIVE_HST2DEV = n
CONFIG_PNO_SUPPORT = n
CONFIG_PNO_SET_DEBUG = n
CONFIG_AP_WOWLAN = n
######### Notify SDIO Host Keep Power During Syspend ############
CONFIG_RTW_SDIO_PM_KEEP_POWER = y
###################### MP HW TX MODE FOR VHT ####################
CONFIG_MP_VHT_HW_TX_MODE = n
###################### ROAMING ##################################
CONFIG_LAYER2_ROAMING = y
#bit0: ROAM_ON_EXPIRED, #bit1: ROAM_ON_RESUME, #bit2: ROAM_ACTIVE
CONFIG_ROAMING_FLAG = 0x3
####################### HACKS? ##################################
CONFIG_REGD_SRC_FROM_OS = y       # Sets (REGD) sourse to OS
CONFIG_FORCE_SW_CHANNEL_PLAN = y  # needed to scan all channels
###################### COMMON  ##################################

CROSS_COMPILE ?=
SUBARCH := $(shell uname -m | sed -e "s/i.86/i386/; s/ppc/powerpc/; s/armv.l/arm/; s/aarch64/arm64/; s/riscv.*/riscv/; s/mipseb/mips/; s/loong.*64/loongarch/;")
ifndef ARCH
    ARCH := $(SUBARCH)
endif

ccflags-y += -DCONFIG_LITTLE_ENDIAN -DCONFIG_IOCTL_CFG80211 -DRTW_USE_CFG80211_STA_EVENT -DCONFIG_RTL8723D

KVER ?= $(shell if [ -n "${NEW_VERSION}" ] && [ -n "${FLAVOR}" ]; then echo "${NEW_VERSION}-${FLAVOR}"; else uname -r; fi)
KSRC := /lib/modules/$(KVER)/build

CONFIG_RTL8723D = y
export CONFIG_RTL8723DU = m

########### HAL_RTL8723D #################################

_OS_INTFS_FILES := os_dep/osdep_service.o \
                        os_dep/linux/os_intfs.o \
                        os_dep/linux/usb_intf.o \
                        os_dep/linux/usb_ops_linux.o \
                        os_dep/linux/ioctl_linux.o \
                        os_dep/linux/xmit_linux.o \
                        os_dep/linux/mlme_linux.o \
                        os_dep/linux/recv_linux.o \
                        os_dep/linux/ioctl_cfg80211.o \
                        os_dep/linux/rtw_cfgvendor.o \
                        os_dep/linux/wifi_regd.o \
                        os_dep/linux/rtw_android.o \
                        os_dep/linux/rtw_proc.o \
                        os_dep/linux/nlrtw.o \
                        os_dep/linux/rtw_rhashtable.o \
                  	hal/hal_intf.o \
                  	hal/hal_com.o \
                  	hal/hal_com_phycfg.o \
                  	hal/hal_phy.o \
                  	hal/hal_dm.o \
                  	hal/hal_dm_acs.o \
                  	hal/hal_btcoex_wifionly.o \
                  	hal/hal_btcoex.o \
                        hal/hal_mp.o \
                  	hal/hal_mcc.o \
                       	hal/hal_hci/hal_usb.o \
                        hal/led/hal_led.o \
                        hal/led/hal_usb_led.o

_PLATFORM_FILES := platform/platform_ops.o

ifeq ($(CONFIG_MP_INCLUDED), y)
_OS_INTFS_FILES += os_dep/linux/ioctl_mp.o
endif

_HAL_INTFS_FILES += hal/HalPwrSeqCmd.o \
                        hal/rtl8723d/Hal8723DPwrSeq.o \
                        hal/rtl8723d/rtl8723d_sreset.o \
                        hal/rtl8723d/rtl8723d_hal_init.o \
                        hal/rtl8723d/rtl8723d_phycfg.o \
                        hal/rtl8723d/rtl8723d_rf6052.o \
                        hal/rtl8723d/rtl8723d_dm.o \
                        hal/rtl8723d/rtl8723d_rxdesc.o \
                        hal/rtl8723d/rtl8723d_cmd.o \
                        hal/rtl8723d/hal8723d_fw.o \
                        hal/rtl8723d/rtl8723d_lps_poff.o \
                        hal/rtl8723d/usb/usb_halinit.o \
                        hal/rtl8723d/usb/rtl8723du_led.o \
                        hal/rtl8723d/usb/rtl8723du_xmit.o \
                        hal/rtl8723d/usb/rtl8723du_recv.o \
                        hal/efuse/rtl8723d/HalEfuseMask8723D_USB.o \
                        hal/rtl8723d/usb/usb_ops.o

ifeq ($(CONFIG_BT_COEXIST), y)
_BTC_FILES += hal/btc/halbtc8723d1ant.o \
                  hal/btc/halbtc8723d2ant.o
endif

########### AUTO_CFG  #################################

ifeq ($(CONFIG_AUTOCFG_CP), y)
$(shell cp $(TopDIR)/autoconf_rtl8723d_usb_linux.h $(TopDIR)/include/autoconf.h)
endif

########### END OF PATH  #################################

ifeq ($(CONFIG_AP_MODE), y)
ccflags-y += -DCONFIG_AP_MODE
endif

ifeq ($(CONFIG_P2P), y)
ccflags-y += -DCONFIG_P2P
ifneq ($(CONFIG_AP_MODE), y)
$(error "CONFIG_AP_MODE is required for CONFIG_P2P")
endif
endif

ifeq ($(CONFIG_USB_AUTOSUSPEND), y)
ccflags-y += -DCONFIG_USB_AUTOSUSPEND
endif

ifeq ($(CONFIG_MP_INCLUDED), y)
#MODULE_NAME := $(MODULE_NAME)_mp
ccflags-y += -DCONFIG_MP_INCLUDED
endif

ifeq ($(CONFIG_CONCURRENT_MODE), y)
ccflags-y += -DCONFIG_CONCURRENT_MODE
endif

ifeq ($(CONFIG_POWER_SAVING), y)
ifneq ($(CONFIG_IPS_MODE), default)
ccflags-y += -DRTW_IPS_MODE=$(CONFIG_IPS_MODE)
endif
ifneq ($(CONFIG_LPS_MODE), default)
ccflags-y += -DRTW_LPS_MODE=$(CONFIG_LPS_MODE)
endif
ifneq ($(CONFIG_WOW_LPS_MODE), default)
ccflags-y += -DRTW_WOW_LPS_MODE=$(CONFIG_WOW_LPS_MODE)
endif
ccflags-y += -DCONFIG_POWER_SAVING
endif

ifeq ($(CONFIG_HW_PWRP_DETECTION), y)
ccflags-y += -DCONFIG_HW_PWRP_DETECTION
endif

ifeq ($(CONFIG_BT_COEXIST), y)
ccflags-y += -DCONFIG_BT_COEXIST
endif

ifeq ($(CONFIG_WAPI_SUPPORT), y)
ccflags-y += -DCONFIG_WAPI_SUPPORT
endif

ifeq ($(CONFIG_EFUSE_CONFIG_FILE), y)
ccflags-y += -DCONFIG_EFUSE_CONFIG_FILE

#EFUSE_MAP_PATH
USER_EFUSE_MAP_PATH ?=
ifneq ($(USER_EFUSE_MAP_PATH),)
ccflags-y += -DEFUSE_MAP_PATH=\"$(USER_EFUSE_MAP_PATH)\"
else
ccflags-y += -DEFUSE_MAP_PATH=\"/system/etc/wifi/wifi_efuse_$(MODULE_NAME).map\"
endif

#WIFIMAC_PATH
USER_WIFIMAC_PATH ?=
ifneq ($(USER_WIFIMAC_PATH),)
ccflags-y += -DWIFIMAC_PATH=\"$(USER_WIFIMAC_PATH)\"
else
ccflags-y += -DWIFIMAC_PATH=\"/data/wifimac.txt\"
endif
endif

ifeq ($(CONFIG_EXT_CLK), y)
ccflags-y += -DCONFIG_EXT_CLK
endif

ifeq ($(CONFIG_TRAFFIC_PROTECT), y)
ccflags-y += -DCONFIG_TRAFFIC_PROTECT
endif

ifeq ($(CONFIG_LOAD_PHY_PARA_FROM_FILE), y)
ccflags-y += -DCONFIG_LOAD_PHY_PARA_FROM_FILE
#ccflags-y += -DREALTEK_CONFIG_PATH_WITH_IC_NAME_FOLDER
ccflags-y += -DREALTEK_CONFIG_PATH=\"/lib/firmware/\"
endif

ifeq ($(CONFIG_TXPWR_BY_RATE), n)
ccflags-y += -DCONFIG_TXPWR_BY_RATE=0
else ifeq ($(CONFIG_TXPWR_BY_RATE), y)
ccflags-y += -DCONFIG_TXPWR_BY_RATE=1
endif
ifeq ($(CONFIG_TXPWR_BY_RATE_EN), n)
ccflags-y += -DCONFIG_TXPWR_BY_RATE_EN=0
else ifeq ($(CONFIG_TXPWR_BY_RATE_EN), y)
ccflags-y += -DCONFIG_TXPWR_BY_RATE_EN=1
else ifeq ($(CONFIG_TXPWR_BY_RATE_EN), auto)
ccflags-y += -DCONFIG_TXPWR_BY_RATE_EN=2
endif

ifeq ($(CONFIG_TXPWR_LIMIT), n)
ccflags-y += -DCONFIG_TXPWR_LIMIT=0
else ifeq ($(CONFIG_TXPWR_LIMIT), y)
ccflags-y += -DCONFIG_TXPWR_LIMIT=1
endif
ifeq ($(CONFIG_TXPWR_LIMIT_EN), n)
ccflags-y += -DCONFIG_TXPWR_LIMIT_EN=0
else ifeq ($(CONFIG_TXPWR_LIMIT_EN), y)
ccflags-y += -DCONFIG_TXPWR_LIMIT_EN=1
else ifeq ($(CONFIG_TXPWR_LIMIT_EN), auto)
ccflags-y += -DCONFIG_TXPWR_LIMIT_EN=2
endif

ifneq ($(CONFIG_RTW_CHPLAN), 0xFF)
ccflags-y += -DCONFIG_RTW_CHPLAN=$(CONFIG_RTW_CHPLAN)
endif

ifeq ($(CONFIG_CALIBRATE_TX_POWER_BY_REGULATORY), y)
ccflags-y += -DCONFIG_CALIBRATE_TX_POWER_BY_REGULATORY
endif

ifeq ($(CONFIG_CALIBRATE_TX_POWER_TO_MAX), y)
ccflags-y += -DCONFIG_CALIBRATE_TX_POWER_TO_MAX
endif

ifeq ($(CONFIG_RTW_ADAPTIVITY_EN), disable)
ccflags-y += -DCONFIG_RTW_ADAPTIVITY_EN=0
else ifeq ($(CONFIG_RTW_ADAPTIVITY_EN), enable)
ccflags-y += -DCONFIG_RTW_ADAPTIVITY_EN=1
else ifeq ($(CONFIG_RTW_ADAPTIVITY_EN), auto)
ccflags-y += -DCONFIG_RTW_ADAPTIVITY_EN=2
endif

ifeq ($(CONFIG_RTW_ADAPTIVITY_MODE), normal)
ccflags-y += -DCONFIG_RTW_ADAPTIVITY_MODE=0
else ifeq ($(CONFIG_RTW_ADAPTIVITY_MODE), carrier_sense)
ccflags-y += -DCONFIG_RTW_ADAPTIVITY_MODE=1
endif

ifeq ($(CONFIG_SIGNAL_SCALE_MAPPING), y)
ccflags-y += -DCONFIG_SIGNAL_SCALE_MAPPING
endif

ifeq ($(CONFIG_80211W), y)
ccflags-y += -DCONFIG_IEEE80211W
endif

ifeq ($(CONFIG_WOWLAN), y)
ccflags-y += -DCONFIG_WOWLAN -DRTW_WAKEUP_EVENT=$(CONFIG_WAKEUP_TYPE)
ccflags-y += -DRTW_SUSPEND_TYPE=$(CONFIG_SUSPEND_TYPE)
ifeq ($(CONFIG_WOW_STA_MIX), y)
ccflags-y += -DRTW_WOW_STA_MIX
endif
ifeq ($(CONFIG_SDIO_HCI), y)
ccflags-y += -DCONFIG_RTW_SDIO_PM_KEEP_POWER
endif
endif

ifeq ($(CONFIG_AP_WOWLAN), y)
ccflags-y += -DCONFIG_AP_WOWLAN
ifeq ($(CONFIG_AP_MODE), n)
ccflags-y += -DCONFIG_AP_MODE
endif
ifeq ($(CONFIG_SDIO_HCI), y)
ccflags-y += -DCONFIG_RTW_SDIO_PM_KEEP_POWER
endif
endif

ifeq ($(CONFIG_LAYER2_ROAMING), y)
ccflags-y += -DCONFIG_LAYER2_ROAMING -DCONFIG_ROAMING_FLAG=$(CONFIG_ROAMING_FLAG)
endif

ifeq ($(CONFIG_PNO_SUPPORT), y)
ccflags-y += -DCONFIG_PNO_SUPPORT
ifeq ($(CONFIG_PNO_SET_DEBUG), y)
ccflags-y += -DCONFIG_PNO_SET_DEBUG
endif
endif

ifeq ($(CONFIG_GPIO_WAKEUP), y)
ccflags-y += -DCONFIG_GPIO_WAKEUP
ifeq ($(CONFIG_ONE_PIN_GPIO), y)
ccflags-y += -DCONFIG_RTW_ONE_PIN_GPIO
endif
ifeq ($(CONFIG_HIGH_ACTIVE_DEV2HST), y)
ccflags-y += -DHIGH_ACTIVE_DEV2HST=1
else
ccflags-y += -DHIGH_ACTIVE_DEV2HST=0
endif
endif

ifeq ($(CONFIG_HIGH_ACTIVE_HST2DEV), y)
ccflags-y += -DHIGH_ACTIVE_HST2DEV=1
else
ccflags-y += -DHIGH_ACTIVE_HST2DEV=0
endif

ifneq ($(CONFIG_WAKEUP_GPIO_IDX), default)
ccflags-y += -DWAKEUP_GPIO_IDX=$(CONFIG_WAKEUP_GPIO_IDX)
endif

ifeq ($(CONFIG_RTW_SDIO_PM_KEEP_POWER), y)
ifeq ($(CONFIG_SDIO_HCI), y)
ccflags-y += -DCONFIG_RTW_SDIO_PM_KEEP_POWER
endif
endif

ifeq ($(CONFIG_REDUCE_TX_CPU_LOADING), y)
ccflags-y += -DCONFIG_REDUCE_TX_CPU_LOADING
endif

ifeq ($(CONFIG_BR_EXT), y)
BR_NAME = br0
ccflags-y += -DCONFIG_BR_EXT
ccflags-y += '-DCONFIG_BR_EXT_BRNAME="'$(BR_NAME)'"'
endif

ifeq ($(CONFIG_TDLS), y)
ccflags-y += -DCONFIG_TDLS
endif

ifeq ($(CONFIG_WIFI_MONITOR), y)
ccflags-y += -DCONFIG_WIFI_MONITOR
endif

ifeq ($(CONFIG_MCC_MODE), y)
ccflags-y += -DCONFIG_MCC_MODE
endif

ifeq ($(CONFIG_RTW_NAPI), y)
ccflags-y += -DCONFIG_RTW_NAPI
endif

ifeq ($(CONFIG_RTW_GRO), y)
ccflags-y += -DCONFIG_RTW_GRO
endif

ifeq ($(CONFIG_RTW_REPEATER_SON), y)
ccflags-y += -DCONFIG_RTW_REPEATER_SON
endif

ifeq ($(CONFIG_RTW_IPCAM_APPLICATION), y)
ccflags-y += -DCONFIG_RTW_IPCAM_APPLICATION
ifeq ($(CONFIG_WIFI_MONITOR), n)
ccflags-y += -DCONFIG_WIFI_MONITOR
endif
endif

ifeq ($(CONFIG_RTW_NETIF_SG), y)
ccflags-y += -DCONFIG_RTW_NETIF_SG
endif

ifeq ($(CONFIG_ICMP_VOQ), y)
ccflags-y += -DCONFIG_ICMP_VOQ
endif

ifeq ($(CONFIG_IP_R_MONITOR), y)
ccflags-y += -DCONFIG_IP_R_MONITOR
endif

ifeq ($(CONFIG_MP_VHT_HW_TX_MODE), y)
ccflags-y += -DCONFIG_MP_VHT_HW_TX_MODE
ifeq ($(CONFIG_PLATFORM_I386_PC), y)
## For I386 X86 ToolChain use Hardware FLOATING
ccflags-y += -mhard-float
else
## For ARM ToolChain use Hardware FLOATING
ccflags-y += -mfloat-abi=hard
endif
endif

ifeq ($(CONFIG_APPEND_VENDOR_IE_ENABLE), y)
ccflags-y += -DCONFIG_APPEND_VENDOR_IE_ENABLE
endif

ifeq ($(CONFIG_RTW_DEBUG), y)
ccflags-y += -DCONFIG_RTW_DEBUG
ccflags-y += -DRTW_LOG_LEVEL=$(CONFIG_RTW_LOG_LEVEL)
endif

ifeq ($(CONFIG_PROC_DEBUG), y)
ccflags-y += -DCONFIG_PROC_DEBUG
endif

ifeq ($(CONFIG_RTW_UP_MAPPING_RULE), dscp)
ccflags-y += -DCONFIG_RTW_UP_MAPPING_RULE=1
else
ccflags-y += -DCONFIG_RTW_UP_MAPPING_RULE=0
endif

ccflags-y += -DDM_ODM_SUPPORT_TYPE=0x04

ifeq ($(CONFIG_RTW_MBO), y)
ccflags-y += -DCONFIG_RTW_MBO -DCONFIG_RTW_80211K -DCONFIG_RTW_WNM -DCONFIG_RTW_BTM_ROAM
ccflags-y += -DCONFIG_RTW_80211R
endif

ifeq ($(CONFIG_REGD_SRC_FROM_OS), y)
ccflags-y += -DCONFIG_REGD_SRC_FROM_OS
endif

ifeq ($(CONFIG_FORCE_SW_CHANNEL_PLAN), y)
ccflags-y += -DCONFIG_FORCE_SW_CHANNEL_PLAN
endif

ifeq ($(CONFIG_SEC_AMSDU_MODE), non-spp)
ccflags-y += -DRTW_AMSDU_MODE=0
else ifeq ($(CONFIG_SEC_AMSDU_MODE), spp)
ccflags-y += -DRTW_AMSDU_MODE=1
else ifeq ($(CONFIG_SEC_AMSDU_MODE), disable)
ccflags-y += -DRTW_AMSDU_MODE=2
endif

USER_MODULE_NAME ?=
ifneq ($(USER_MODULE_NAME),)
MODULE_NAME := $(USER_MODULE_NAME)
endif

ifneq ($(KERNELRELEASE),)

########### this part for *.mk ############################
include $(src)/hal/phydm/phydm.mk

rtk_core := core/rtw_cmd.o \
                core/rtw_security.o \
                core/rtw_debug.o \
                core/rtw_io.o \
                core/rtw_ioctl_query.o \
                core/rtw_ioctl_set.o \
                core/rtw_ieee80211.o \
                core/rtw_mlme.o \
                core/rtw_mlme_ext.o \
                core/rtw_mi.o \
                core/rtw_wlan_util.o \
                core/rtw_vht.o \
                core/rtw_pwrctrl.o \
                core/rtw_rf.o \
                core/rtw_chplan.o \
                core/monitor/rtw_radiotap.o \
                core/rtw_recv.o \
                core/rtw_sta_mgt.o \
                core/rtw_ap.o \
                core/wds/rtw_wds.o \
                core/mesh/rtw_mesh.o \
                core/mesh/rtw_mesh_pathtbl.o \
                core/mesh/rtw_mesh_hwmp.o \
                core/rtw_xmit.o \
                core/rtw_p2p.o \
                core/rtw_rson.o \
                core/rtw_tdls.o \
                core/rtw_br_ext.o \
                core/rtw_iol.o \
                core/rtw_sreset.o \
                core/rtw_btcoex_wifionly.o \
                core/rtw_btcoex.o \
                core/rtw_beamforming.o \
                core/rtw_odm.o \
                core/rtw_rm.o \
                core/rtw_rm_fsm.o \
                core/rtw_ft.o \
                core/rtw_wnm.o \
                core/rtw_mbo.o \
                core/rtw_rm_util.o \
                core/efuse/rtw_efuse.o \
                core/rtw_roch.o

ccflags-y += -I$(src)/core/crypto
rtk_core += \
                core/crypto/aes-internal.o \
                core/crypto/aes-internal-enc.o \
                core/crypto/aes-gcm.o \
                core/crypto/aes-ccm.o \
                core/crypto/aes-omac1.o \
                core/crypto/ccmp.o \
                core/crypto/gcmp.o \
                core/crypto/aes-siv.o \
                core/crypto/aes-ctr.o \
                core/crypto/sha256-internal.o \
                core/crypto/sha256.o \
                core/crypto/sha256-prf.o \
                core/crypto/rtw_crypto_wrap.o \
                core/rtw_swcrypto.o

$(MODULE_NAME)-y += $(rtk_core)

$(MODULE_NAME)-$(CONFIG_WAPI_SUPPORT) += core/rtw_wapi.o        \
                                        core/rtw_wapi_sms4.o

$(MODULE_NAME)-y += $(_OS_INTFS_FILES)
$(MODULE_NAME)-y += $(_HAL_INTFS_FILES)
$(MODULE_NAME)-y += $(_PHYDM_FILES)
$(MODULE_NAME)-y += $(_BTC_FILES)
$(MODULE_NAME)-y += $(_PLATFORM_FILES)

$(MODULE_NAME)-$(CONFIG_MP_INCLUDED) += core/rtw_mp.o

obj-$(CONFIG_RTL8723DU) := $(MODULE_NAME).o

else

export CONFIG_RTL8723DU = m

all: modules

modules:
	$(MAKE) ARCH=$(ARCH) CROSS_COMPILE=$(CROSS_COMPILE) -C $(KSRC) M=$(shell pwd)  modules

strip:
	$(CROSS_COMPILE)strip $(MODULE_NAME).ko --strip-unneeded

install:
	install -p -m 644 $(MODULE_NAME).ko  $(MODDESTDIR)
	/sbin/depmod -a ${KVER}

uninstall:
	rm -f $(MODDESTDIR)/$(MODULE_NAME).ko
	/sbin/depmod -a ${KVER}

backup_rtlwifi:
	@echo "Making backup rtlwifi drivers"
ifneq (,$(wildcard $(STAGINGMODDIR)/rtl*))
	@tar cPf $(wildcard $(STAGINGMODDIR))/backup_rtlwifi_driver.tar $(wildcard $(STAGINGMODDIR)/rtl*)
	@rm -rf $(wildcard $(STAGINGMODDIR)/rtl*)
endif
ifneq (,$(wildcard $(MODDESTDIR)realtek))
	@tar cPf $(MODDESTDIR)backup_rtlwifi_driver.tar $(MODDESTDIR)realtek
	@rm -fr $(MODDESTDIR)realtek
endif
ifneq (,$(wildcard $(MODDESTDIR)rtl*))
	@tar cPf $(MODDESTDIR)../backup_rtlwifi_driver.tar $(wildcard $(MODDESTDIR)rtl*)
	@rm -fr $(wildcard $(MODDESTDIR)rtl*)
endif
	@/sbin/depmod -a ${KVER}
	@echo "Please reboot your system"

restore_rtlwifi:
	@echo "Restoring backups"
ifneq (,$(wildcard $(STAGINGMODDIR)/backup_rtlwifi_driver.tar))
	@tar xPf $(STAGINGMODDIR)/backup_rtlwifi_driver.tar
	@rm $(STAGINGMODDIR)/backup_rtlwifi_driver.tar
endif
ifneq (,$(wildcard $(MODDESTDIR)backup_rtlwifi_driver.tar))
	@tar xPf $(MODDESTDIR)backup_rtlwifi_driver.tar
	@rm $(MODDESTDIR)backup_rtlwifi_driver.tar
endif
ifneq (,$(wildcard $(MODDESTDIR)../backup_rtlwifi_driver.tar))
	@tar xPf $(MODDESTDIR)../backup_rtlwifi_driver.tar
	@rm $(MODDESTDIR)../backup_rtlwifi_driver.tar
endif
	@/sbin/depmod -a ${KVER}
	@echo "Please reboot your system"

config_r:
	@echo "make config"
	/bin/bash script/Configure script/config.in

.PHONY: modules clean

clean:
        #$(MAKE) -C $(KSRC) M=$(shell pwd) clean
	cd hal ; rm -fr */*/*/*.mod.c */*/*/*.mod */*/*/*.o */*/*/.*.cmd */*/*/*.ko
	cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
	cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
	cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
	cd core ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
	cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
	cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
	cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
	cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
	rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
	rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
	rm -fr .tmp_versions
endif