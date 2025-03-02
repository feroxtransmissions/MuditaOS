add_library(service-appmgr STATIC)

target_sources(service-appmgr
    PRIVATE
        ApplicationManifest.cpp
        Controller.cpp
        data/CallActionsParams.cpp
        data/MmiActionsParams.cpp
        data/NotificationsChangedActionsParams.cpp
        messages/ActionRequest.cpp
        messages/ApplicationCloseRequest.cpp
        messages/ApplicationInitialised.cpp
        messages/ApplicationStatus.cpp
        messages/BaseMessage.cpp
        messages/CloseConfirmation.cpp
        messages/DOMRequest.cpp
        messages/FinishRequest.cpp
        messages/LanguageChangeRequest.cpp
        messages/PowerSaveModeInitRequest.cpp
        messages/PreventBlockingRequest.cpp
        messages/ShutdownRequest.cpp
        messages/StartAllowedMessage.cpp
        messages/SwitchBackRequest.cpp
        messages/SwitchConfirmation.cpp
        messages/SwitchRequest.cpp
        messages/FinalizingClose.cpp
        model/ActionsRegistry.cpp
        model/ApplicationHandle.cpp
        model/ApplicationManagerCommon.cpp
        model/ApplicationStack.cpp
        model/ApplicationsRegistry.cpp
        model/OnActionPolicy.cpp
    PUBLIC
        include/service-appmgr/Actions.hpp
        include/service-appmgr/ApplicationManifest.hpp
        include/service-appmgr/Constants.hpp
        include/service-appmgr/Controller.hpp
        include/service-appmgr/StartupType.hpp
        include/service-appmgr/data/CallActionsParams.hpp
        include/service-appmgr/data/MmiActionsParams.hpp
        include/service-appmgr/data/NotificationsChangedActionsParams.hpp
        include/service-appmgr/messages/ActionRequest.hpp
        include/service-appmgr/messages/ApplicationCloseRequest.hpp
        include/service-appmgr/messages/ApplicationInitialised.hpp
        include/service-appmgr/messages/ApplicationStatus.hpp
        include/service-appmgr/messages/AutoLockRequests.hpp
        include/service-appmgr/messages/BaseMessage.hpp
        include/service-appmgr/messages/CloseConfirmation.hpp
        include/service-appmgr/messages/DOMRequest.hpp
        include/service-appmgr/messages/FinishRequest.hpp
        include/service-appmgr/messages/GetAllNotificationsRequest.hpp
        include/service-appmgr/messages/GetCurrentDisplayLanguageRequest.hpp
        include/service-appmgr/messages/GetCurrentDisplayLanguageResponse.hpp
        include/service-appmgr/messages/LanguageChangeRequest.hpp
        include/service-appmgr/messages/Message.hpp
        include/service-appmgr/messages/PowerSaveModeInitRequest.hpp
        include/service-appmgr/messages/PreventBlockingRequest.hpp
        include/service-appmgr/messages/ShutdownRequest.hpp
        include/service-appmgr/messages/StartAllowedMessage.hpp
        include/service-appmgr/messages/SwitchBackRequest.hpp
        include/service-appmgr/messages/SwitchConfirmation.hpp
        include/service-appmgr/messages/SwitchRequest.hpp
        include/service-appmgr/messages/UserPowerDownRequest.hpp
        include/service-appmgr/messages/FinalizingClose.hpp
        include/service-appmgr/model/ActionsRegistry.hpp
        include/service-appmgr/model/ApplicationHandle.hpp
        include/service-appmgr/model/ApplicationManagerCommon.hpp
        include/service-appmgr/model/ApplicationStack.hpp
        include/service-appmgr/model/ApplicationsRegistry.hpp
        include/service-appmgr/model/OnActionPolicy.hpp
)

target_link_libraries(service-appmgr
    PRIVATE
        application-special-input
        json::json
        module-audio
        service-cellular
        service-desktop
        service-db
        service-gui
    PUBLIC
        apps-common
        utils-time
)

target_include_directories(service-appmgr
    PRIVATE
        $<BUILD_INTERFACE:
            ${CMAKE_CURRENT_SOURCE_DIR}/include/service-appmgr
            ${CMAKE_CURRENT_SOURCE_DIR}/include/service-appmgr/data
            ${CMAKE_CURRENT_SOURCE_DIR}/include/service-appmgr/messages
            ${CMAKE_CURRENT_SOURCE_DIR}/include/service-appmgr/model
        >
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
)

if (${ENABLE_TESTS})
    add_subdirectory(tests)
endif()
