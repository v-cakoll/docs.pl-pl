---
ms.openlocfilehash: d587e542a72d584502ac3ac892619cc38b88ef77
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620146"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>HttpUtility. JavaScriptStringEncode — ucieczki

#### <a name="details"></a>Szczegóły

Począwszy od .NET Framework 4,5, <xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> wyprowadza znak handlowego "i" ( &amp; ).

#### <a name="suggestion"></a>Sugestia

Jeśli aplikacja zależy od poprzedniego zachowania tej metody, można dodać ustawienie ASPNET: JavaScriptDoNotEncodeAmpersand do [elementu appSettings ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120)) w pliku konfiguracji.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Mały|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
