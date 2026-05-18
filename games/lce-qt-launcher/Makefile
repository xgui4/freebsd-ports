PORTNAME=		lce-qt-launcher
DISTVERSION=	0.0.20.0-pre_alpha1
CATEGORIES=		games python

MAINTAINER=		xgui4-dev@example.com
COMMENT=		Custom Free/Libre Minecraft Legacy Console Launcher
WWW=			https://github.com/xgui4/LCE-Qt-Launcher/

LICENSE=		GPLv3
LICENSE_FILE=	${WRKSRC}/license.md

BUILD_DEPENDS=	bash:shells/bash \
		git:devel/git \
		${PYTHON_PKGNAMEPREFIX}hatchling>0:devel/py-hatchling@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}hatch>0:devel/py-hatch@${PY_FLAVOR}

RUN_DEPENDS=	bash:shells/bash \
				git:devel/git \
				${PYTHON_PKGNAMEPREFIX}pyside6>0:devel/pyside6@${PY_FLAVOR} \
				${PYTHON_PKGNAMEPREFIX}rich>0:devel/py-rich@${PY_FLAVOR} \
				${PYTHON_PKGNAMEPREFIX}vdf>0:devel/py-vdf@${PY_FLAVOR} \
				${PYTHON_PKGNAMEPREFIX}platformdirs>0:devel/py-platformdirs@${PY_FLAVOR}

USES=			python qt:6 shebangfix desktop-file-utils shared-mime-info
USE_GITHUB=		yes
GH_ACCOUNT=		xgui4
GH_PROJECT=		LCE-Qt-Launcher
GH_COMMITS=		dba4cdef4493a44027b998ef88f130078cf2208a

SHEBANG_FILES=	scripts/*.sh

USE_PYTHON=		autoplist pep517
USE_QT=			tools:build

OPTIONS_DEFINE=		WINE STEAM
OPTIONS_DEFAULT=	# Keep blank if you want them off by default

WINE_DESC=		Enable Wine integration features
STEAM_DESC=		Enable Steam integration features

WINE_RUN_DEPENDS=	wine:emulators/wine
STEAM_RUN_DEPENDS=	steam:games/steam-utils

install:
	@${MKDIR} ${STAGEDIR}${ETCDIR}
	@${MKDIR} ${STAGEDIR}${DESKTOPDIR}
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/mime/packages
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/metainfo
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/icons/hicolor/128x128/apps
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/icons/hicolor/128x128/mimetypes
	@${MKDIR} ${STAGEDIR}${DOCSDIR}

	${INSTALL_DATA} ${WRKSRC}/data/lce_qt_launcher.ini \
		${STAGEDIR}${PREFIX}/etc/lce_qt_launcher.ini.sample

	${INSTALL_DATA} ${WRKSRC}/packages/io.github.xgui4.lce_qt_launcher.desktop \
		${STAGEDIR}${DESKTOPDIR}/io.github.xgui4.lce_qt_launcher.desktop
	${INSTALL_DATA} ${WRKSRC}/packages/lce_inst-mime.xml \
		${STAGEDIR}${PREFIX}/share/mime/packages/io.github.xgui4.lce_qt_launcher.xml

	${INSTALL_DATA} ${WRKSRC}/packages/io.github.xgui4.lce_qt_launcher.metainfo.xml \
		${STAGEDIR}${PREFIX}/share/metainfo/
	${INSTALL_DATA} ${WRKSRC}/assets/io.github.xgui4.lce_qt_launcher.png \
		${STAGEDIR}${PREFIX}/share/icons/hicolor/128x128/apps/
	${INSTALL_DATA} ${WRKSRC}/assets/lce_inst.png \
		${STAGEDIR}${PREFIX}/share/icons/hicolor/128x128/mimetypes/application-x-lce_inst.png

	${INSTALL_DATA} ${WRKSRC}/readme.md ${WRKSRC}/code-of-conduct.md \
		${STAGEDIR}${DOCSDIR}/

.include <bsd.port.mk>
