---
title: Dodatkowe biblioteki klas i interfejsy API
ms.date: 10/09/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: b869ca2f5e17db9a204a8b757b5e24ebb209d7c5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395662"
---
# <a name="additional-class-libraries-and-apis"></a>Dodatkowe biblioteki klas i interfejsy API

.NET Framework ciągle się zmienia. Aby ulepszyć Programowanie dla wielu platform i wprowadzić nowe funkcje wczesne, nowe funkcje są uwalniane poza pasmem (OOB). W tym temacie wymieniono projekty OOB, dla których dostarczamy dokumentację.  
  
Ponadto niektóre biblioteki są przeznaczone dla określonych platform lub implementacji .NET Framework. Na przykład Klasa <xref:System.Text.CodePagesEncodingProvider> sprawia, że kodowanie stron kodowych jest dostępne dla aplikacji platformy UWP utworzonych przy użyciu .NET Framework. W tym temacie wymieniono również te biblioteki.  
  
## <a name="oob-projects"></a>Projekty OOB
  
| Projekt | Opis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Zapewnia kolekcje, które są bezpieczne dla wątków i gwarantują, że nigdy nie zmieniają ich zawartości. |
| <xref:System.Net.Http.WinHttpHandler> | Zapewnia obsługę komunikatów dla <xref:System.Net.Http.HttpClient> w oparciu o interfejs WinHTTP systemu Windows. |
| <xref:System.Numerics> | Udostępnia bibliotekę typów wektorów, które mogą korzystać z przyspieszania sprzętowego SIMD.| 
| <xref:System.Threading.Tasks.Dataflow> | Biblioteka TPL przepływu danych zawiera składniki przepływu danych, które ułatwiają zwiększenie niezawodności aplikacji z obsługą współbieżności. |  

## <a name="platform-specific-libraries"></a>Biblioteki specyficzne dla platformy
  
| Projekt | Opis |  
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
* [System .NET. Connection — Klasa](connection.md)
* [System .NET. Connection. m @ no__t-1WriteList pole](m_writelist.md)
* [System .NET. Connection — Klasa](connectiongroup.md)
* [System .NET. Connections. m @ no__t-1ConnectionList Field](m_connectionlist.md)
* [System .NET. CoreResponseData, Klasa](coreresponsedata.md)
* [System .NET. CoreResponseData. m @ no__t-1ResponseHeaders pole](coreresponsedata_m_responseheaders.md)
* [System .NET. CoreResponseData. m @ no__t-1StatusCode pole](coreresponsedata_m_statuscode.md)
* [System .NET. HttpWebRequest. @no__t — pole 1AutoRedirects](_autoredirects.md)
* [System .NET. HttpWebRequest. @no__t — pole 1CoreResponse](httpwebrequest__coreresponse.md)
* [System .NET. HttpWebRequest. @no__t — pole 1HttpResponse](_httpresponse.md)
* [System .NET. ServicePoint. m @ no__t-1ConnectionGroupList pole](m_connectiongrouplist.md)
* [System .NET. ServicePointManager. s @ no__t-1ServicePointTable pole](s_servicepointtable.md)
* [System. Windows. Diagnostics. VisualDiagnostics. s @ no__t-1isDebuggerCheckDisabledForTestPurposes pole](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System. Windows. Forms. Design. DataMemberFieldEditor — Klasa](datamemberfieldeditor-class.md)
* [System. Windows. Forms. Design. Datamemberfieldeditor — Klasa](datamemberlisteditor-class.md)
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
  
## <a name="see-also"></a>Zobacz także

* [Program .NET Framework i wydania poza harmonogramem (OOB)](../get-started/the-net-framework-and-out-of-band-releases.md)
