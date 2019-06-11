# $FreeBSD$

PORTNAME=	cannonball
DISTVERSION=	g20171201
CATEGORIES=	emulators

MAINTAINER=	santhosh.raju@gmail.com
COMMENT=	Enhanced OutRun Engine

LICENSE=	MAME-LICENSE
LICENSE_NAME=	MAME license
LICENSE_FILE=	${WRKSRC}/docs/license.txt
LICENSE_PERMS=	dist-mirror no-dist-sell pkg-mirror no-pkg-sell auto-accept

LIB_DEPENDS=	libboost_program_options.so:devel/boost-libs

USES=		cmake:insource pkgconfig sdl
USE_SDL=	sdl

USE_GITHUB=	yes
GH_ACCOUNT=	djyt
GH_TAGNAME=	0c0814d

BUILD_WRKSRC=		${WRKSRC}/build
CONFIGURE_WRKSRC=	${WRKSRC}/build

SUB_FILES=	${PORTNAME}.sh

pre-configure:
	${MKDIR} ${WRKSRC}/build

do-configure:
	cd ${WRKSRC}/build && cmake -G "Unix Makefiles" -DTARGET=bsd ${WRKSRC}/cmake

do-build:
	cd ${WRKSRC}/build && make

do-install:
	${MKDIR} ${STAGEDIR}${DATADIR}/res
	${MKDIR} ${STAGEDIR}${DATADIR}/conf
	${INSTALL_DATA} ${WRKSRC}/build/res/tilemap.bin \
	    ${STAGEDIR}${DATADIR}/res/tilemap.bin
	${INSTALL_DATA} ${WRKSRC}/build/res/tilepatch.bin \
	    ${STAGEDIR}${DATADIR}/res/tilepatch.bin
	${INSTALL_DATA} ${WRKSRC}/build/config.xml \
	    ${STAGEDIR}${DATADIR}/conf/config.xml
	${INSTALL_SCRIPT} ${WRKDIR}/${PORTNAME}.sh \
	    ${STAGEDIR}${PREFIX}/bin/${PORTNAME}
	${INSTALL_PROGRAM} ${WRKSRC}/build/cannonball \
	    ${STAGEDIR}${PREFIX}/libexec

.include <bsd.port.mk>
