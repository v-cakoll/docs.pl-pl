---
title: Dodatkowe biblioteki klas i interfejsy API
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 0aed6f32bbd3ffdc9446e9d17be2d90c62444ee1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053244"
---
# <a name="additional-class-libraries-and-apis"></a>Dodatkowe biblioteki klas i interfejsy API

.NET Framework ciągle się zmienia. Aby ulepszyć Programowanie dla wielu platform i wprowadzić nowe funkcje wczesne, nowe funkcje są uwalniane poza pasmem (OOB). W tym temacie wymieniono projekty OOB, dla których dostarczamy dokumentację.  
  
Ponadto niektóre biblioteki są przeznaczone dla określonych platform lub implementacji .NET Framework. Na przykład Klasa sprawia <xref:System.Text.CodePagesEncodingProvider> , że kodowanie strony kodowej jest dostępne dla aplikacji platformy UWP utworzonych przy użyciu .NET Framework. W tym temacie wymieniono również te biblioteki.  
  
## <a name="oob-projects"></a>Projekty OOB
  
| Projekt | Opis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Zapewnia kolekcje, które są bezpieczne dla wątków i gwarantują, że nigdy nie zmieniają ich zawartości. |
| <xref:System.Net.Http.WinHttpHandler> | Zapewnia obsługę komunikatów dla <xref:System.Net.Http.HttpClient> programu na podstawie interfejsu WinHTTP systemu Windows. |
| <xref:System.Numerics> | Udostępnia bibliotekę typów wektorów, które mogą korzystać z przyspieszania sprzętowego SIMD.| 
| <xref:System.Threading.Tasks.Dataflow> | Biblioteka TPL przepływu danych zawiera składniki przepływu danych, które ułatwiają zwiększenie niezawodności aplikacji z obsługą współbieżności. |  

## <a name="platform-specific-libraries"></a>Biblioteki charakterystyczne dla platformy
  
| Projekt | Opis |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <xref:System.Text.EncodingProvider> Rozszerza klasę, aby umożliwić dostęp do kodowania stron kodowych aplikacjom przeznaczonym dla platforma uniwersalna systemu Windows. |  
  
## <a name="private-apis"></a>Prywatne interfejsy API  

Te interfejsy API obsługują infrastrukturę produktu i nie są przeznaczone do użycia bezpośrednio w kodzie.  
  
| Nazwa interfejsu API |
| -------- |
| [System.Net.Connection Class](connection.md) |
| [System.Net.Connection.m\_WriteList Field](m_writelist.md) |
| [System.Net.ConnectionGroup Class](connectiongroup.md) |
| [System.Net.ConnectionGroup.m\_ConnectionList Field](m_connectionlist.md) |
| [System.Net.CoreResponseData Class](coreresponsedata.md) |
| [System.Net.CoreResponseData.m\_ResponseHeaders Field](coreresponsedata_m_responseheaders.md) |
| [System.Net.CoreResponseData.m\_StatusCode Field](coreresponsedata_m_statuscode.md) |
| [System.Net.HttpWebRequest.\_AutoRedirects Field](_autoredirects.md) |
| [System.Net.HttpWebRequest.\_CoreResponse Field](httpwebrequest__coreresponse.md) |
| [System.Net.HttpWebRequest.\_HttpResponse Field](_httpresponse.md) |
| [System.Net.ServicePoint.m\_ConnectionGroupList Field](m_connectiongrouplist.md) |
| [System.Net.ServicePointManager.s\_ServicePointTable Field](s_servicepointtable.md) |
| [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field](s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [System.Windows.Forms.Design.DataMemberFieldEditor Class](datamemberfieldeditor-class.md) |
| [System.Windows.Forms.Design.DataMemberListEditor Class](datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>Zobacz także

- [Program .NET Framework i wydania poza harmonogramem (OOB)](../get-started/the-net-framework-and-out-of-band-releases.md)
