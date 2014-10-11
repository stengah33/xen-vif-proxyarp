# Script for configuring a vif in proxy arp mode.
# It is a mix of parts of vir-bridge and vir-route scripts.
# The hotplugging system will call this script if it is specified either in
# the device configuration given to Xend, or the default Xend configuration
# in ${XEN_CONFIG_DIR}/xend-config.sxp.  If the script is specified in
# neither of those places, then this script is the default.
#
# Usage:
# vif-proxyarp (add|remove|online|offline)
#
# Environment vars:
# vif         vif interface name (required).
# XENBUS_PATH path to this device's details in the XenStore (required).
#
# Read from the store:
# bridge  bridge to add the vif to (optional).  Defaults to searching for the
#         bridge itself.
# ip      list of IP networks for the vif, space-separated (optional).
#
# up:
# Enslaves the vif interface to the bridge and adds iptables rules
# for its ip addresses (if any).
#
# down:
# Removes the vif interface from the bridge and removes the iptables
# rules for its ip addresses (if any).
#
# Created by stengah33 <stengah33@gmail.com>
