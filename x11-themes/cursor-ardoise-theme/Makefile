# Created by: lightside <lightside@gmx.com>
# $FreeBSD$

PORTNAME=	ardoise
PORTVERSION=	3.5
PORTREVISION=	1
CATEGORIES=	x11-themes
MASTER_SITES=	http://ftp.internat.freebsd.org/pub/FreeBSD/distfiles/${DIST_SUBDIR}/ \
		https://ftp.tw.freebsd.org/distfiles/${DIST_SUBDIR}/
PKGNAMEPREFIX=	cursor-
PKGNAMESUFFIX=	-theme
DISTFILES=	Ardoise_no_shadow_100.tar.gz Ardoise_no_shadow_75.tar.gz \
		Ardoise_no_shadow_87.tar.gz Ardoise_shadow_100.tar.gz \
		Ardoise_shadow_75.tar.gz Ardoise_shadow_87.tar.gz
DIST_SUBDIR=	${PKGNAMEPREFIX}${PORTNAME}${PKGNAMESUFFIX}/${PORTVERSION}

MAINTAINER=	lightside@gmx.com
COMMENT=	Ardoise X cursor theme

LICENSE=	CC-BY-NC-SA-3.0

NO_ARCH=	yes
NO_BUILD=	yes
NO_WRKSUBDIR=	yes

DATADIR=	${PREFIX}/share/icons
PORTDATA=	*

do-install:
	(cd ${WRKSRC} && ${COPYTREE_SHARE} "${PORTDATA}" ${STAGEDIR}${DATADIR})

.include <bsd.port.mk>
