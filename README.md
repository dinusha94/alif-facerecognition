# alif-senzmate

## Command to build the asr use case    

mkdir build_he  
cd build_he 

cmake -DTARGET_PLATFORM=ensemble -DTARGET_SUBSYSTEM=RTSS-HE -DTARGET_BOARD=AppKit -DTARGET_REVISION=B -DCMAKE_TOOLCHAIN_FILE=scripts/cmake/toolchains/bare-metal-gcc.cmake -DUSE_CASE_BUILD=asr -DGLCD_UI=NO -DLINKER_SCRIPT_NAME=ensemble-RTSS-HE-TCM -DCMAKE_BUILD_TYPE=Release -DLOG_LEVEL=LOG_LEVEL_DEBUG ..  

make ethos-u-asr -j  