# $FreeBSD$

PORTNAME=	kscreenlocker
DISTVERSION=	${KDE_PLASMA_VERSION}
CATEGORIES=	security kde kde-plasma

MAINTAINER=	kde@FreeBSD.org
COMMENT=	Plasma5 secure lock screen architecture

LIB_DEPENDS=	libwayland-client.so:graphics/wayland \
		libxcb-keysyms.so:x11/xcb-util-keysyms
RUN_DEPENDS=	ck-list-sessions:sysutils/consolekit2\
		dbus-send:devel/dbus

USES=		cmake:outsource compiler:c++11-lib cpe gettext kde:5 pkgconfig \
		qt:5 shebangfix tar:xz
USE_KDE=	auth codecs config configwidgets coreaddons crash ecm \
		emoticons globalaccel i18n idletime init itemmodels kcmutils \
		kdeclarative kdelibs4support notifications package \
		plasma-framework sonnet textwidgets wayland widgetsaddons \
		windowsystem xmlgui
USE_QT=		core dbus gui network qml quick testlib widgets x11extras xml \
		buildtools_build qmake_build
USE_XORG=	ice sm x11 xcb xcursor xext xi

SHEBANG_FILES=	updaters/ksreenlocker_5_3_separate_autologin.pl

# Install a generic console kit based program to unlock the screen in the event
# of a failure.
SUB_FILES=	ck-unlock-session

post-install:
	${INSTALL_SCRIPT} ${WRKDIR}/ck-unlock-session ${STAGEDIR}${PREFIX}/bin

.include <bsd.port.mk>
