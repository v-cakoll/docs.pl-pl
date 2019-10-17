---
ms.openlocfilehash: 22ef5d0f91a4f61ca75203f677bcc14e91d77dc1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394324"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP: zmiany infrastruktury treści odpowiedzi

Infrastruktura do tworzenia kopii zapasowych treści odpowiedzi HTTP została zmieniona. Jeśli używasz bezpośrednio `HttpResponse`, nie musisz wprowadzać żadnych zmian w kodzie. Zapoznaj się z dodatkowymi opcjami, jeśli są zawijane lub zastępowane `HttpResponse.Body` lub do `HttpContext.Features`.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Z treścią odpowiedzi HTTP są skojarzone trzy interfejsy API:

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>Nowe zachowanie

Jeśli zastąpisz `HttpResponse.Body`, zastępuje cały `IHttpResponseBodyFeature` otoką wokół danego strumienia przy użyciu `StreamResponseBodyFeature`, aby zapewnić domyślne implementacje dla wszystkich oczekiwanych interfejsów API. Ustawienie Przywróć oryginalny strumień przywraca tę zmianę.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Motywacja polega na połączeniu interfejsów API treści odpowiedzi w jeden nowy interfejs funkcji.

#### <a name="recommended-action"></a>Zalecana akcja

Użyj `IHttpResponseBodyFeature`, w przypadku których poprzednio użyto `IHttpResponseFeature.Body`, `IHttpSendFileFeature` lub `IHttpBufferingFeature`.

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
