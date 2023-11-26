cmake_minimum_required(VERSION 3.22)

project(AudioPlugin VERSION 0.0.1)

juce_add_plugin(${PROJECT_NAME}
        COMPANY_NAME Mangl
        IS_SYNTH FALSE
        NEEDS_MIDI_INPUT TRUE
        NEEDS_MIDI_OUTPUT FALSE
        IS_MIDI_EFFECT FALSE
        PLUGIN_MANUFACTURER_CODE Mngl
        PLUGIN_CODE Shft
        FORMATS AU VST3 Standalone
        PRODUCT_NAME "Audio Plugin"
)

juce_generate_juce_header(${PROJECT_NAME})

target_sources(${PROJECT_NAME}
        PRIVATE
        source/PluginEditor.cpp
        source/PluginProcessor.cpp
)

target_include_directories(${PROJECT_NAME} PRIVATE source)

target_compile_definitions(${PROJECT_NAME}
        PUBLIC
        JUCE_WEB_BROWSER=0
        JUCE_USE_CURL=0
        JUCE_VST3_CAN_REPLACE_VST2=0
)

target_link_libraries(${PROJECT_NAME}
        PRIVATE
        juce::juce_audio_utils
        PUBLIC
        juce::juce_recommended_config_flags
        juce::juce_recommended_lto_flags
        juce::juce_recommended_warning_flags
)

