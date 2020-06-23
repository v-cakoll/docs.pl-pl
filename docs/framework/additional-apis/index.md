---
title: Dodatkowe biblioteki klas i interfejsy API
description: Poznaj dodatkowe biblioteki klas i interfejsy API w programie .NET, w tym projekty poza pasmem (OOB), biblioteki specyficzne dla platformy i prywatne interfejsy API.
ms.date: 06/12/2020
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: 0b888d2f0e80685ba993682b2f3067cf8aee15bc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989739"
---
# <a name="additional-class-libraries-and-apis"></a>Dodatkowe biblioteki klas i interfejsy API

Ten artykuł zawiera listę .NET Framework interfejsów API, które zostały wydane poza pasmem, przeznaczone dla konkretnej platformy lub są typami prywatnymi lub wewnętrznymi.

## <a name="oob-projects"></a>Projekty OOB

Aby ulepszyć Programowanie dla wielu platform i wprowadzić nowe funkcje wczesne, niektóre .NET Framework funkcje zostały wydane poza pasmem (OOB).

| Project | Opis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Zapewnia kolekcje, które są bezpieczne dla wątków i gwarantują, że nigdy nie zmieniają ich zawartości. |
| <xref:System.Net.Http.WinHttpHandler> | Zapewnia obsługę komunikatów dla programu na <xref:System.Net.Http.HttpClient> podstawie interfejsu WinHTTP systemu Windows. |
| <xref:System.Numerics> | Udostępnia bibliotekę typów wektorów, które mogą korzystać z przyspieszania sprzętowego SIMD.|
| <xref:System.Threading.Tasks.Dataflow> | Biblioteka TPL przepływu danych zawiera składniki przepływu danych, które ułatwiają zwiększenie niezawodności aplikacji z obsługą współbieżności. |  

## <a name="platform-specific-libraries"></a>Biblioteki specyficzne dla platformy

Niektóre biblioteki są przeznaczone dla konkretnych platform. Na przykład <xref:System.Text.CodePagesEncodingProvider> Klasa udostępnia kodowanie stron kodowych dla aplikacji platformy UWP utworzonych przy użyciu .NET Framework.
  
| Project | Opis |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Rozszerza <xref:System.Text.EncodingProvider> klasę, aby umożliwić dostęp do kodowania stron kodowych aplikacjom przeznaczonym dla platforma uniwersalna systemu Windows. |  
  
## <a name="private-apis"></a>Prywatne interfejsy API  

Te interfejsy API obsługują infrastrukturę produktu i nie są przeznaczone do użycia bezpośrednio w kodzie.  
  
