all: payload.bin payload-702.bin payload-3gb.bin payload-702-3gb.bin payload-755.bin payload-755-3gb.bin payload-900.bin payload-900-3gb.bin

clean:
	rm -f payload.elf payload.bin payload-702.elf payload-702.bin payload-755.elf payload-755.bin payload-3gb.elf payload-3gb.bin payload-702-3gb.elf payload-702-3gb.bin payload-755-3gb.elf payload-755-3gb.bin payload-900.bin payload-900.elf payload-900-3gb.bin payload-900-3gb.elf

../lib/lib.a:
	cd ../lib; make

payload.elf: ../lib/lib.a main.c ps4-kexec-672/kexec.bin
	gcc -isystem ../freebsd-headers -nostdinc -nostdlib -fno-stack-protector -static ../lib/lib.a main.c -Wl,-gc-sections -o payload.elf -fPIE -ffreestanding

payload.bin: payload.elf
	objcopy payload.elf --only-section .text --only-section .data --only-section .bss --only-section .rodata -O binary payload.bin
	file payload.bin | fgrep -q 'payload.bin: DOS executable (COM)'

payload-702.elf: ../lib/lib.a main.c ps4-kexec-702/kexec.bin
	gcc -isystem ../freebsd-headers -nostdinc -nostdlib -fno-stack-protector -static ../lib/lib.a -D__7_02__ main.c -Wl,-gc-sections -o payload-702.elf -fPIE -ffreestanding

payload-702.bin: payload-702.elf
	objcopy payload-702.elf --only-section .text --only-section .data --only-section .bss --only-section .rodata -O binary payload-702.bin
	file payload-702.bin | fgrep -q 'payload-702.bin: DOS executable (COM)'

payload-755.elf: ../lib/lib.a main.c ps4-kexec-755/kexec.bin
	gcc -isystem ../freebsd-headers -nostdinc -nostdlib -fno-stack-protector -static ../lib/lib.a -D__7_55__ main.c -Wl,-gc-sections -o payload-755.elf -fPIE -ffreestanding

payload-755.bin: payload-755.elf
	objcopy payload-755.elf --only-section .text --only-section .data --only-section .bss --only-section .rodata -O binary payload-755.bin
	file payload-755.bin | fgrep -q 'payload-755.bin: DOS executable (COM)'

payload-3gb.elf: ../lib/lib.a main.c ps4-kexec-672/kexec.bin
	gcc -isystem ../freebsd-headers -nostdinc -nostdlib -fno-stack-protector -static ../lib/lib.a -DVRAM_GB_DEFAULT=3 main.c -Wl,-gc-sections -o payload-3gb.elf -fPIE -ffreestanding

payload-3gb.bin: payload-3gb.elf
	objcopy payload-3gb.elf --only-section .text --only-section .data --only-section .bss --only-section .rodata -O binary payload-3gb.bin
	file payload-3gb.bin | fgrep -q 'payload-3gb.bin: DOS executable (COM)'

payload-702-3gb.elf: ../lib/lib.a main.c ps4-kexec-702/kexec.bin
	gcc -isystem ../freebsd-headers -nostdinc -nostdlib -fno-stack-protector -static ../lib/lib.a -D__7_02__ -DVRAM_GB_DEFAULT=3 main.c -Wl,-gc-sections -o payload-702-3gb.elf -fPIE -ffreestanding

payload-702-3gb.bin: payload-702-3gb.elf
	objcopy payload-702-3gb.elf --only-section .text --only-section .data --only-section .bss --only-section .rodata -O binary payload-702-3gb.bin
	file payload-702-3gb.bin | fgrep -q 'payload-702-3gb.bin: DOS executable (COM)'

payload-755-3gb.elf: ../lib/lib.a main.c ps4-kexec-755/kexec.bin
	gcc -isystem ../freebsd-headers -nostdinc -nostdlib -fno-stack-protector -static ../lib/lib.a -D__7_55__ -DVRAM_GB_DEFAULT=3 main.c -Wl,-gc-sections -o payload-755-3gb.elf -fPIE -ffreestanding

payload-755-3gb.bin: payload-755-3gb.elf
	objcopy payload-755-3gb.elf --only-section .text --only-section .data --only-section .bss --only-section .rodata -O binary payload-755-3gb.bin
	file payload-755-3gb.bin | fgrep -q 'payload-755-3gb.bin: DOS executable (COM)'

payload-900.elf: ../lib/lib.a main.c ps4-kexec-900/kexec.bin
	gcc -isystem ../freebsd-headers -nostdinc -nostdlib -fno-stack-protector -static ../lib/lib.a -D__9_00__ main.c -Wl,-gc-sections -o payload-900.elf -fPIE -ffreestanding

payload-900.bin: payload-900.elf
	objcopy payload-900.elf --only-section .text --only-section .data --only-section .bss --only-section .rodata -O binary payload-900.bin
	file payload-900.bin | fgrep -q 'payload-900.bin: DOS executable (COM)'

payload-900-3gb.elf: ../lib/lib.a main.c ps4-kexec-900/kexec.bin
	gcc -isystem ../freebsd-headers -nostdinc -nostdlib -fno-stack-protector -static ../lib/lib.a -D__9_00__ -DVRAM_GB_DEFAULT=3 main.c -Wl,-gc-sections -o payload-900-3gb.elf -fPIE -ffreestanding

payload-900-3gb.bin: payload-900-3gb.elf
	objcopy payload-900-3gb.elf --only-section .text --only-section .data --only-section .bss --only-section .rodata -O binary payload-900-3gb.bin
	file payload-900-3gb.bin | fgrep -q 'payload-900-3gb.bin: DOS executable (COM)'

ps4-kexec-672/kexec.bin:
	cd ps4-kexec-672; make

ps4-kexec-702/kexec.bin:
	cd ps4-kexec-702; make

ps4-kexec-755/kexec.bin:
	cd ps4-kexec-755; make

ps4-kexec-900/kexec.bin:
	cd ps4-kexec-900; make
