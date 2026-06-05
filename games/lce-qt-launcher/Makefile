PORTNAME=			lce-qt-launcher
PORTVERSION=		0.0.21a0
PORTREVISION= 		0
CATEGORIES=			games python
PKGNAMEPREFIX=		${PYTHON_PKGNAMEPREFIX}

MAINTAINER=			xgui4-dev@example.com
COMMENT=			Custom Free/Libre Minecraft Legacy Console Launcher
WWW=				https://github.com/xgui4/LCE-Qt-Launcher/

LICENSE=			GPLv3
LICENSE_FILE=		${WRKSRC}/license.md

BUILD_DEPENDS=		${PYTHON_PKGNAMEPREFIX}hatchling>0:devel/py-hatchling@${PY_FLAVOR} \
					${PYTHON_PKGNAMEPREFIX}pyside6>0:devel/pyside6@${PY_FLAVOR} \
					${PYTHON_PKGNAMEPREFIX}pyside6-tools>0:devel/pyside6-tools@${PY_FLAVOR}

RUN_DEPENDS=		bash:shells/bash \
					git:devel/git \
					${PYTHON_PKGNAMEPREFIX}pyside6>0:devel/pyside6@${PY_FLAVOR} \
					${PYTHON_PKGNAMEPREFIX}rich>0:textproc/py-rich@${PY_FLAVOR} \
					${PYTHON_PKGNAMEPREFIX}vdf>0:devel/vdf@${PY_FLAVOR} \
					${PYTHON_PKGNAMEPREFIX}platformdirs>0:devel/py-platformdirs@${PY_FLAVOR}

USES=				python shebangfix desktop-file-utils shared-mime-info
USE_GITHUB=			yes
GH_ACCOUNT=			xgui4
GH_PROJECT=			LCE-Qt-Launcher
GH_TAGNAME=			32881041710ee0ab2604294dc93c433a944d4769

SHEBANG_FILES=		scripts/*.sh src/lce_qt_launcher/main.py src/lce_qt_launcher/managers/mod_manager.py src/lce_qt_launcher/managers/steam_manager.py

USE_PYTHON=			autoplist pep517
PEP517_WHEEL_NAME=  lce_qt_launcher-0.0.21a0

OPTIONS_DEFINE=		WINE STEAM DOCS
OPTIONS_DEFAULT=	DOCS # Keep blank if you want them off by default

WINE_DESC=			Enable Wine integration features
STEAM_DESC=			Enable Steam integration features
DOCS_DESC=  		Install App Documentation

WINE_RUN_DEPENDS=	wine:emulators/wine
STEAM_RUN_DEPENDS=	steam:games/steam-utils

PLIST_FILES=	etc/lce_qt_launcher.ini.sample \
		share/applications/io.github.xgui4.lce_qt_launcher.desktop \
		share/applications/lce-content-installer.desktop \
		share/mime/packages/io.github.xgui4.lce_qt_launcher.xml \
		share/icons/hicolor/128x128/apps/io.github.xgui4.lce_qt_launcher.png \
		share/icons/hicolor/128x128/mimetypes/application-x-lce_inst.png \
		share/icons/hicolor/128x128/apps/lce_content_installer.png

PORTDOCS=	code-of-conduct.md readme.md

post-install:
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/mime/packages
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/icons/hicolor/128x128/apps
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/icons/hicolor/128x128/mimetypes

	${INSTALL_DATA} ${WRKSRC}/data/lce_qt_launcher.ini \
		${STAGEDIR}${PREFIX}/etc/lce_qt_launcher.ini.sample

	${INSTALL_DATA} ${WRKSRC}/packages/io.github.xgui4.lce_qt_launcher.desktop \
		${STAGEDIR}${DESKTOPDIR}/io.github.xgui4.lce_qt_launcher.desktop

	${INSTALL_DATA} ${WRKSRC}/packages/lce-content-installer.desktop \
		${STAGEDIR}${DESKTOPDIR}/lce-content-installer.desktop

	${INSTALL_DATA} ${WRKSRC}/packages/lce_inst-mime.xml \
		${STAGEDIR}${PREFIX}/share/mime/packages/io.github.xgui4.lce_qt_launcher.xml

	${INSTALL_DATA} ${WRKSRC}/assets/io.github.xgui4.lce_qt_launcher.png \
		${STAGEDIR}${PREFIX}/share/icons/hicolor/128x128/apps/

	${INSTALL_DATA} ${WRKSRC}/assets/lce_content_installer.png \
		${STAGEDIR}${PREFIX}/share/icons/hicolor/128x128/apps/

	${INSTALL_DATA} ${WRKSRC}/assets/lce_inst.png \
		${STAGEDIR}${PREFIX}/share/icons/hicolor/128x128/mimetypes/application-x-lce_inst.png

post-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/readme.md ${STAGEDIR}${DOCSDIR}/
	${INSTALL_DATA} ${WRKSRC}/code-of-conduct.md ${STAGEDIR}${DOCSDIR}/

.include <bsd.port.mk>
