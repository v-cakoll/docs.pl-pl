---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290756"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP: Usunięto rozszerzalność domyślnego elementu HttpContext

W ramach ASP.NET core 3.0 poprawy wydajności, rozszerzalność została usunięta. `DefaultHttpContext` Klasa jest `sealed`teraz . Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).

Jeśli testy jednostkowe `Mock<HttpContext>` `new DefaultHttpContext()` używają `Mock<DefaultHttpContext>`, użyj lub zamiast tego.

Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Klasy mogą pochodzić z `DefaultHttpContext`.

#### <a name="new-behavior"></a>Nowe zachowanie

Klasy nie mogą pochodzić z `DefaultHttpContext`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Rozszerzalność została początkowo dostarczona, aby umożliwić łączenie `HttpContext`, ale wprowadziła niepotrzebną złożoność i utrudniła inne optymalizacje.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli używasz `Mock<DefaultHttpContext>` w testach jednostkowych, `Mock<HttpContext>` zacznij używać zamiast tego.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
