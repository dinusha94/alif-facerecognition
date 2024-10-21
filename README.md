# alif-senzmate

## Command to build the use case    

mkdir build_hp  
cd build_hp  
cmake -DTARGET_PLATFORM=ensemble -DTARGET_SUBSYSTEM=RTSS-HP -DTARGET_BOARD=AppKit -DTARGET_REVISION=B -DCMAKE_TOOLCHAIN_FILE=scripts/cmake/toolchains/bare-metal-gcc.cmake -DCMAKE_BUILD_TYPE=Release -DUSE_CASE_BUILD=alif_object_detection -DLOG_LEVEL=LOG_LEVEL_DEBUG ..  

make ethos-u-alif_object_detection -j  

cd build_hp/bin/sectors/alif_object_detection/  
mv mram.bin ethos-u-alif_object_detection.bin  

move the ethos-u-alif_object_detection.bin file to app-release-exec-linux/build/images folder  


## Commands to upload to the AI ML Appkit  

### content of the obj_detection.json    
```
{
    "HP_Detection": {
        "binary": "ethos-u-alif_object_detection.bin",
        "version" : "1.0.0",
        "mramAddress": "0x80008000",
        "cpu_id": "M55_HP",
        "flags": ["boot"],
        "signed": false
    }
}
```  

cd app-release-exec-linux/  
./app-gen-toc -f build/config/obj_detection.json  
sudo ./app-write-mram -p  
