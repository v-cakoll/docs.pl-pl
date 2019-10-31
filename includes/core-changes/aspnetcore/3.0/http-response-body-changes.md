---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198526"
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
