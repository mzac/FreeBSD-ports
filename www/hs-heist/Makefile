# $FreeBSD$

PORTNAME=	heist
PORTVERSION=	1.1
PORTREVISION=	1
CATEGORIES=	www haskell

MAINTAINER=	haskell@FreeBSD.org
COMMENT=	Haskell template system supporting both HTML5 and XML

LICENSE=	BSD3CLAUSE

USE_CABAL=	aeson attoparsec blaze-builder blaze-html directory-tree \
		dlist hashable lifted-base map-syntax monad-control mtl \
		random transformers-base unordered-containers vector \
		xmlhtml

.include "${.CURDIR}/../../lang/ghc/bsd.cabal.mk"
.include <bsd.port.mk>
