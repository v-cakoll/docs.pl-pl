---
ms.openlocfilehash: c861d61cbbe8075db4b17a702e863336ea621f2b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198525"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP: synchroniczna operacja we/wy wyłączona na wszystkich serwerach

Począwszy od ASP.NET Core 3,0, operacje serwera synchronicznego są domyślnie wyłączone.

#### <a name="change-description"></a>Zmień opis

`AllowSynchronousIO` to opcja na każdym serwerze, która włącza lub wyłącza synchroniczne interfejsy API we/wy, takie jak `HttpRequest.Body.Read`, `HttpResponse.Body.Write` i `Stream.Flush`. Te interfejsy API były źródłem zawieszania wątków i zawieszenia aplikacji. Począwszy od ASP.NET Core 3,0 wersji zapoznawczej 3, te operacje synchroniczne są domyślnie wyłączone.

Narażone serwery:

- Kestrel
- HttpSys
- Usługi IIS w procesie
- TestServer

Oczekiwane błędy są podobne do:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

Każdy serwer ma opcję `AllowSynchronousIO`, która kontroluje to zachowanie, a wartość domyślna dla wszystkich z nich to teraz `false`.

Zachowanie może być również zastąpione dla każdego żądania jako tymczasowe środki zaradcze. Na przykład:

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

Jeśli masz problemy z `TextWriter` lub innym strumieniem wywołującym synchroniczny interfejs API w `Dispose`, wywołaj nowy interfejs API `DisposeAsync`.

W przypadku dyskusji zobacz [ASPNET/AspNetCore # 7644](https://github.com/aspnet/AspNetCore/issues/7644).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Domyślnie dozwolone są `HttpRequest.Body.Read`, `HttpResponse.Body.Write` i `Stream.Flush`.

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
