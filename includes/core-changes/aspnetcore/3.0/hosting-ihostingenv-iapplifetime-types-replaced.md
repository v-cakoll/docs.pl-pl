---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394332"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a>Hosting: typy IHostingEnvironment i IApplicationLifetime oznaczone jako przestarzałe i zastąpione

Wprowadzono nowe typy do zastępowania istniejących typów `IHostingEnvironment` i `IApplicationLifetime`.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Istnieją dwa różne typy `IHostingEnvironment` i `IApplicationLifetime` z `Microsoft.Extensions.Hosting` i `Microsoft.AspNetCore.Hosting`.

#### <a name="new-behavior"></a>Nowe zachowanie

Stare typy zostały oznaczone jako przestarzałe i zastąpione nowymi typami.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Gdy `Microsoft.Extensions.Hosting` wprowadzono w ASP.NET Core 2,1, niektóre typy takie jak `IHostingEnvironment` i `IApplicationLifetime` zostały skopiowane z `Microsoft.AspNetCore.Hosting`. Niektóre zmiany w ASP.NET Core 3,0 powodują, że aplikacje zawierają zarówno przestrzenie nazw `Microsoft.Extensions.Hosting`, jak i `Microsoft.AspNetCore.Hosting`. Każde użycie tych zduplikowanych typów powoduje błąd kompilatora "niejednoznaczne odwołanie", gdy następuje odwołanie do obu przestrzeni nazw.

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

Nowe metody rozszerzenia `IHostEnvironment` `IsDevelopment` i `IsProduction` znajdują się w przestrzeni nazw `Microsoft.Extensions.Hosting`. Ta przestrzeń nazw może być konieczna do dodania do projektu.

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
