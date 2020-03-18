---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394332"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>Hosting: Typy IHostingEnvironment i IApplicationLifetime oznaczone jako przestarzałe i zastąpione

Wprowadzono nowe typy, aby `IHostingEnvironment` `IApplicationLifetime` zastąpić istniejące i typy.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Były dwa `IHostingEnvironment` różne `IApplicationLifetime` i `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting`typy z i .

#### <a name="new-behavior"></a>Nowe zachowanie

Stare typy zostały oznaczone jako przestarzałe i zastąpione nowymi typami.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Kiedy `Microsoft.Extensions.Hosting` został wprowadzony w ASP.NET Core 2.1, niektóre typy jak `IHostingEnvironment` i `IApplicationLifetime` zostały skopiowane z `Microsoft.AspNetCore.Hosting`. Niektóre zmiany ASP.NET Core 3.0 powodują, że aplikacje zawierają zarówno przestrzenie nazw, `Microsoft.Extensions.Hosting` jak i `Microsoft.AspNetCore.Hosting` przestrzenie nazw. Każde użycie tych typów duplikatów powoduje błąd kompilatora "niejednoznaczne odwołanie", gdy oba obszary nazw są przywoływani.

#### <a name="recommended-action"></a>Zalecana akcja

Zastąpiono wszystkie zastosowania starych typów nowo wprowadzonymi typami, jak poniżej:

**Przestarzałe typy (ostrzeżenie):**

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

**Nowe typy:**

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

Nowe `IHostEnvironment` `IsDevelopment` metody `IsProduction` i rozszerzenia znajdują `Microsoft.Extensions.Hosting` się w obszarze nazw. Ten obszar nazw może wymagać dodania do projektu.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.EnvironmentName`
- `T:Microsoft.AspNetCore.Hosting.IApplicationLifetime`
- `T:Microsoft.AspNetCore.Hosting.IHostingEnvironment`
- `T:Microsoft.Extensions.Hosting.EnvironmentName`
- `T:Microsoft.Extensions.Hosting.IApplicationLifetime`
- `T:Microsoft.Extensions.Hosting.IHostingEnvironment`

-->
