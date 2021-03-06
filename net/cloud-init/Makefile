# $FreeBSD$

PORTNAME=	cloud-init
PORTVERSION=	0.7.6
PORTREVISION=	1
CATEGORIES=	net python
MASTER_SITES=	http://launchpad.net/${PORTNAME}/trunk/${PORTVERSION}/+download/
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Init scripts for use on cloud images

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	dmidecode>0:sysutils/dmidecode \
		sudo>0:security/sudo \
		gpart>0:sysutils/gpart \
		${PYTHON_PKGNAMEPREFIX}boto>0:devel/py-boto@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}Jinja2>0:devel/py-Jinja2@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}prettytable>0:devel/py-prettytable@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}configobj>0:devel/py-configobj@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}yaml>0:devel/py-yaml@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}six>0:devel/py-six@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}serial>0:comms/py-serial@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}requests>0:www/py-requests@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}oauth>0:net/py-oauth@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}jsonpatch>0:devel/py-jsonpatch@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}jsonpointer>0:devel/py-jsonpointer@${PY_FLAVOR}

ETCDIR=		${PREFIX}/etc/cloud

USES=		python:2.7 shebangfix
SHEBANG_FILES=	tools/validate-yaml.py tools/read-dependencies \
		tools/read-version tools/hacking.py
USE_PYTHON=	autoplist distutils

PYDISTUTILS_INSTALLARGS+=	"--init-system=sysvinit_freebsd"

ONLY_FOR_ARCHS=		amd64 i386
ONLY_FOR_ARCHS_REASON=	currently depends on dmidecode which is x86-only

post-patch:
	@${RM} ${WRKSRC}/sysvinit/freebsd/cloudinit.orig

post-build:
	@cd ${WRKSRC} && ${MV} config/cloud.cfg-freebsd config/cloud.cfg

.include <bsd.port.mk>
