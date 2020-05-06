---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394332"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>Hosting: typy IHostingEnvironment i IApplicationLifetime oznaczone jako przestarzałe i zastąpione

Wprowadzono nowe typy do zastępowania istniejących `IHostingEnvironment` i `IApplicationLifetime` typów.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`IHostingEnvironment` Istnieją dwa różne `IApplicationLifetime` i typy z `Microsoft.Extensions.Hosting` i. `Microsoft.AspNetCore.Hosting`

#### <a name="new-behavior"></a>Nowe zachowanie

Stare typy zostały oznaczone jako przestarzałe i zastąpione nowymi typami.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Kiedy `Microsoft.Extensions.Hosting` został wprowadzony w ASP.NET Core 2,1, niektóre typy takie `IHostingEnvironment` jak `IApplicationLifetime` i zostały skopiowane z `Microsoft.AspNetCore.Hosting`. Niektóre zmiany w ASP.NET Core 3,0 powodują, `Microsoft.Extensions.Hosting` że aplikacje zawierają zarówno `Microsoft.AspNetCore.Hosting` przestrzeń nazw, jak i. Każde użycie tych zduplikowanych typów powoduje błąd kompilatora "niejednoznaczne odwołanie", gdy następuje odwołanie do obu przestrzeni nazw.

#### <a name="recommended-action"></a>Zalecana akcja

Zamieniono wszystkie użycia starych typów na nowo wprowadzone typy w następujący sposób:

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

Nowe `IHostEnvironment` `IsDevelopment` i `IsProduction` rozszerzenie metody znajdują się w `Microsoft.Extensions.Hosting` przestrzeni nazw. Ta przestrzeń nazw może być konieczna do dodania do projektu.

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
