---
title: SMCI Build Environment Setup

---

[TOC]

# SMCI Build Environment Setup
# OBMC Open source:
git clone https://github.com/openbmc/openbmc.git
cd openbmc
`export TEMPLATECONF=$(pwd)/meta-supermicro/meta-x11spi/conf/templates/
default`
`. oe-init-build-env`
bitbake -c cleanall obmc-phosphor-image
unset BB_ENV_EXTRAWHITE
export BB_ENV_PASSTHROUGH_ADDITIONS="$BB_ENV_PASSTHROUGH_ADDITIONS"

# Build Delta Next
git clone git@gitlab.supermicro.com:hw2_sw/deltanext
sudo make sx13_rot2hw2_ast26_dn_p ver=1.03.20 core=24 dg=y 2>&1 | tee build.log
sudo make sx13_rot2hw2_ast26_dn_p  signfile=images/AST2600_all.bin

# Build LBMC
- https://gitlab.supermicro.com/hw2_sw/center/-/wikis/Project-Build-Command
sudo make sx13_rot2hw2_ast26_p ver=9.90.15 core=8 dg=y
sudo make sx13_rot2hw2_ast26_p signfile=images/AST2600_all.bin
sudo make sx13_rot2hw2_ast26_p ver=9.90.15 core=8 P=Kernel dg=y <= 全部build過一次後也可以partial build更快
 
## Build SMCI OBMC config
- For OBMC X14 ROT:
`TEMPLATECONF=meta-supermicro/meta-x14-ast2600-rot/conf . openbmc-env`
- For OBMC X14 DCSCM:
`TEMPLATECONF=meta-supermicro/meta-x14-ast2600-dcscm/conf . openbmc-env`
- For OBMC X14-DBG-DAP:
`TEMPLATECONF=meta-supermicro/meta-x14-ast2600-deltanext/conf . openbmc-env`
- For OBMC H14:
`TEMPLATECONF=meta-supermicro/meta-h14-ast2600-dcscm/conf . openbmc-env`
- For Google H13 SVW:
`branch: google-h13-svw-dev-rebase-1.11`
`TEMPLATECONF=meta-supermicro/meta-h13-ast2600-svw/conf . openbmc-env`
## Build SMCI OBMC image:
`SMCI_FW_SIGN=product SMCI_BMC_VERSION=09.25.03.11 time bitbake -v obmc-phosphor-image`
[TOC]

# SMCI Build Environment Setup
# OBMC Open source:
git clone https://github.com/openbmc/openbmc.git
cd openbmc
`export TEMPLATECONF=$(pwd)/meta-supermicro/meta-x11spi/conf/templates/
default`
`. oe-init-build-env`
bitbake -c cleanall obmc-phosphor-image
unset BB_ENV_EXTRAWHITE
export BB_ENV_PASSTHROUGH_ADDITIONS="$BB_ENV_PASSTHROUGH_ADDITIONS"

# Build Delta Next
git clone git@gitlab.supermicro.com:hw2_sw/deltanext
sudo make sx13_rot2hw2_ast26_dn_p ver=1.03.20 core=24 dg=y 2>&1 | tee build.log
sudo make sx13_rot2hw2_ast26_dn_p  signfile=images/AST2600_all.bin

# Build LBMC
- https://gitlab.supermicro.com/hw2_sw/center/-/wikis/Project-Build-Command
sudo make sx13_rot2hw2_ast26_p ver=9.90.15 core=8 dg=y
sudo make sx13_rot2hw2_ast26_p signfile=images/AST2600_all.bin
sudo make sx13_rot2hw2_ast26_p ver=9.90.15 core=8 P=Kernel dg=y <= 全部build過一次後也可以partial build更快
 
## Build SMCI OBMC config
- For OBMC X14 ROT:
`TEMPLATECONF=meta-supermicro/meta-x14-ast2600-rot/conf . openbmc-env`
- For OBMC X14 DCSCM:
`TEMPLATECONF=meta-supermicro/meta-x14-ast2600-dcscm/conf . openbmc-env`
- For OBMC X14-DBG-DAP:
`TEMPLATECONF=meta-supermicro/meta-x14-ast2600-deltanext/conf . openbmc-env`
- For OBMC H14:
`TEMPLATECONF=meta-supermicro/meta-h14-ast2600-dcscm/conf . openbmc-env`
- For Google H13 SVW:
`branch: google-h13-svw-dev-rebase-1.11`
`TEMPLATECONF=meta-supermicro/meta-h13-ast2600-svw/conf . openbmc-env`
## Build SMCI OBMC image:
`SMCI_FW_SIGN=product SMCI_BMC_VERSION=09.25.03.11 time bitbake -v obmc-phosphor-image`
