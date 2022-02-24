# Prodos-512kB-NVRAM-Drive
A card with 512kB NVRAM for Apple/2 compatible computers which is a ProDOS compliant R/W device.
A card for Apple][ computers with 512kB NVRAM A periferal card for Apple][.
This is a project based on my NVRAM card which is intended to work with NVRAM chip 39SF040 and compatible.
The NVRAM is organized in 256 banks of 2kB each, numbered #00 to #FF Banks are selected by writing a byte (#00 - #FF) into $C0Nx, where N = 8 + [slot number].
When writing to $C0Nx at the same time the NVRAM chip is also enabled. When a bank is selected, its content are seen in the address space $C800-$CFFF.
To de-enable the NVRAM chip a write must be performed to address $CFFF or reset executed If a user program is accessing the card,
it is important that at the end a write is performed to $CFFF so that the card is deactivated and does not conflict with other hardware,
which is using the same address space.
The bootloader is programmed in the highest 256 bytes of the chip.The boot loader is always available at addresses $CM00-$CMFF, where M = [slot number].
The bootloader can also be seen at addresses $CF00-$CFFF of bank #FF.
The image contains a ProDOS volume which is loaded by the boot loader. Additional firmware resdes in ProDOS Block $01.
Recommended installation is on Slot 7. The boot loader has functionality that it captures the boot sequence of the computer and loads ProDOS.
If ”\” is pressed before performing a cold reset – the boot sequence will override the NVRAM Drive so the floppy disk can boot.
www.clintech.net/romcard
