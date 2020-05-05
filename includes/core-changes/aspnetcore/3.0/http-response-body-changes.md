---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198526"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP: zmiany infrastruktury treści odpowiedzi

Infrastruktura do tworzenia kopii zapasowych treści odpowiedzi HTTP została zmieniona. Jeśli używasz `HttpResponse` bezpośrednio, nie musisz wprowadzać żadnych zmian w kodzie. Przeczytaj więcej w przypadku zawijania lub zamieniania `HttpResponse.Body` lub `HttpContext.Features`uzyskiwania dostępu do.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Z treścią odpowiedzi HTTP są skojarzone trzy interfejsy API:

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>Nowe zachowanie

Jeśli zastąpisz `HttpResponse.Body`, zastępuje cały `IHttpResponseBodyFeature` element otoką wokół danego strumienia przy użyciu `StreamResponseBodyFeature` , aby zapewnić domyślne implementacje dla wszystkich oczekiwanych interfejsów API. Ustawienie Przywróć oryginalny strumień przywraca tę zmianę.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Motywacja polega na połączeniu interfejsów API treści odpowiedzi w jeden nowy interfejs funkcji.

#### <a name="recommended-action"></a>Zalecana akcja

Użyj `IHttpResponseBodyFeature` tam, gdzie wcześniej `IHttpResponseFeature.Body`korzystano `IHttpSendFileFeature`z, `IHttpBufferingFeature`lub.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
