# $FreeBSD$

PORTNAME=	kdecoration
DISTVERSION=	${KDE_PLASMA_VERSION}
CATEGORIES=	x11-wm kde kde-plasma

MAINTAINER=	kde@FreeBSD.org
COMMENT=	Plasma5 library to create window decorations

LICENSE=	LGPL21
LICENSE_FILE=	${WRKSRC}/COPYING.LIB

USES=		cmake:outsource compiler:c++11-lib cpe kde:5 qt:5 tar:xz
USE_LDCONFIG=	yes
USE_KDE=	ecm
USE_QT=		core gui testlib buildtools_build qmake_build

.include <bsd.port.mk>
