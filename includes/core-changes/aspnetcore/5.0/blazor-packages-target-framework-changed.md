---
ms.openlocfilehash: 17a167e5245914329195d61ab45ae2d8ecb617d6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416265"
---
### <a name="blazor-target-framework-of-nuget-packages-changed"></a>Blazor: zmieniono platformę docelową pakietów NuGet

Skompilowano projekty zestawu webBlazor 3,2 dla elementu docelowego .NET Standard 2,1 ( `<TargetFramework>netstandard2.1</TargetFramework>` ). W ASP.NET Core 5,0 zarówno projekty Blazor Server i Blazor webassembly są przeznaczone dla platformy .NET 5,0 ( `<TargetFramework>net5.0</TargetFramework>` ). Aby lepiej dostosować się do zmiany platformy docelowej, następujące pakiety Blazor nie są już docelowe .NET Standard 2,1:

* [Microsoft. AspNetCore. Components](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [Microsoft. AspNetCore. Components. Authorization](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [Microsoft. AspNetCore. Components. Forms](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [Microsoft. AspNetCore. Components. Web](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [Microsoft. AspNetCore. Components. webassembly](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [Microsoft. AspNetCore. Components. webassembly. Authentication](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [Microsoft.JSmiędzyoperacyjny](https://www.nuget.org/packages/Microsoft.JSInterop)
* [Microsoft.JSInterop. webassembly](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [Microsoft. Authentication. webassembly. Msal](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

Aby zapoznać się z omówieniem, zobacz sekcję dotyczącą usługi GitHub wydaj [/aspnetcore # 23424](https://github.com/dotnet/aspnetcore/issues/23424).

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 7

#### <a name="old-behavior"></a>Stare zachowanie

W Blazor 3,1 i 3,2 pakiety są przeznaczone dla .NET Standard 2,1 i .NET Core 3,1.

#### <a name="new-behavior"></a>Nowe zachowanie

W ASP.NET Core 5,0 pakiety są przeznaczone dla platformy .NET 5,0.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Wprowadzono zmiany w celu lepszego dostosowania z wymaganiami programu .NET Target Framework.

#### <a name="recommended-action"></a>Zalecana akcja

Projekty zestawu webassembly Blazor 3,2 powinny kierować platformą .NET 5,0 w ramach aktualizowania odwołań do pakietów do 5. x.x. Biblioteki odwołujące się do jednego z tych pakietów mogą wskazywać na platformę .NET 5,0 lub wiele obiektów docelowych w zależności od ich wymagań.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!--

#### Affected APIs

Not detectable via API analysis

-->
