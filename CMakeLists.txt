cmake_minimum_required(VERSION 3.22)

project(AdvancedPitchShifter VERSION 0.1.0)

include(FetchContent)
FetchContent_Declare(
  JUCE
  GIT_REPOSITORY https://github.com/juce-framework/JUCE.git
  GIT_TAG 7.0.12
)
FetchContent_MakeAvailable(JUCE)

juce_add_plugin(AdvancedPitchShifter
    COMPANY_NAME "YourName"
    BUNDLE_ID    com.yourname.AdvancedPitchShifter
    IS_SYNTH FALSE
    NEEDS_MIDI_INPUT FALSE
    NEEDS_MIDI_OUTPUT FALSE
    IS_MIDI_EFFECT FALSE
    COPY_PLUGIN_AFTER_BUILD TRUE
    PLUGIN_MANUFACTURER_CODE YNm1
    PLUGIN_CODE ApS1
    FORMATS VST3 AU
    PRODUCT_NAME "Advanced Pitch Shifter")

target_sources(AdvancedPitchShifter PRIVATE
    Source/PluginProcessor.cpp
    Source/PluginProcessor.h
    Source/PluginEditor.cpp
    Source/PluginEditor.h
    Source/GranularPitchShifter.cpp
    Source/GranularPitchShifter.h)

target_compile_features(AdvancedPitchShifter PRIVATE cxx_std_20)

if(NOT CMAKE_BUILD_TYPE)
  set(CMAKE_BUILD_TYPE Release CACHE STRING "" FORCE)
endif()

target_link_libraries(AdvancedPitchShifter
    PRIVATE
      juce::juce_audio_utils
      juce::juce_dsp
    PUBLIC
      juce::juce_recommended_config_flags
      juce::juce_recommended_lto_flags
      juce::juce_recommended_warning_flags)

juce_enable_vst3_copy_dir(AdvancedPitchShifter)
