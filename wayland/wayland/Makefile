# Created by: kwm@FreeBSD.org
# $FreeBSD$

# NOTE
# Changes made by kwm to use kevent instead of epoll
# are still in place. However, since libinput depends
# on libepoll-shim the simplest to do was to have Wayland
# also use it. Currently build will fail if epoll-shim
# is not available but can be built without epoll-shim
# if EPOLLSHIM_LIBS is cleared (configure.ac)
#
# TODO: Add condition for this in configure
#
# If we want to build Wayland with kwm's kevent patches
# and use epoll-shim for libinput we have to change it
# so that Wayland ignore epoll headers installed by
# epoll-shim.
# Maybe best is to use epoll-shim if it is good enough
# and keep diff with upstream minimal.

PORTNAME=	wayland
PORTVERSION=	1.11.0
CATEGORIES=	wayland
MASTER_SITES= http://wayland.freedesktop.org/releases/

MAINTAINER=	x11@FreeBSD.org
COMMENT=	Wayland composite "server"

LIB_DEPENDS=	libexpat.so:${PORTSDIR}/textproc/expat2 \
				libffi.so:${PORTSDIR}/devel/libffi \
				libepoll-shim.so:${PORTSDIR}/wayland/libepoll-shim
WITH_DEBUG=	1
USES=		autoreconf gmake libtool pathfix pkgconfig tar:xz
USE_GNOME=	libxslt:build
USE_LDCONFIG=	yes
GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--disable-documentation
INSTALL_TARGET=	install-strip

CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib

.include <bsd.port.mk>
