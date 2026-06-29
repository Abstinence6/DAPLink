# DAPLink

<!-- AI-ASSISTANT-NOTES:START -->
## Мапа роботи для AI-агентів

Останнє оновлення: 2026-06-28. Цей розділ написаний для агентів кодування, яким потрібно швидко зрозуміти репозиторій.

Імена файлів, API, символів, гілок, команд і форматів залишені без перекладу навмисно.

### Призначення

Fork з Arm Mbed DAPLink: CMSIS-DAP/debug probe firmware, bootloader/application sources, board/HIC/target records and build/test tooling.

### Тип проєкту

Large embedded C firmware fork.

### Основні точки входу і ролі файлів

- `README.md` - upstream project overview
- `projects.yaml` - build matrix tying boards/HICs/targets to source records
- `records/board/*.yaml` - board definitions
- `records/hic/*.yaml` - host interface chip definitions
- `records/target/*.yaml` - target MCU/family definitions
- `source/` - bootloader, DAPLink application, CMSIS-DAP, USB/MSD/UART and target support code
- `tools/` - build/release/test helper scripts
- `docs/` - developer, porting, troubleshooting and user guides

### Індекс джерел

- Показано 45 з 1066 текстових source-файлів; generated/vendor/build-heavy області навмисно підсумовані.
- `test/board.py` - Python-модуль; символи: disable_popup, get_all_attached_daplink_boards, _unique_id_to_host_id, _get_board_endpoints, _ranges, _parse_kvp_file, _compute_crc, _run_chkdsk, AssertInfo, __init__, file, line, DaplinkBoard, __str__
- `test/bundle.py` - Python-модуль; символи: load_bundle_from_release, load_bundle_from_project, FirmwareBundle, get_firmware_list, build_sha, build_local_mods, ReleaseFirmwareBundle, __init__, ProjectFirmwareBundle
- `test/firmware.py` - Python-модуль; символи: Firmware, TYPE, __str__, name, hic_id, type, bin_path, hex_path, elf_path, DAPLinkFirmware, __init__, valid, ReleaseFirmware
- `test/info.py` - Python-модуль; символи: VENDOR_TO_FAMILY
- `test/mbedapi.py` - Python-модуль; символи: build_repo
- `test/run_test.py` - Python-модуль; символи: test_endpoints, TestConfiguration, __init__, __str__, TestManager, _STATE, all_tests_pass, set_test_first_board_only, set_load_if, set_load_bl, set_test_daplink, set_test_ep, add_firmware, add_boards
- `test/target.py` - Python-модуль; символи: load_target_bundle, TargetBundle, __init__, get_target_list, build_target_bundle, Target, __str__, set_hex_path, set_bin_path, valid, name, hex_path, bin_path
- `test/test_info.py` - Python-модуль; символи: TestInfo, __init__, failure, warning, info, print_msg, get_failed, get_warning, get_name, create_subtest, attach_subtest, get_counts, _update_counts, _add_entry
- `tools/combine_images.py` - Python-модуль; символи: ranges, print_hex_info, merge_hex, main
- `tools/copy_release_files.py` - Python-модуль; символи: generate_info_files, main
- `tools/dap_info.py` - Python-модуль
- `tools/flash_algo.py` - Python-модуль; символи: main, PackFlashAlgo, __init__, format_algo_data, process_template, _extract_symbols, _find_sections, _algo_fill_zi_if_missing, _algo_check_for_section_problems, _create_algo_bin, PackFlashInfo, __str__, _sector_and_sz_itr, ElfFileSimple
- `tools/generate_config.py` - Python-модуль; символи: create_hex, str_to_int, main
- `tools/generate_flash_algo.py` - Python-модуль; символи: str_to_num, PackFlashAlgoGenerator, format_algo_data, process_template, main
- `tools/mbedcli_compile.py` - Python-модуль; символи: main
- `tools/offset_update.py` - Python-модуль; символи: dec_or_hex, create_padded_image, main
- `tools/package_release_files.py` - Python-модуль; символи: literal, literal_presenter, ordered_dict_presenter, make_bin_zip, package_release_files
- `tools/post_build_script.py` - Python-модуль; символи: ranges, post_build_script
- `tools/post_build_script_armcc.py` - Python-модуль
- `tools/post_build_script_armclang.py` - Python-модуль
- `tools/post_build_script_gcc.py` - Python-модуль
- `tools/pre_build_script.py` - Python-модуль; символи: generate_version_file
- `tools/progen_compile.py` - Python-модуль; символи: load_project_list, get_core_count
- `tools/projects_sort.py` - Python-модуль
- `source/board/96b_nitrogen.c` - C реалізація
- `source/board/archble.c` - C реалізація
- `source/board/archlink.c` - C реалізація
- `source/board/archmax.c` - C реалізація
- `source/board/archpro.c` - C реалізація
- `source/board/artemis_dk.c` - C реалізація; символи: set_board_id, prerun_board_config
- `source/board/blueninja.c` - C реалізація; символи: target_set_state_by_board
- `source/board/c027.c` - C реалізація
- `source/board/ep_agora.c` - C реалізація
- `source/board/ep_kairos.c` - C реалізація
- `source/board/FF1705_L151.c` - C реалізація
- `source/board/ff_lpc546xx.c` - C реалізація
- `source/board/frdmk20dx.c` - C реалізація
- `source/board/frdmk22f.c` - C реалізація
- `source/board/frdmk28f.c` - C реалізація
- `source/board/frdmk32l3a6.c` - C реалізація
- `source/board/frdmk64f.c` - C реалізація
- `source/board/frdmk66f.c` - C реалізація
- `source/board/frdmk82f.c` - C реалізація
- `source/board/frdmke15z.c` - C реалізація
- `source/board/frdmkl02z.c` - C реалізація

