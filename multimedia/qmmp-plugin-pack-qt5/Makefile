# $FreeBSD$

PORTNAME=	qmmp-plugin-pack
PORTVERSION=	1.1.1
CATEGORIES=	multimedia
MASTER_SITES=	http://qmmp.ylsoftware.com/files/plugins/ \
	SF/qmmp-dev/${PORTNAME}/
PKGNAMESUFFIX=	-qt5

MAINTAINER=	liangtai.s16@gmail.com
COMMENT=	Additional plug-ins for QMMP (Qt5)

LICENSE=	GPLv2

CONFLICTS=	${PORTNAME}-0.*
PORTSCOUT=	limit:^1\..*

LIB_DEPENDS=	libqmmpui.so:multimedia/qmmp-qt5
BUILD_DEPENDS=	qmmp-qt5>=1.1.0:multimedia/qmmp-qt5

USES=		cmake:outsource pkgconfig tar:bzip2
USE_QT5=	core gui widgets \
		buildtools_build linguisttools_build qmake_build
USE_LDCONFIG=	yes

OPTIONS_SUB=	yes

OPTIONS_MULTI=	PLUGINS
OPTIONS_MULTI_PLUGINS=	FFAP MPG123 SRCONV XMP
OPTIONS_DEFAULT=	FFAP MPG123 XMP

FFAP_DESC=		Support APE sound file
FFAP_LIB_DEPENDS=	libtag.so:audio/taglib
FFAP_CMAKE_BOOL=	USE_FFAP
OPTIONS_DEFINE_i386=	FFAPASM
OPTIONS_DEFAULT_i386=	FFAPASM
OPTIONS_DEFINE_amd64=	FFAPASM
OPTIONS_DEFAULT_amd64=	FFAPASM
FFAPASM_DESC=	Optimize FFap decoder using devel/yasm
FFAPASM_BUILD_DEPENDS=	yasm:devel/yasm
FFAPASM_CMAKE_BOOL=	USE_ASM

MPG123_LIB_DEPENDS=	libmpg123.so:audio/mpg123 \
		libtag.so:audio/taglib
MPG123_CMAKE_BOOL=	USE_MPG123

SRCONV_DESC=	Support the sample rate converter
SRCONV_LIB_DEPENDS=	libsamplerate.so:audio/libsamplerate
SRCONV_CMAKE_BOOL=	USE_SRC

XMP_DESC=		Support various module formats using libxmp
XMP_LIB_DEPENDS=	libxmp.so:audio/libxmp
XMP_CMAKE_BOOL=	USE_XMP

pre-configure:
	@${RM} -f ${BUILD_WRKSRC}/CMakeCache.txt

.include <bsd.port.mk>
