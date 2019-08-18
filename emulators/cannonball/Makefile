# $FreeBSD: head/emulators/cannonball/Makefile 506026 2019-07-06 18:55:17Z swills $

PORTNAME=	cannonball
DISTVERSION=	g20171201
PORTREVISION=	1
CATEGORIES=	emulators games

MAINTAINER=	santhosh.raju@gmail.com
COMMENT=	Enhanced OutRun Engine

LICENSE=	MAME-LICENSE
LICENSE_NAME=	MAME license
LICENSE_FILE=	${WRKSRC}/docs/license.txt
LICENSE_PERMS=	dist-mirror no-dist-sell pkg-mirror no-pkg-sell auto-accept

LIB_DEPENDS=	libboost_program_options.so:devel/boost-libs

USES=		cmake:insource pkgconfig sdl
USE_SDL=	sdl

CMAKE_ARGS+=	${WRKSRC}/cmake
CMAKE_ARGS+=	-DTARGET=bsd
CMAKE_ARGS+=	-DBSD_PREFIX_PATH=${LOCALBASE}

USE_GITHUB=	yes
GH_ACCOUNT=	djyt
GH_TAGNAME=	0c0814d

BUILD_WRKSRC=		${WRKSRC}/cmake
CONFIGURE_WRKSRC=	${WRKSRC}/cmake

SUB_FILES=	${PORTNAME}.sh ${PORTNAME}.6

do-install:
	${MKDIR} ${STAGEDIR}${DATADIR}/res
	${MKDIR} ${STAGEDIR}${DATADIR}/conf
	${INSTALL_DATA} ${WRKSRC}/cmake/res/tilemap.bin ${STAGEDIR}${DATADIR}/res/tilemap.bin
	${INSTALL_DATA} ${WRKSRC}/cmake/res/tilepatch.bin ${STAGEDIR}${DATADIR}/res/tilepatch.bin
	${INSTALL_DATA} ${WRKSRC}/cmake/config.xml ${STAGEDIR}${DATADIR}/conf/config.xml
	${INSTALL_MAN} ${WRKDIR}/cannonball.6 ${STAGEDIR}${MAN1PREFIX}/man/man6
	${INSTALL_SCRIPT} ${WRKDIR}/${PORTNAME}.sh ${STAGEDIR}${PREFIX}/bin/${PORTNAME}
	${INSTALL_PROGRAM} ${WRKSRC}/cmake/cannonball ${STAGEDIR}${PREFIX}/libexec

.include <bsd.port.mk>
