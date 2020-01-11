---
ms.openlocfilehash: 1b4b0aba3ea24682ae972bf283ac387692c83781
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901634"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: Usunięto rozszerzalność DefaultHttpContext

W ramach ulepszeń wydajności ASP.NET Core 3,0, rozszerzalność `DefaultHttpContext` została usunięta. Klasa jest teraz `sealed`. Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504).

Jeśli testy jednostkowe używają `Mock<DefaultHttpContext>`, użyj `Mock<HttpContext>` zamiast tego.

Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Klasy mogą pochodzić od `DefaultHttpContext`.

#### <a name="new-behavior"></a>Nowe zachowanie

Klasy nie mogą pochodzić od `DefaultHttpContext`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Rozszerzalność podano początkowo w celu umożliwienia puli `HttpContext`, ale wprowadza niepotrzebną złożoność i utrudnia inne optymalizacje.

#### <a name="recommended-action"></a>Zalecane działanie

Jeśli używasz `Mock<DefaultHttpContext>` w testach jednostkowych, Zacznij używać `Mock<HttpContext>` zamiast tego.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
