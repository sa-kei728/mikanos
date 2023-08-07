TARGET = kernel.elf
OBJS = main.o

CXXFLAGS += -O2 -Wall -g --target=x86_64-elf -ffreestanding -mno-red-zone \
            -fno-exceptions -fno-rtti -fshort-wchar -std=c++17
LDFLAGS  += --entry KernelMain -z norelro --image-base 0x100000 --static

CXXFLAGS += -I/usr/include/c++/11 -I/usr/include/x86_64-linux-gnu/ -I/usr/include/x86_64-linux-gnu/c++/11/

.PHONY: all
all: $(TARGET)

.PHONY: clean
clean:
	rm -rf *.o

kernel.elf: $(OBJS) Makefile
	ld.lld $(LDFLAGS) -o kernel.elf $(OBJS)

%.o: %.cpp Makefile
	clang++ $(CPPFLAGS) $(CXXFLAGS) -c $<