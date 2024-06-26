
include $(top_srcdir)/Makefile.tool-tests.am

dist_noinst_SCRIPTS = filter_cpuid filter_inf_nan filter_stderr gen_insn_test.pl

CLEANFILES = $(addsuffix .c,$(INSN_TESTS))

INSN_TESTS = insn_basic insn_cmov insn_mmx insn_mmxext insn_sse insn_sse2

if BUILD_SSSE3_TESTS
   INSN_TESTS += insn_ssse3
endif
if BUILD_SSE3_TESTS
if !SOLARIS_SUN_STUDIO_AS
# Sun Studio assembler fails to build some tests (illegal mnemonic).
   INSN_TESTS += insn_sse3
endif
endif

if !SOLARIS_SUN_STUDIO_AS
# Sun Studio assembler fails to build some tests (illegal mnemonic).
   INSN_TESTS += insn_fpu
endif

# Explicitly include insn_sse3 even if ! BUILD_SSE3_TESTS, 
# to avoid packaging screwups if 'make dist' is run on a machine
# which failed the BUILD_SSE3_TESTS test in configure.in.

## FIXME: move lzcnt32 to SSE4 conditionalisation, when that happens.

EXTRA_DIST = \
	aad_aam.stdout.exp aad_aam.stderr.exp aad_aam.vgtest \
	badseg.stderr.exp badseg.stdout.exp badseg.stdout.exp-solaris \
	badseg.vgtest \
	bswapw.stderr.exp bswapw.stdout.exp bswapw.vgtest \
	bt_everything.stderr.exp bt_everything.stdout.exp bt_everything.vgtest \
	bt_literal.stderr.exp bt_literal.stdout.exp bt_literal.vgtest \
	bug125959-x86.stderr.exp bug125959-x86.stdout.exp bug125959-x86.vgtest \
	bug126147-x86.stderr.exp bug126147-x86.stdout.exp bug126147-x86.vgtest \
	bug132813-x86.stderr.exp bug132813-x86.stdout.exp bug132813-x86.vgtest \
	bug135421-x86.stderr.exp bug135421-x86.stdout.exp bug135421-x86.vgtest \
	bug137714-x86.stderr.exp bug137714-x86.stdout.exp bug137714-x86.vgtest \
	bug152818-x86.stderr.exp bug152818-x86.stdout.exp bug152818-x86.vgtest \
	cet_nops.stderr.exp cet_nops.stdout.exp cet_nops.vgtest \
	cmpxchg8b.stderr.exp cmpxchg8b.stdout.exp cmpxchg8b.vgtest \
	cpuid.stderr.exp cpuid.stdout.exp cpuid.vgtest \
	cse_fail.stderr.exp cse_fail.stdout.exp cse_fail.vgtest \
	faultstatus.disabled faultstatus.stderr.exp \
	fcmovnu.vgtest fcmovnu.stderr.exp fcmovnu.stdout.exp \
	fpu_lazy_eflags.stderr.exp fpu_lazy_eflags.stdout.exp \
	fpu_lazy_eflags.vgtest \
	fxtract.stdout.exp fxtract.stderr.exp fxtract.vgtest \
	fxtract.stdout.exp-older-glibc \
	getseg.stdout.exp getseg.stderr.exp getseg.vgtest \
	gnu_binutils_nop.stderr.exp gnu_binutils_nop.vgtest \
	incdec_alt.stdout.exp incdec_alt.stderr.exp incdec_alt.vgtest \
	int.stderr.exp int.stdout.exp int.disabled \
	$(addsuffix .stderr.exp,$(INSN_TESTS)) \
	$(addsuffix .stdout.exp,$(INSN_TESTS)) \
	$(addsuffix .vgtest,$(INSN_TESTS)) \
	insn_fpu.stdout.exp insn_fpu.stderr.exp insn_fpu.vgtest \
	insn_sse.stdout.exp insn_sse.stderr.exp insn_sse.vgtest \
	insn_sse2.stdout.exp insn_sse2.stderr.exp insn_sse2.vgtest \
	insn_sse3.stdout.exp insn_sse3.stderr.exp insn_sse3.vgtest \
	insn_ssse3.stdout.exp insn_ssse3.stderr.exp insn_ssse3.vgtest \
	jcxz.stdout.exp jcxz.stderr.exp jcxz.vgtest \
	lahf.stdout.exp lahf.stderr.exp lahf.vgtest \
	looper.stderr.exp looper.stdout.exp looper.vgtest \
	lzcnt32.stderr.exp lzcnt32.stdout.exp lzcnt32.vgtest \
	movx.stderr.exp movx.stdout.exp movx.vgtest \
	movbe.stderr.exp movbe.stdout.exp movbe.vgtest \
	pushpopseg.stderr.exp pushpopseg.stdout.exp pushpopseg.vgtest \
	sbbmisc.stderr.exp sbbmisc.stdout.exp sbbmisc.vgtest \
	shift_ndep.stderr.exp shift_ndep.stdout.exp shift_ndep.vgtest \
	smc1.stderr.exp smc1.stdout.exp smc1.vgtest \
	ssse3_misaligned.stderr.exp ssse3_misaligned.stdout.exp \
	ssse3_misaligned.vgtest ssse3_misaligned.c \
	sse4-x86.stdout.exp sse4-x86.stderr.exp sse4-x86.vgtest \
	x86locked.vgtest x86locked.stdout.exp x86locked.stderr.exp \
	x87trigOOR.vgtest x87trigOOR.stdout.exp x87trigOOR.stderr.exp \
	yield.stderr.exp yield.stdout.exp yield.disabled \
	xadd.stdout.exp xadd.stderr.exp xadd.vgtest

