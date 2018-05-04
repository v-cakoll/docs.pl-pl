---
title: Biblioteki dodatkowe klasy i interfejsy API
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bdba02feb8cacc6ab1886c12f88716184aa2a81a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="additional-class-libraries-and-apis"></a>Biblioteki dodatkowe klasy i interfejsy API

Stale ewoluuje programu .NET Framework i wydania w celu ulepszania wiele platform lub wprowadzenie nowych funkcji wcześniej dla naszych klientów, nowych funkcji poza pasmem (OOB). Ten temat zawiera listę projektów OOB, które firma Microsoft udostępnia w dokumentacji.  
  
Ponadto niektóre biblioteki docelowych określonych platform lub implementacji programu .NET Framework. Na przykład <xref:System.Text.CodePagesEncodingProvider> klasy udostępnia kodowania strony kodu do aplikacji platformy uniwersalnej systemu Windows opracowana za pomocą programu .NET Framework. W tym temacie wymieniono także tych bibliotek.  
  
## <a name="oob-projects"></a>Projekty OOB
  
| Projekt | Opis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Zawiera kolekcje, które są wątkowo bezpieczne i zagwarantowanie odpowiednich nigdy nie ulegną zmianie ich zawartość. |
| <xref:System.Net.Http.WinHttpHandler> | Udostępnia program obsługi komunikatów dla <xref:System.Net.Http.HttpClient> oparte na interfejsie WinHTTP systemu Windows. |
| [System.Numerics.Vectors](https://msdn.microsoft.com/library/mt452176.aspx) | Udostępnia bibliotekę typów wektora, które można wykorzystać SIMD przyspieszanie sprzętowe.| 
| <xref:System.Threading.Tasks.Dataflow> | Biblioteka przepływu danych tpl zawiera składniki przepływu danych, aby zwiększyć niezawodność aplikacji z obsługą współbieżności. |  

## <a name="platform-specific-libraries"></a>Biblioteki specyficzne dla platformy
  
| Projekt | Opis |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Rozszerza <xref:System.Text.EncodingProvider> klasy, aby udostępnić kodowania strony kodu aplikacji przeznaczonych dla platformy uniwersalnej systemu Windows. |  
  
## <a name="private-apis"></a>Interfejsy API prywatnych  

Te interfejsy API obsługuje infrastrukturę programu produktu i nie są/obsługiwane przeznaczonych do użycia bezpośrednio w kodzie.  
  
| Nazwa interfejsu API |
| -------- |
| [System.Net.Connection Class](../../../docs/framework/additional-apis/connection.md) |
| [System.Net.Connection.m\_WriteList Field](../../../docs/framework/additional-apis/m_writelist.md) |
| [System.Net.ConnectionGroup Class](../../../docs/framework/additional-apis/connectiongroup.md) |
| [System.Net.ConnectionGroup.m\_ConnectionList Field](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [System.Net.CoreResponseData Class](../../../docs/framework/additional-apis/coreresponsedata.md) |
| [System.Net.CoreResponseData.m\_ResponseHeaders Field](../../../docs/framework/additional-apis/coreresponsedata_m_responseheaders.md) |
| [System.Net.CoreResponseData.m\_StatusCode Field](../../../docs/framework/additional-apis/coreresponsedata_m_statuscode.md) |
| [System.Net.HttpWebRequest.\_AutoRedirects Field](../../../docs/framework/additional-apis/_autoredirects.md) |
| [System.Net.HttpWebRequest.\_CoreResponse Field](../../../docs/framework/additional-apis/httpwebrequest__coreresponse.md) |
| [System.Net.HttpWebRequest.\_HttpResponse Field](../../../docs/framework/additional-apis/_httpresponse.md) |
| [System.Net.ServicePoint.m\_ConnectionGroupList Field](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [System.Net.ServicePointManager.s\_ServicePointTable Field](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [System.Windows.Forms.Design.DataMemberFieldEditor Class](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [System.Windows.Forms.Design.DataMemberListEditor Class](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>Zobacz także

[Program .NET Framework i wydania poza harmonogramem (OOB)](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
