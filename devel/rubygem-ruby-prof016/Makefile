# $FreeBSD$

PORTNAME=	ruby-prof
PORTVERSION=	0.16.2
CATEGORIES=	devel rubygems
MASTER_SITES=	RG
PKGNAMESUFFIX=	016

MAINTAINER=	mfechner@FreeBSD.org
COMMENT=	Fast profiler for Ruby

LICENSE=	BSD2CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

DEPRECATED=	Obsoleted by update of www/gitlab. Please use devel/rubygem-ruby-prof instead.
EXPIRATION_DATE=	2018-06-30

PORTSCOUNT=	limit:^0\.16
CONFLICTS_INSTALL=	rubygem-ruby-prof

USES=		gem
USE_RUBY=	yes

PLIST_FILES=	bin/ruby-prof bin/ruby-prof-check-trace

.include <bsd.port.mk>
