Modified commands for ESP32-c3

# Dockerfile
```dockerfile
ARG TOOLCHAIN_LIST="-t xtensa-espressif_esp32_zephyr-elf -t xtensa-espressif_esp32s2_zephyr-elf -t xtensa-espressif_esp32s3_zephyr-elf -t riscv64-zephyr-elf"
```

# Local Docker build
```powershell
docker run --rm -it -p 8080:8080 -v $pwd/workspace:/workspace -w /workspace env-zephyr-espressif
```

# Container CLI
``` bash
west build -p always -b xiao_esp32c3
```

# Local Serial
```powershell
python -m esptool --port "COM6" --chip auto --baud 921600 --before default_reset --after hard_reset write_flash -u --flash_mode keep --flash_freq 40m --flash_size detect 0x0 workspace/apps/blink/build/zephyr/zephyr.bin
```


```powershell
python -m serial.tools.miniterm "COM6" 115200
```