### Потік виконання / даних

- YAML records select a board/HIC/target combination.
- Build tooling consumes projects.yaml and records to compile source/ into bootloader/application images.
- Runtime firmware exposes debug, drag-and-drop flash/MSD, USB serial and target programming behavior.

### Збірка, запуск або перевірка

- Follow upstream docs/DEVELOPERS-GUIDE.md and README.md build instructions.

### Підказки для AI-агентів

- This is a fork; keep upstream README intact and document local deltas separately.
- Board ports should start in records/ and docs/PORT_BOARD.md, not by editing unrelated source directly.
- Avoid committing generated build outputs.

<!-- AI-ASSISTANT-NOTES:END -->

## Existing notes


[![DAPLink](/docs/images/daplink-website-logo-link.png)](https://daplink.io/)

[![Linux Build (main)](https://github.com/ARMmbed/DAPLink/actions/workflows/linux.yml/badge.svg?branch=main)](https://github.com/ARMmbed/DAPLink/actions/workflows/linux.yml)
[![Linux Build (develop)](https://github.com/ARMmbed/DAPLink/actions/workflows/linux.yml/badge.svg?branch=develop)](https://github.com/ARMmbed/DAPLink/actions/workflows/linux.yml)
[![Join us on Slack](https://img.shields.io/static/v1?label=Slack&color=4A154B&logo=slack&style=social&message=Join%20us%20on%20Slack)](https://join.slack.com/t/pyocd/shared_invite/zt-zqjv6zr5-ZfGAXl_mFCGGmFlB_8riHA)

----

Arm Mbed DAPLink is an open-source software project that enables programming and debugging application software running on Arm Cortex CPUs. Commonly referred to as interface firmware, DAPLink runs on a secondary MCU that is attached to the SWD or JTAG port of the application MCU. This configuration is found on nearly all development boards. Enumerating as a USB composite device, it creates a bridge between your development computer and the CPU debug access port. DAPLink enables developers with:

* MSC - drag-n-drop programming flash memory
* CDC - virtual com port for log, trace and terminal emulation
* CMSIS-DAPv2 WinUSB (driver-less vendor-specific bulk) - CMSIS compliant debug channel
* CMSIS-DAPv1 HID - CMSIS compliant debug channel
* WebUSB CMSIS-DAP HID - CMSIS compliant debug channel

More features are planned and will show up gradually over time. The project is constantly under heavy development by Arm, its partners, numerous hardware vendors and the open-source community around the world. DAPLink has superseded the mbed CMSIS-DAP interface firmware project. You are free to use and contribute. Enjoy!

For more detailed usability information [see the users guide.](docs/USERS-GUIDE.md)

## Compatibility
There are many ARM microcontroller-based Hardware Interface Circuits (HICs) that DAPLink interface firmware runs on. These can be found as standalone boards (debugger) or as part of a development kit. Some branded circuits that are known to be IO compatible are:

* [Maxim Integrated MAX32625PICO based on MAX32625](https://www.maximintegrated.com/en/products/microcontrollers/MAX32625PICO.html)
* Nuvoton Nu-Link2-Me based on M48SSIDAE
* [NXP LPC-Link2 based on LPC11U35 or LPC4322](https://www.nxp.com/support/developer-resources/hardware-development-tools/lpcxpresso-boards:LPCXPRESSO-BOARDS)
* [NXP MCU-LINK on LPC55xx](https://www.nxp.com/design/microcontrollers-developer-resources/mcu-link-debug-probe:MCU-LINK)
* [NXP OpenSDA based on K20, K22, KL26Z and KL27Z](http://www.nxp.com/products/software-and-tools/run-time-software/kinetis-software-and-tools/ides-for-kinetis-mcus/opensda-serial-and-debug-adapter:OPENSDA)
* [Segger J-Link OB based on Atmel SAM3U](https://www.segger.com/products/debug-probes/j-link/models/j-link-ob/)
* [STMicroelectronics ST-LINK/V2 (on NUCLEO boards) based on STM32F103CB](https://www.st.com/en/evaluation-tools/stm32-nucleo-boards.html)

You can find more information on the microcontrollers supported [here](docs/hic/README.md).

## Releases
There are many board builds (board = HIC + target combination) created from this repository. Quarterly releases will contain new features and bugfixes. Standalone bugfixes are released once reported, verified and fixed. Both quarterly and bugfix releases will result in the build number being incremented. Many development kits and products ship with DAPLink interface firmware or are capable of running DAPLink firmware. **[The current release builds and instructions for updating DAPLink interface firmware is hosted on the DAPLink release site.](https://daplink.io/)** Release notes and previous release builds can be found under GitHub releases.

## Contribute

We welcome contributions to DAPLink in any area. Look for an interesting feature or defect
[under issues](https://github.com/ARMmbed/DAPLink/issues). Start a new thread [in the
discussions](https://github.com/ARMmbed/DAPLink/discussions) or
[in Slack](https://join.slack.com/t/pyocd/shared_invite/zt-zqjv6zr5-ZfGAXl_mFCGGmFlB_8riHA)
to engage with the developers and maintainers.

Please see the [contribution guidelines](CONTRIBUTING.md) for detailed requirements for
contributions.

To report bugs, please [create an issue](https://github.com/ARMmbed/DAPLink/issues/new) in the
GitHub project.

## Develop
Information for setting up a development environment, running the tests or creating a release build [can be found in the developers guide.](docs/DEVELOPERS-GUIDE.md)

## License
DAPLink is licensed with the permissive Apache 2.0 license. See the [LICENSE](LICENSE) file for the
full text of the license.

Copyright © 2006-2023 Arm Ltd
