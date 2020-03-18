---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901584"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP: Synchroniczne we/wy wyłączone na wszystkich serwerach

Począwszy od ASP.NET Core 3.0, synchroniczne operacje serwera są domyślnie wyłączone.

#### <a name="change-description"></a>Zmień opis

`AllowSynchronousIO`jest opcją na każdym serwerze, która włącza lub `HttpRequest.Body.Read`wyłącza `HttpResponse.Body.Write`synchroniczne interfejsy API We/Wy, takie jak , i `Stream.Flush`. Te interfejsy API od dawna źródłem głodu wątku i aplikacji zawiesza. Począwszy od ASP.NET Core 3.0 Preview 3, te operacje synchroniczne są domyślnie wyłączone.

Serwery, których dotyczy problem:

- Kestrel
- HttpSys (HttpSys)
- Przetwarzanie iIS
- Testserver

Spodziewaj się błędów podobnych do:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

Każdy serwer `AllowSynchronousIO` ma opcję, która kontroluje to zachowanie i `false`domyślnie dla wszystkich z nich jest teraz .

Zachowanie można również zastąpić na podstawie na żądanie jako tymczasowe środki zaradcze. Przykład:

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

Jeśli masz problemy `TextWriter` z lub innego strumienia wywołując `Dispose`synchroniczne `DisposeAsync` interfejsu API w , wywołać nowy interfejs API zamiast.

Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`HttpRequest.Body.Read`, `HttpResponse.Body.Write`i `Stream.Flush` były domyślnie dozwolone.

#### <a name="new-behavior"></a>Nowe zachowanie

Te synchroniczne interfejsy API są domyślnie niedozwolone:

Spodziewaj się błędów podobnych do:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a>Przyczyna zmiany

Te synchroniczne interfejsy API od dawna źródłem głodu wątków i aplikacji zawiesza. Począwszy od ASP.NET Core 3.0 Preview 3, operacje synchroniczne są domyślnie wyłączone.

#### <a name="recommended-action"></a>Zalecana akcja

Użyj asynchronicznych wersji metod. Zachowanie można również zastąpić na podstawie na żądanie jako tymczasowe środki zaradcze.

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
