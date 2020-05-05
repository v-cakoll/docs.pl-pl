---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901584"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP: synchroniczna operacja we/wy wyłączona na wszystkich serwerach

Począwszy od ASP.NET Core 3,0, operacje serwera synchronicznego są domyślnie wyłączone.

#### <a name="change-description"></a>Zmień opis

`AllowSynchronousIO`jest opcją na każdym serwerze, który włącza lub wyłącza synchroniczne interfejsy API we `HttpRequest.Body.Read`/ `HttpResponse.Body.Write`wy, `Stream.Flush`takie jak, i. Te interfejsy API były źródłem zawieszania wątków i zawieszenia aplikacji. Począwszy od ASP.NET Core 3,0 wersji zapoznawczej 3, te operacje synchroniczne są domyślnie wyłączone.

Narażone serwery:

- Kestrel
- HttpSys
- Usługi IIS w procesie
- TestServer

Oczekiwane błędy są podobne do:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

Każdy serwer ma `AllowSynchronousIO` opcję, która steruje tym zachowaniem i domyślnie dla wszystkich z nich jest `false`teraz.

Zachowanie może być również zastąpione dla każdego żądania jako tymczasowe środki zaradcze. Przykład:

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

Jeśli masz problemy z `TextWriter` lub innym strumieniem wywołującym synchroniczny interfejs API `Dispose`w programie, wywołaj zamiast niego nowy `DisposeAsync` interfejs API.

Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 7644](https://github.com/dotnet/aspnetcore/issues/7644).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`HttpRequest.Body.Read`, `HttpResponse.Body.Write`i `Stream.Flush` były domyślnie dozwolone.

#### <a name="new-behavior"></a>Nowe zachowanie

Te synchroniczne interfejsy API są domyślnie niedozwolone:

Oczekiwane błędy są podobne do:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a>Przyczyna zmiany

Te synchroniczne interfejsy API były źródłem przetrzymania wątku i zawieszenia aplikacji. Począwszy od ASP.NET Core 3,0 wersja zapoznawcza 3 operacje synchroniczne są domyślnie wyłączone.

#### <a name="recommended-action"></a>Zalecana akcja

Używaj asynchronicznych wersji metod. Zachowanie może być również zastąpione dla każdego żądania jako tymczasowe środki zaradcze.

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
