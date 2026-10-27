# rm-hacks-qmd v0.0.11-pre6

Port of 0.0.11-pre5 to reMarkable OS 3.29.0.153 (Qt 6.10). Tested on rM2.

Current state of the port:

- ✅ base
- ✅ split_doc (based on the 3.26 version; `onOpened` is replaced wholesale because qmldiff cannot rebuild functions with destructured or default arguments)

---

- ✅ all_mono_hack.qmd (3.29 dropped the global `ScreenModeItem`; a new one is added to `MainView`)
- ✅ alphabetize_tags_list_hack.qmd
- ✅ auto_new_page_hack.qmd
- ✅ bookmarks.qmd
- ✅ document_battery_wifi_hack.qmd (`WifiManager` is gone; the icon now only reflects online/offline/airplane mode via `LinkProvider`)
- ✅ document_clock_hack.qmd
- ✅ document_pages_hide_hack.qmd
- ✅ force_refresh_gesture_hack.qmd (3.29 removed the stock 5-finger ghostbuster gesture; the hack re-adds it)
- ✅ hide_close_button_hack.qmd
- ✅ hide_text_tool_hack.qmd (`ToolbarTool.shouldShow`)
- ✅ last_document_gesture_hack.qmd
- ✅ switch_pens_gesture_hack.qmd
- ✅ light_sleep_icon_hack.qmd (banner moved to `xofm.modules.sleepscreen`)
- ✅ more_stroke_sizes_hack.qmd
- ✅ more_colors_hack.qmd is unnecessary on 3.29: the new `StrokeColorProfile` already exposes all pen and highlighter colors, so the toggle was dropped.
- ✅ navigator_compressed_list_hack.qmd (list thumbnail is no longer a Loader; the hack swaps the thumbnail image for an icon)
- ✅ new_notebook_date_name_hack.qmd
- ✅ screenshare_everywhere_hack.qmd
- ✅ share_tool_settings_hack.qmd
- ✅ share_tool_toggle_all_gestures_hack.qmd
- ✅ share_tool_toggle_wifi_hack.qmd (toggles airplane mode via `Settings`)
- ✅ table_of_contents_button_hack.qmd (3.29 only loads the TOC eagerly for ebooks; the hack requests it for PDFs/notebooks on open)
- ✅ toggle_eraser_gesture_hack.qmd
- ✅ toggle_toolbar_gesture_hack.qmd
- ✅ toolbar_pages_button_hack.qmd
- ✅ toolbar_width_hack.qmd
- ✅ floating.qmd (fixed a stray `ToolbarTool.Type.ToolButton`, which is not a member of the enum)

Other notes:

- The settings page root objects (`Settings.qml`, `Battery.qml`, `SortDropdown.qml`, `TagsFilter.qml`) changed from `DeviceKeyboardNavigationHandler` to plain `Item`/`FocusScope`; `xofm.libs.qtgui` became `xofm.bindings.qt`; `xofm.libs.wifimanager` and `device.system` are gone.
- Requires qt-resource-rebuilder >= pre-v20-08092026 (xovi 0.3.3) for Qt 6.10.
