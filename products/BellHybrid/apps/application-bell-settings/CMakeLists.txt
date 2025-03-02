﻿# Copyright (c) 2017-2021, Mudita Sp. z.o.o. All rights reserved.
# For licensing, see https://github.com/mudita/MuditaOS/LICENSE.md

add_library(application-bell-settings STATIC)
add_library(bell::app-settings ALIAS application-bell-settings)

target_include_directories(application-bell-settings
    PRIVATE
        $<BUILD_INTERFACE:
            ${CMAKE_CURRENT_SOURCE_DIR}
            data
            include/application-bell-settings
            models
            presenter
            widgets
            windows
        >
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
)

target_sources(application-bell-settings
    PRIVATE
        ApplicationBellSettings.cpp
        models/TemperatureUnitModel.cpp
        models/TimeUnitsModel.cpp
        models/advanced/AboutYourBellModel.cpp
        models/advanced/FrontlightListItemProvider.cpp
        models/advanced/FrontlightModel.cpp
        models/alarm_settings/AlarmSettingsListItemProvider.cpp
        models/alarm_settings/AlarmSettingsModel.cpp
        models/alarm_settings/BedtimeSettingsListItemProvider.cpp
        models/alarm_settings/PrewakeUpListItemProvider.cpp
        models/alarm_settings/PrewakeUpSettingsModel.cpp
        models/alarm_settings/SnoozeListItemProvider.cpp
        models/alarm_settings/SnoozeSettingsModel.cpp
        models/alarm_settings/SettingsListItemProvider.cpp

        presenter/BedtimeSettingsPresenter.cpp
        presenter/TimeUnitsPresenter.cpp
        presenter/advanced/FrontlightPresenter.cpp
        presenter/advanced/AboutYourBellWindowPresenter.cpp
        presenter/advanced/LanguageWindowPresenter.cpp
        presenter/alarm_settings/AlarmSettingsPresenter.cpp
        presenter/alarm_settings/PrewakeUpPresenter.cpp
        presenter/alarm_settings/SnoozePresenter.cpp

        widgets/TemperatureUnitListItem.cpp
        widgets/TimeFormatSetListItem.cpp
        widgets/TimeSetListItem.cpp
        widgets/advanced/AboutYourBellListItem.cpp
        widgets/DialogYesNo.cpp

        windows/BellSettingsBedtimeToneWindow.cpp
        windows/BellSettingsTimeUnitsWindow.cpp
        windows/BellSettingsHomeViewWindow.cpp
        windows/BellSettingsWindow.cpp
        windows/advanced/AboutYourBellWindow.cpp
        windows/advanced/BellSettingsAdvancedWindow.cpp
        windows/advanced/BellSettingsLanguageWindow.cpp
        windows/advanced/BellSettingsFrontlightWindow.cpp
        windows/alarm_settings/BellSettingsAlarmSettingsSnoozeWindow.cpp
        windows/alarm_settings/BellSettingsAlarmSettingsMenuWindow.cpp
        windows/alarm_settings/BellSettingsAlarmSettingsWindow.cpp
        windows/alarm_settings/BellSettingsPrewakeUpWindow.cpp

        models/advanced/AboutYourBellModel.hpp
        models/advanced/FrontlightListItemProvider.hpp
        models/advanced/FrontlightModel.hpp
        models/alarm_settings/AbstractAlarmSettingsModel.hpp
        models/alarm_settings/AbstractPrewakeUpSettingsModel.hpp
        models/alarm_settings/AbstractSnoozeSettingsModel.hpp
        models/alarm_settings/AlarmSettingsListItemProvider.hpp
        models/alarm_settings/AlarmSettingsModel.hpp
        models/alarm_settings/BedtimeSettingsListItemProvider.cpp
        models/alarm_settings/PrewakeUpListItemProvider.hpp
        models/alarm_settings/PrewakeUpSettingsModel.hpp
        models/alarm_settings/SnoozeListItemProvider.hpp
        models/alarm_settings/SnoozeSettingsModel.hpp
        models/alarm_settings/SettingsListItemProvider.hpp

        presenter/BedtimeSettingsPresenter.hpp
        presenter/advanced/FrontlightPresenter.hpp
        presenter/advanced/AboutYourBellWindowPresenter.hpp
        presenter/advanced/LanguageWindowPresenter.hpp
        presenter/alarm_settings/AlarmSettingsPresenter.hpp
        presenter/alarm_settings/PrewakeUpPresenter.hpp
        presenter/alarm_settings/SnoozePresenter.hpp

        widgets/TemperatureUnitListItem.hpp
        widgets/TimeFormatSetListItem.hpp
        widgets/TimeSetListItem.hpp
        widgets/advanced/AboutYourBellListItem.hpp
        widgets/DialogYesNo.hpp

        windows/alarm_settings/BellSettingsAlarmSettingsSnoozeWindow.hpp
        windows/alarm_settings/BellSettingsAlarmSettingsWindow.hpp
        windows/advanced/BellSettingsAdvancedWindow.hpp
        windows/BellSettingsBedtimeToneWindow.hpp
        windows/BellSettingsHomeViewWindow.hpp
        windows/BellSettingsWindow.hpp
        windows/advanced/AboutYourBellWindow.hpp
        windows/advanced/BellSettingsLanguageWindow.hpp
        windows/advanced/BellSettingsAdvancedWindow.hpp
        windows/advanced/BellSettingsFrontlightWindow.hpp
        windows/alarm_settings/BellSettingsAlarmSettingsSnoozeWindow.hpp
        windows/alarm_settings/BellSettingsAlarmSettingsMenuWindow.hpp
        windows/alarm_settings/BellSettingsAlarmSettingsWindow.hpp
        windows/alarm_settings/BellSettingsPrewakeUpWindow.hpp

        data/FinishedWindowMessageData.hpp

    PUBLIC
        include/application-bell-settings/models/TimeUnitsModel.hpp
        include/application-bell-settings/presenter/TimeUnitsPresenter.hpp
        include/application-bell-settings/windows/BellSettingsTimeUnitsWindow.hpp
        include/application-bell-settings/ApplicationBellSettings.hpp
)

target_link_libraries(application-bell-settings
    PRIVATE
        app
        bell::audio
        bellgui
        bell::db
        bell::alarms
        bell::app-main
        service-appmgr
        apps-common
    PUBLIC
        module-gui
        bell::app-common
)
