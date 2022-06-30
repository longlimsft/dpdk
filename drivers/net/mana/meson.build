# SPDX-License-Identifier: BSD-3-Clause
# Copyright(c) 2022 Microsoft Corporation

if not is_linux or dpdk_conf.get('RTE_ARCH_X86_64') != 1
    build = false
    reason = 'mana is supported on Linux X86_64'
    subdir_done()
endif

deps += ['pci', 'bus_pci', 'net', 'eal', 'kvargs']

sources += files(
	'mana.c',
	'rx.c',
	'tx.c',
	'mr.c',
	'gdma.c',
	'mp.c',
)

lib = cc.find_library('ibverbs', required:false)
if lib.found()
    ext_deps += lib
else
    build = false
    reason = 'missing dependency ibverbs'
    subdir_done()
endif


lib = cc.find_library('mana', required:false)
if lib.found()
    ext_deps += lib
else
    build = false
    reason = 'missing dependency mana'
    subdir_done()
endif