* [Microsoft. SqlServer. Server. SmiOrderProperty. Item — Właściwość](microsoft.sqlserver.server.smiorderproperty.item.md)
* [System. Exception. PrepForRemoting — Metoda](system.exception.prepforremoting.md)
* [System. Data. SqlTypes. SqlChars. Stream — Właściwość](system.data.sqltypes.sqlchars.stream.md)
* [System. Data. SqlTypes. SqlStreamChars — Konstruktor](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [Właściwość system. Data. SqlTypes. SqlStreamChars. CanSeek](system.data.sqltypes.sqlstreamchars.canseek.md)
* [Właściwość system. Data. SqlTypes. SqlStreamChars. IsNull](system.data.sqltypes.sqlstreamchars.isnull.md)
* [System. Data. SqlTypes. SqlStreamChars. Length — właściwość](system.data.sqltypes.sqlstreamchars.length.md)
* [System. Data. SqlTypes. SqlStreamChars. Close — Metoda](system.data.sqltypes.sqlstreamchars.close.md)
* [System. Data. SqlTypes. SqlStreamChars. Dispose — Metoda](system.data.sqltypes.sqlstreamchars.dispose.md)
* [System. Data. SqlTypes. SqlStreamChars. Flush — Metoda](system.data.sqltypes.sqlstreamchars.flush.md)
* [System. Data. SqlTypes. SqlStreamChars. Read — metoda](system.data.sqltypes.sqlstreamchars.read.md)
* [System. Data. SqlTypes. SqlStreamChars. Seek — metoda](system.data.sqltypes.sqlstreamchars.seek.md)
* [System. Data. SqlTypes. SqlStreamChars. SetLength — Metoda](system.data.sqltypes.sqlstreamchars.setlength.md)
* [System. Data. SqlTypes. SqlStreamChars. Write — Metoda](system.data.sqltypes.sqlstreamchars.write.md)
* [System. IO. elementu MemoryStream. InternalGetOriginAndLength — Metoda](system.io.memorystream.internalgetoriginandlength.md)
* [System .NET. ComNetOS, Klasa](system.net.comnetos.md)
* [System .NET. Connection — Klasa](connection.md)
* [Pole System .NET. Connection. m \_ WriteList](m_writelist.md)
* [System .NET. Connection — Klasa](connectiongroup.md)
* [Pole System .NET. Connections. m \_ ConnectionList](m_connectionlist.md)
* [Właściwość system .NET. ConnectStream. Connection](system.net.connectstream.connection.md)
* [System .NET. CoreResponseData, Klasa](coreresponsedata.md)
* [Pole System .NET. CoreResponseData. m \_ ResponseHeaders](coreresponsedata_m_responseheaders.md)
* [Pole StatusCode systemu .NET. CoreResponseData. m \_](coreresponsedata_m_statuscode.md)
* [System .NET. ExceptionHelper, Klasa](system.net.exceptionhelper.md)
* [System .NET. HttpStatusDescription, Klasa](system.net.httpstatusdescription.md)
* [System .NET. HttpWebRequest. \_ Pole autoredirect](_autoredirects.md)
* [System .NET. HttpWebRequest. \_ Pole CoreResponse](httpwebrequest__coreresponse.md)
* [System .NET. HttpWebRequest. \_ Pole HttpResponse](_httpresponse.md)
* [System .NET. Logging — Klasa](system.net.logging.md)
* [System .NET. mail. MailAddressParser — Klasa](system.net.mail.mailaddressparser.md)
* [System .NET. mail. QuotedPairReader — Klasa](system.net.mail.quotedpairreader.md)
* [System .NET. MIME. MailBnfHelper — Klasa](system.net.mime.mailbnfhelper.md)
* [System .NET. PooledStream. NetworkStream — Właściwość](system.net.pooledstream.networkstream.md)
* [System .NET. RtcState, Klasa](system.net.rtcstate.md)
* [System .NET. Security. SslState. SslProtocol — Właściwość](system.net.security.sslstate.sslprotocol.md)
* [Pole System .NET. ServicePoint. m \_ ConnectionGroupList](m_connectiongrouplist.md)
* [System .NET. ServicePointManager. CloseConnectionGroups — Metoda](system.net.servicepointmanager.closeconnectiongroups.md)
* [System .NET. ServicePointManager. s — \_ pole ServicePoint](s_servicepointtable.md)
* [Pole System .NET. TlsStream. m_Worker](system.net.tlsstream.m_worker.md)
* [System .NET. UnsafeNclNativeMethods, Klasa](system.net.unsafenclnativemethods.md)
* [System .NET. WebHeaderCollection. addinternal — Metoda](system.net.webheadercollection.addinternal.md)
* [System. ServiceModel. Channels. Message. BodyToString — Metoda](system.servicemodel.channels.message.bodytostring.md)
* [System. ServiceModel. Channels. Message. WriteStartHeaders — Metoda](system.servicemodel.channels.message.writestartheaders.md)
* [Pole System. Windows. Diagnostics. VisualDiagnostics. s \_ isDebuggerCheckDisabledForTestPurposes](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System. Windows. Forms. Design. DataMemberFieldEditor — Klasa](datamemberfieldeditor-class.md)
* [System. Windows. Forms. Design. Datamemberfieldeditor — Klasa](datamemberlisteditor-class.md)
* [System.Xml.XmlReader. CreateSqlReader — Metoda](system.xml.xmlreader.createsqlreader.md)
* [ADODB. Interfejs połączenia](adodb.connection.md)
* [ADODB. Wyliczenie EventReason](adodb.eventreasonenum.md)
* [ADODB. Wyliczenie obiektu EventStatus](adodb.eventstatusenum.md)
* [stdole. DISPPARAMS, struktura](stdole.dispparams.md)
* [stdole. EXCEPINFO, struktura](stdole.excepinfo.md)
* [stdole. Właściwość IFont.Name](stdole.ifont.name.md)
* [stdole. IFontDisp, interfejs](stdole.ifontdisp.md)
* [stdole. IPicture. Handle — właściwość](stdole.ipicture.handle.md)
* [stdole. IPictureDisp. Handle — właściwość](stdole.ipicturedisp.handle.md)
* [stdole. StdFont, interfejs](stdole.stdfont.md)
* [stdole. StdPicture, interfejs](stdole.stdpicture.md)
  
## <a name="see-also"></a>Zobacz też

* [.NET Framework i wersje poza pasmem](../get-started/the-net-framework-and-out-of-band-releases.md)
