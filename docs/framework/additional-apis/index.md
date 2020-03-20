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
ms.openlocfilehash: abf7fd20988ebaaaf1a40ccc168c636fd0dacc1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155911"
---
# <a name="additional-class-libraries-and-apis"></a>Dodatkowe biblioteki klas i interfejsy API

.NET Framework stale ewoluuje. Aby poprawić rozwój między platformami i wprowadzić nowe funkcje wcześnie, nowe funkcje są wydawane poza pasmem (OOB). W tym temacie wymieniono projekty OOB, dla których dostarczamy dokumentację.  
  
Ponadto niektóre biblioteki są przeznaczone dla określonych platform lub implementacji programu .NET Framework. Na przykład <xref:System.Text.CodePagesEncodingProvider> klasa udostępnia kodowanie stron kodowych aplikacjom platformy uniwersalnej systemu Windows opracowanym przy użyciu programu .NET Framework. W tym temacie wymieniono również te biblioteki.  
  
## <a name="oob-projects"></a>Projekty OOB
  
| Project | Opis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Udostępnia kolekcje, które są bezpieczne dla wątków i gwarantuje, że nigdy nie zmienią ich zawartości. |
| <xref:System.Net.Http.WinHttpHandler> | Udostępnia program obsługi <xref:System.Net.Http.HttpClient> wiadomości oparty na interfejsie WinHTTP systemu Windows. |
| <xref:System.Numerics> | Udostępnia bibliotekę typów wektorów, które mogą korzystać z przyspieszania sprzętowego simd.|
| <xref:System.Threading.Tasks.Dataflow> | Biblioteka przepływ danych TPL udostępnia składniki przepływu danych, aby zwiększyć niezawodność aplikacji obsługujących współbieżność. |  

## <a name="platform-specific-libraries"></a>Biblioteki specyficzne dla platformy
  
| Project | Opis |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Rozszerza klasę, <xref:System.Text.EncodingProvider> aby kodowanie stron kodowych było dostępne dla aplikacji docelowych na platformie uniwersalnej systemu Windows. |  
  
## <a name="private-apis"></a>Prywatne interfejsy API  

Te interfejsy API obsługują infrastrukturę produktu i nie są przeznaczone/obsługiwane do użycia bezpośrednio z kodu.  
  
* [Właściwość Microsoft.SqlServer.Server.SmiOrderProperty.Item](microsoft.sqlserver.server.smiorderproperty.item.md)
* [Metoda system.exception.prepForRemoting](system.exception.prepforremoting.md)
* [Właściwość System.Data.SqlTypes.SqlChars.Stream](system.data.sqltypes.sqlchars.stream.md)
* [System.Data.SqlTypes.SqlStreamChars Konstruktor](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [Właściwość System.Data.SqlTypes.SqlStreamChars.CanSeek](system.data.sqltypes.sqlstreamchars.canseek.md)
* [Właściwość System.Data.SqlTypes.SqlStreamChars.IsNull](system.data.sqltypes.sqlstreamchars.isnull.md)
* [Właściwość System.Data.SqlTypes.SqlStreamChars.Length](system.data.sqltypes.sqlstreamchars.length.md)
* [Metoda System.Data.SqlTypes.SqlStreamChars.Close](system.data.sqltypes.sqlstreamchars.close.md)
* [Metoda System.Data.SqlTypes.SqlStreamChars.Dispose](system.data.sqltypes.sqlstreamchars.dispose.md)
* [Metoda system.data.sqltypes.sqlstreamchars.flush](system.data.sqltypes.sqlstreamchars.flush.md)
* [Metoda System.Data.SqlTypes.SqlStreamChars.Read](system.data.sqltypes.sqlstreamchars.read.md)
* [Metoda System.Data.SqlTypes.SqlStreamChars.Seek](system.data.sqltypes.sqlstreamchars.seek.md)
* [Metoda System.Data.SqlTypes.SqlStreamChars.SetLength](system.data.sqltypes.sqlstreamchars.setlength.md)
* [Metoda System.Data.SqlTypes.SqlStreamChars.Write](system.data.sqltypes.sqlstreamchars.write.md)
* [Metoda System.IO.MemoryStream.InternalGetOriginAndLength](system.io.memorystream.internalgetoriginandlength.md)
* [Klasa połączenia system.net.connection](connection.md)
* [Pole Lista zapisów\_system.net.connection.m](m_writelist.md)
* [Klasa Grupy System.Net.ConnectionGroup](connectiongroup.md)
* [Pole Lista połączeń system.Net.ConnectionGroup.m\_](m_connectionlist.md)
* [Właściwość System.Net.ConnectStream.Connection](system.net.connectstream.connection.md)
* [Klasa System.Net.CoreResponseData](coreresponsedata.md)
* [Pole Odpowiedzi System.Net.CoreResponseData.m\_](coreresponsedata_m_responseheaders.md)
* [Pole Kod stanu System.Net.CoreResponseData.m\_](coreresponsedata_m_statuscode.md)
* [System.net.httpWebRequest. \_Pole Autoredirects](_autoredirects.md)
* [System.net.httpWebRequest. \_Pole CoreResponse](httpwebrequest__coreresponse.md)
* [System.net.httpWebRequest. \_Pole httpResponse](_httpresponse.md)
* [Właściwość System.Net.PooledStream.NetworkStream](system.net.pooledstream.networkstream.md)
* [Klasa System.Net.RtcState](system.net.rtcstate.md)
* [Pole Lista połączeń system.Net.ServicePoint.m\_](m_connectiongrouplist.md)
* [Pole ServicePointTable w pliku\_System.Net.ServicePointManager.s](s_servicepointtable.md)
* [Pole system.net.TlsStream.m_Worker](system.net.tlsstream.m_worker.md)
* [Właściwość System.Net.Security.SslState.SslProtocol](system.net.security.sslstate.sslprotocol.md)
* [Metoda System.ServiceModel.Channels.Message.BodyToString](system.servicemodel.channels.message.bodytostring.md)
* [System.ServiceModel.Channels.Message.WriteStartHeaders Metoda](system.servicemodel.channels.message.writestartheaders.md)
* [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [Klasa System.Windows.Forms.Design.DataMemberFieldEditor](datamemberfieldeditor-class.md)
* [Klasa System.Windows.Forms.Design.DataMemberListEditor](datamemberlisteditor-class.md)
* [Metoda system.Xml.XmlReader.CreateSqlReader](system.xml.xmlreader.createsqlreader.md)
* [Adodb. Interfejs połączenia](adodb.connection.md)
* [Adodb. Wyliczenie eventreason](adodb.eventreasonenum.md)
* [Adodb. Wyliczenie Statusu Zdarzeń](adodb.eventstatusenum.md)
* [stdole. Struktura DISPPARAMS](stdole.dispparams.md)
* [stdole. Struktura EXCEPINFO](stdole.excepinfo.md)
* [stdole. IFont.Name właściwość](stdole.ifont.name.md)
* [stdole. Interfejs IFontDisp](stdole.ifontdisp.md)
* [stdole. Właściwość IPicture.Handle](stdole.ipicture.handle.md)
* [stdole. Właściwość IPictureDisp.Handle](stdole.ipicturedisp.handle.md)
* [stdole. Interfejs StdFont](stdole.stdfont.md)
* [stdole. Interfejs stdPicture](stdole.stdpicture.md)
  
## <a name="see-also"></a>Zobacz też

* [Program .NET Framework i wydania poza harmonogramem (OOB)](../get-started/the-net-framework-and-out-of-band-releases.md)
