---
title: Dodatkowe biblioteki klas i interfejsy API
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: 3a5134aa4407598e223fd2c938bfaac02cf9178c
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215526"
---
# <a name="additional-class-libraries-and-apis"></a>Dodatkowe biblioteki klas i interfejsy API

.NET Framework ciągle się zmienia. Aby ulepszyć Programowanie dla wielu platform i wprowadzić nowe funkcje wczesne, nowe funkcje są uwalniane poza pasmem (OOB). W tym temacie wymieniono projekty OOB, dla których dostarczamy dokumentację.  
  
Ponadto niektóre biblioteki są przeznaczone dla określonych platform lub implementacji .NET Framework. Na przykład Klasa <xref:System.Text.CodePagesEncodingProvider> udostępnia kodowanie stron kodowych dla aplikacji platformy UWP utworzonych przy użyciu .NET Framework. W tym temacie wymieniono również te biblioteki.  
  
## <a name="oob-projects"></a>Projekty OOB
  
| {1&gt;Projekt&lt;1} | Opis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Zapewnia kolekcje, które są bezpieczne dla wątków i gwarantują, że nigdy nie zmieniają ich zawartości. |
| <xref:System.Net.Http.WinHttpHandler> | Zapewnia obsługę komunikatów dla <xref:System.Net.Http.HttpClient> w oparciu o interfejs WinHTTP systemu Windows. |
| <xref:System.Numerics> | Udostępnia bibliotekę typów wektorów, które mogą korzystać z przyspieszania sprzętowego SIMD.| 
| <xref:System.Threading.Tasks.Dataflow> | Biblioteka TPL przepływu danych zawiera składniki przepływu danych, które ułatwiają zwiększenie niezawodności aplikacji z obsługą współbieżności. |  

## <a name="platform-specific-libraries"></a>Biblioteki charakterystyczne dla platformy
  
| {1&gt;Projekt&lt;1} | Opis |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Rozszerza klasę <xref:System.Text.EncodingProvider>, aby umożliwić dostęp do kodowania stron kodowych aplikacjom przeznaczonym dla platforma uniwersalna systemu Windows. |  
  
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
* [System .NET. Connection — Klasa](connection.md)
* [System .NET. Connection. m\_pole WriteList](m_writelist.md)
* [System .NET. Connection — Klasa](connectiongroup.md)
* [System .NET. Connections. m\_pole ConnectionList](m_connectionlist.md)
* [Właściwość system .NET. ConnectStream. Connection](system.net.connectstream.connection.md)
* [System .NET. CoreResponseData, Klasa](coreresponsedata.md)
* [Pole System .NET. CoreResponseData. m\_ResponseHeaders](coreresponsedata_m_responseheaders.md)
* [System .NET. CoreResponseData. m\_pole StatusCode](coreresponsedata_m_statuscode.md)
* [Pole System .NET. HttpWebRequest.\_autoredirects](_autoredirects.md)
* [Pole System .NET. HttpWebRequest.\_CoreResponse](httpwebrequest__coreresponse.md)
* [Pole System .NET. HttpWebRequest.\_HttpResponse](_httpresponse.md)
* [System .NET. PooledStream. NetworkStream — Właściwość](system.net.pooledstream.networkstream.md)
* [System .NET. RtcState, Klasa](system.net.rtcstate.md)
* [Pole System .NET. ServicePoint. m\_ConnectionGroupList](m_connectiongrouplist.md)
* [System .NET. ServicePointManager. s\_pole ServicePoint](s_servicepointtable.md)
* [Pole System .NET. TlsStream. m_Worker](system.net.tlsstream.m_worker.md)
* [System .NET. Security. SslState. SslProtocol — Właściwość](system.net.security.sslstate.sslprotocol.md)
* [System. ServiceModel. Channels. Message. BodyToString — Metoda](system.servicemodel.channels.message.bodytostring.md)
* [System. ServiceModel. Channels. Message. WriteStartHeaders — Metoda](system.servicemodel.channels.message.writestartheaders.md)
* [System. Windows. Diagnostics. VisualDiagnostics. s\_isDebuggerCheckDisabledForTestPurposes pole](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System. Windows. Forms. Design. DataMemberFieldEditor — Klasa](datamemberfieldeditor-class.md)
* [System. Windows. Forms. Design. Datamemberfieldeditor — Klasa](datamemberlisteditor-class.md)
* [System. XML. XmlReader. CreateSqlReader — Metoda](system.xml.xmlreader.createsqlreader.md)
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

* [Program .NET Framework i wydania poza harmonogramem (OOB)](../get-started/the-net-framework-and-out-of-band-releases.md)
