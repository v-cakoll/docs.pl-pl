---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290756"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: Usunięto rozszerzalność DefaultHttpContext

W ramach ulepszeń wydajności ASP.NET Core 3,0, rozszerzalność `DefaultHttpContext` została usunięta. Klasa jest teraz `sealed`. Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504).

Jeśli jednostka testuje użycie `Mock<DefaultHttpContext>`, użyj `Mock<HttpContext>` lub `new DefaultHttpContext()` zamiast tego.

Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Klasy mogą pochodzić od `DefaultHttpContext`.

#### <a name="new-behavior"></a>Nowe zachowanie

Klasy nie mogą pochodzić `DefaultHttpContext`od.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Rozszerzalność podano początkowo w celu umożliwienia puli `HttpContext`, ale wprowadza niepotrzebną złożoność i utrudnia inne optymalizacje.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli używasz `Mock<DefaultHttpContext>` w testach jednostkowych, Zacznij używać `Mock<HttpContext>` zamiast tego.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
