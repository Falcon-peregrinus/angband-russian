## Makefile.am -- Process this file with automake to process Makefile.in

SUBDIRS = lua

bin_PROGRAMS = angband

WRES = windres

SUFFIXES = .rc
angband.res: angband.rc
	$(WRES) $< -O coff -o $@

angband_LDADD = lua/liblua.a @ANGBAND_OBJS@
angband_DEPENDENCIES = lua/liblua.a @ANGBAND_OBJS@

angband_SOURCES = \
  z-util.c z-virt.c z-form.c z-rand.c z-term.c \
  variable.c tables.c util.c cave.c \
  object1.c object2.c monster1.c monster2.c \
  xtra1.c xtra2.c spells1.c spells2.c \
  melee1.c melee2.c save.c files.c \
  cmd1.c cmd2.c cmd3.c cmd4.c cmd5.c cmd6.c \
  store.c birth.c load.c \
  wizard1.c wizard2.c \
  main-cap.c main-gcu.c main-x11.c main-xaw.c main.c \
  main-win.c main-xpj.c main-vcs.c main-gtk.c \
  generate.c dungeon.c init1.c init2.c randart.c \
  angband.h config.h defines.h externs.h h-basic.h \
  h-config.h h-define.h h-system.h h-type.h init.h \
  types.h z-form.h z-rand.h z-term.h z-util.h \
  z-virt.h main.h \
  script.c script.h \
  l-monst.c l-object.c l-player.c l-random.c l-ui.c l-misc.c l-spell.c \
  use-obj.c x-spell.c \
  obj-info.c

l-monst.c: lua/tolua l-monst.pkg
	lua/tolua -n monster -o l-monst.c l-monst.pkg

l-object.c: lua/tolua l-object.pkg
	lua/tolua -n object -o l-object.c l-object.pkg

l-player.c: lua/tolua l-player.pkg
	lua/tolua -n player -o l-player.c l-player.pkg

l-random.c: lua/tolua l-random.pkg
	lua/tolua -n random -o l-random.c l-random.pkg

l-ui.c: lua/tolua l-ui.pkg
	lua/tolua -n ui -o l-ui.c l-ui.pkg

l-misc.c: lua/tolua l-misc.pkg
	lua/tolua -n misc -o l-misc.c l-misc.pkg

l-spell.c: lua/tolua l-spell.pkg
	lua/tolua -n spell -o l-spell.c l-spell.pkg

EXTRA_angband_SOURCES = \
  main-ros.c main-ami.c main-dos.c main-emx.c \
  main-ibm.c main-lsl.c main-mac.c main-sla.c main-vme.c \
  main-xxx.c main-crb.c \
  Makefile.ros Makefile.ami Makefile.bcc Makefile.cyg \
  Makefile.dos Makefile.emx Makefile.gtk Makefile.ibm \
  Makefile.lcc Makefile.lsl Makefile.std Makefile.wat \
  Makefile.win Makefile.mpw \
  angband.rc angband.ico readdib.c readdib.h \
  maid-x11.c maid-x11.h \
  l-monst.pkg l-object.pkg l-player.pkg l-random.pkg l-ui.pkg \
  l-misc.pkg l-spell.pkg

install-exec-hook:
if SET_GID
	chgrp "@GAMEGROUP@" "$(DESTDIR)$(bindir)/angband"
	chmod g+s "$(DESTDIR)$(bindir)/angband"
endif

