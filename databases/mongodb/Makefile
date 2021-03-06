# Created by: Mirko Zinn <mail@derzinn.de>
# $FreeBSD$

PORTNAME=	mongodb
PORTVERSION=	2.6.12
PORTREVISION=	4
CATEGORIES=	databases net
MASTER_SITES=	http://downloads.mongodb.org/src/
DISTNAME=	${PORTNAME}-src-r${PORTVERSION}

PATCH_SITES=	https://github.com/${PORTNAME}/${PORTNAME:S|db$||}/commit/
PATCHFILES=	0ee4735ab8fb.patch:-p1

MAINTAINER=	ale@FreeBSD.org
COMMENT=	NOSQL distributed document-oriented database

EXPIRATION_DATE=	2018-07-23
DEPRECATED=	End of Life October 2016

# mongodb is AGPLv3, C++ driver is APACHE20
LICENSE=	AGPLv3 APACHE20
LICENSE_COMB=	multi

BROKEN_SSL=	openssl-devel
BROKEN_SSL_REASON_openssl-devel=	use of undeclared identifier 'BIO_s_file_internal'

LIB_DEPENDS=	libpcre.so:devel/pcre \
		libsnappy.so:archivers/snappy \
		libv8.so:lang/v8 \
# boost 1.52/1.55 from ports make mongod segfaulting with many tests
# LIB_DEPENDS+=	libboost_system.so:devel/boost-libs
# MAKE_ARGS+=	--use-system-boost
# use bundled yaml
# MAKE_ARGS+=	--use-system-yaml
# LIB_DEPENDS+=	libyaml-cpp.so:devel/yaml-cpp

ONLY_FOR_ARCHS=	i386 amd64
ONLY_FOR_ARCHS_REASON=	"not yet ported to anything other than i386 and amd64"

OPTIONS_DEFINE=	SSL SASL TEST
OPTIONS_DEFAULT=SSL
TEST_DESC=	Add support for running regression test

USES=		cpe scons
MAKE_ARGS=	--prefix=${STAGEDIR}${PREFIX} --cc=${CC} --cxx=${CXX} \
		--use-system-pcre --use-system-snappy --use-system-v8

USERS=	mongodb
GROUPS=	mongodb

USE_RC_SUBR=	mongod

PORTSCOUT=	limitw:1,even

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MSSL}
USES+=		ssl
MAKE_ARGS+=	--ssl
.endif

.if ${PORT_OPTIONS:MSASL}
MAKE_ARGS+=	--use-sasl-client
LIB_DEPENDS+=	libsasl2.so:security/cyrus-sasl2
.endif

.if ${PORT_OPTIONS:MTEST}
USES+=		python:build
BUILD_DEPENDS=	${PYTHON_PKGNAMEPREFIX}pymongo>=2.5:databases/pymongo@${PY_FLAVOR}
TEST_TARGET=	smokeAll smokeCppUnittests
.	if ${PORT_OPTIONS:MSSL}
TEST_TARGET+=	smokeSsl
.	endif
.else
ALL_TARGET=	core tools
.endif

post-patch:
	@${REINPLACE_CMD} 's/\["-O3"\]/"${CXXFLAGS}"/' \
		${WRKSRC}/SConstruct

.if ${PORT_OPTIONS:MTEST}
test: build-depends build
	@cd ${BUILD_WRKSRC} && ${SETENV} ${MAKE_ENV} \
		${MAKE_CMD} ${_MAKE_JOBS} ${MAKE_ARGS} ${TEST_TARGET}
.endif

.include <bsd.port.mk>
