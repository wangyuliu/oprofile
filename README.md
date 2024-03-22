[  491s] operf_utils.cpp:1423:9: error: 'rmb' was not declared in this scope
[  491s]  1423 |         rmb();
[  491s]       |         ^~~
[  491s] make[2]: *** [Makefile:474: operf_utils.o] Error 1

#define RISCV_FENCE(p, s) \
	__asm__ __volatile__ ("fence " #p "," #s : : : "memory")

/* These barriers need to enforce ordering on both devices or memory. */
#define mb()		RISCV_FENCE(iorw,iorw)
#define rmb()		RISCV_FENCE(ir,ir)
#define wmb()		RISCV_FENCE(ow,ow)
