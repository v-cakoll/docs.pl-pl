---
title: Biblioteki dodatkowe klasy i interfejsy API
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3bb7a7c53cbca8bbd4026b46ce59589cef22382
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="additional-class-libraries-and-apis"></a>Biblioteki dodatkowe klasy i interfejsy API

Stale ewoluuje programu .NET Framework i wydania w celu ulepszania wiele platform lub wprowadzenie nowych funkcji wcześniej dla naszych klientów, nowych funkcji poza pasmem (OOB). Ten temat zawiera listę projektów OOB, które firma Microsoft udostępnia w dokumentacji.  
  
Ponadto niektóre biblioteki docelowych określonych platform lub implementacji programu .NET Framework. Na przykład <xref:System.Text.CodePagesEncodingProvider> klasy udostępnia kodowania strony kodu do aplikacji platformy uniwersalnej systemu Windows opracowana za pomocą programu .NET Framework. W tym temacie wymieniono także tych bibliotek.  
  
## <a name="oob-projects"></a>Projekty OOB
  
| Project | Opis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Zawiera kolekcje, które są wątkowo bezpieczne i zagwarantowanie odpowiednich nigdy nie ulegną zmianie ich zawartość. |
| <xref:System.Net.Http.WinHttpHandler> | Udostępnia program obsługi komunikatów dla <xref:System.Net.Http.HttpClient> oparte na interfejsie WinHTTP systemu Windows. |
| [System.Numerics.Vectors](https://msdn.microsoft.com/library/mt452176.aspx) | Udostępnia bibliotekę typów wektora, które można wykorzystać SIMD przyspieszanie sprzętowe.| 
| <xref:System.Threading.Tasks.Dataflow> | Biblioteka przepływu danych tpl zawiera składniki przepływu danych, aby zwiększyć niezawodność aplikacji z obsługą współbieżności. |  

## <a name="platform-specific-libraries"></a>Biblioteki specyficzne dla platformy
  
| Project | Opis |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Rozszerza <xref:System.Text.EncodingProvider> klasy, aby udostępnić kodowania strony kodu aplikacji przeznaczonych dla platformy uniwersalnej systemu Windows. |  
  
## <a name="private-apis"></a>Interfejsy API prywatnych  

Te interfejsy API obsługuje infrastrukturę programu produktu i nie są/obsługiwane przeznaczonych do użycia bezpośrednio w kodzie.  
  
| Nazwa interfejsu API |
| -------- |
| [Klasa System.Net.Connection](../../../docs/framework/additional-apis/connection.md) |
| [System.Net.Connection.m\_WriteList pola](../../../docs/framework/additional-apis/m_writelist.md) |
| [Klasa System.Net.ConnectionGroup](../../../docs/framework/additional-apis/connectiongroup.md) |
| [System.Net.ConnectionGroup.m\_ConnectionList pola](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [System.Net.HttpWebRequest. \_HttpResponse pola](../../../docs/framework/additional-apis/_httpresponse.md) |
| [System.Net.HttpWebRequest. \_AutoRedirects pola](../../../docs/framework/additional-apis/_autoredirects.md) |
| [System.Net.ServicePoint.m\_ConnectionGroupList pola](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [System.Net.ServicePointManager.s\_ServicePointTable pola](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes pola](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [Klasa System.Windows.Forms.Design.DataMemberFieldEditor](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [Klasa System.Windows.Forms.Design.DataMemberListEditor](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>Zobacz także

[.NET Framework i zwalnia poza pasmem](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