check_PROGRAMS = \
	aad_aam \
	allexec \
	badseg \
	bswapw \
	bt_everything \
	bt_literal \
	bug125959-x86 \
	bug126147-x86 \
	bug132813-x86 \
	bug135421-x86 \
	bug137714-x86 \
	bug152818-x86 \
	cet_nops \
	cmpxchg8b \
	cpuid \
	cse_fail \
	fcmovnu \
	fpu_lazy_eflags \
	fxtract \
	getseg \
	gnu_binutils_nop \
	incdec_alt \
	$(INSN_TESTS) \
	int \
	jcxz \
	lahf \
	looper \
	movx \
	sbbmisc \
	shift_ndep \
	smc1 \
	x86locked \
	x87trigOOR \
	yield \
	xadd
if BUILD_SSSE3_TESTS
   check_PROGRAMS += ssse3_misaligned
endif
if BUILD_SSE42_TESTS
   check_PROGRAMS += sse4-x86
endif
if BUILD_LZCNT_TESTS
 check_PROGRAMS += lzcnt32
endif
if BUILD_MOVBE_TESTS
 check_PROGRAMS += movbe
endif
if !VGCONF_OS_IS_DARWIN
if !SOLARIS_SUN_STUDIO_AS
# Sun Studio assembler fails to assemble the bound instruction
if !COMPILER_IS_CLANG
# clang errors out complaining that %eax as the 1st operand in the bound
# insn is an invalid operand.
 check_PROGRAMS += faultstatus
endif
endif
endif
if !SOLARIS_SUN_STUDIO_AS
# Sun Studio assembler fails to assemble pushw %fs, popw %fs
 check_PROGRAMS += pushpopseg
endif


AM_CFLAGS    += @FLAG_M32@ $(FLAG_MMMX) $(FLAG_MSSE)
AM_CXXFLAGS  += @FLAG_M32@ $(FLAG_MMMX) $(FLAG_MSSE)
AM_CCASFLAGS += @FLAG_M32@

allexec_CFLAGS		= $(AM_CFLAGS) @FLAG_W_NO_NONNULL@

if VGCONF_OS_IS_DARWIN
# Some of the tests (bug125959_x86, bug152818_x86, insn_*) need
# -mdynamic-no-pic.  I tried setting *_CFLAGS separately for all of them,
# but it caused problems with the generation of insn_*.c.  So just use this
# crude approach of setting -mdynamic-no-pic for all tests in this
# directory.
AM_CFLAGS += -mdynamic-no-pic
endif

cpuid_SOURCES 		= cpuid_c.c cpuid_s.S
# fpu_lazy_eflags must use these flags -- the bug only occurred with them.
fpu_lazy_eflags_CFLAGS	= $(AM_CFLAGS) -O2 -march=pentiumpro
fxtract_CFLAGS		= $(AM_CFLAGS) @FLAG_W_NO_OVERFLOW@
fxtract_LDADD		= -lm
insn_basic_SOURCES	= insn_basic.def
insn_basic_LDADD	= -lm
insn_fpu_SOURCES	= insn_fpu.def
insn_fpu_LDADD		= -lm
insn_cmov_SOURCES	= insn_cmov.def
insn_cmov_LDADD		= -lm
insn_mmx_SOURCES	= insn_mmx.def
insn_mmx_LDADD		= -lm
insn_mmxext_SOURCES	= insn_mmxext.def
insn_mmxext_LDADD	= -lm
insn_sse_SOURCES	= insn_sse.def
insn_sse_LDADD		= -lm
insn_sse2_SOURCES	= insn_sse2.def
insn_sse2_LDADD		= -lm
insn_sse3_SOURCES	= insn_sse3.def
insn_sse3_LDADD		= -lm
insn_ssse3_SOURCES	= insn_ssse3.def
insn_ssse3_LDADD	= -lm
x86locked_CFLAGS	= $(AM_CFLAGS) -O
yield_LDADD		= -lpthread

.def.c:
	$(PERL) $(srcdir)/gen_insn_test.pl < $< > $@
