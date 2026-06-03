PORTNAME=			flex-rs
DISTVERSION=		0.0.5
CATEGORIES=			misc
MASTER_SITES=		https://github.com/xgui4/flex

MAINTAINER=			xgui4-dev@example.com
COMMENT=			Modern, maintained replacement for ls
WWW=				https://eza.rocks/

LICENSE=			MIT
LICENSE_FILE=		${WRKSRC}/LICENSE.txt

USES=				cargo

USE_GITHUB=			yes
GH_ACCOUNT=			xgui4
GH_PROJECT=			flex
GH_TAGNAME= 		13f672ab561e4a4cdc85853527a0eebc4a36ce11

PLIST_FILES=		etc/lce_qt_launcher.ini.sample \
				share/applications/io.github.xgui4.lce_qt_launcher.desktop \
				share/mime/packages/io.github.xgui4.lce_qt_launcher.xml \
				share/metainfo/io.github.xgui4.lce_qt_launcher.metainfo.xml \
				share/icons/hicolor/128x128/apps/io.github.xgui4.lce_qt_launcher.png \
				share/icons/hicolor/128x128/mimetypes/application-x-lce_inst.png

PORTDOCS=			code-of-conduct.md readme.md

post-install:
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/metainfo
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/mime/packages
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/icons/hicolor/128x128/apps
	@${MKDIR} ${STAGEDIR}${PREFIX}/share/icons/hicolor/128x128/mimetypes

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

post-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/readme.md ${STAGEDIR}${DOCSDIR}/
	${INSTALL_DATA} ${WRKSRC}/code-of-conduct.md ${STAGEDIR}${DOCSDIR}/

.include <bsd.port.mk>