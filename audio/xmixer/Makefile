# Created by: trevor
# $FreeBSD$

PORTNAME=	xmixer
PORTVERSION=	0.9.4
PORTREVISION=	7
CATEGORIES=	audio
MASTER_SITES=	http://mpx.freeshell.net/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Audio mixer (gtk and Xlib) for X11R6

WRKSRC=		${WRKDIR}/${PORTNAME}

GNU_CONFIGURE=	yes
ALL_TARGET=	${PROGRAMS}

PLIST_FILES=	bin/xmixer \
		man/man1/xmixer.1.gz

OPTIONS_DEFINE=	GTK1

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MGTK1}
USE_GNOME+=	gtk12
PROGRAMS=	xmixer xgmixer
PLIST_FILES+=	bin/xgmixer
.else
USE_XORG=	x11 xt ice xaw
PROGRAMS=	xmixer
LDFLAGS+=	-L${LOCALBASE}/lib -lX11
.endif

post-patch:
	@${GREP} -lR "rxvt -e" ${WRKSRC} | ${XARGS} ${REINPLACE_CMD} -e \
		's|rxvt -e|xterm -e|g'
	@${REINPLACE_CMD} -e 's|-O -Wall||g ; \
		 s|^%\.o:.*$$|.c.o:|g ; \
		 s|gtk-config|pkg-config gtk+|g' ${WRKSRC}/Makefile.in
	@${REINPLACE_CMD} -e 's|<getopt\.h>|<unistd.h>|g' ${WRKSRC}/main.c

do-install:
.for file in ${PROGRAMS}
	${INSTALL_PROGRAM} ${WRKSRC}/${file} ${STAGEDIR}${PREFIX}/bin/${file}
.endfor
	${INSTALL_MAN} ${WRKSRC}/xmixer.man ${STAGEDIR}${MAN1PREFIX}/man/man1/xmixer.1

.include <bsd.port.mk>
