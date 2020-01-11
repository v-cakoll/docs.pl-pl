---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901912"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Hosting: Host ogólny ogranicza iniekcję konstruktora startowego

Jedyne Typy obsługiwane przez hosta generycznego dla iniekcji konstruktora klasy `Startup` są `IHostEnvironment`, `IWebHostEnvironment`i `IConfiguration`. Aplikacje korzystające z `WebHost` nie podlegają usterce.

#### <a name="change-description"></a>Opis zmiany

Przed ASP.NET Core 3,0, iniekcja konstruktora może zostać użyta dla dowolnego typu w konstruktorze klasy `Startup`. W ASP.NET Core 3,0 stos sieci Web został przeładowany do biblioteki ogólnego hosta. W pliku *program.cs* szablonów można zobaczyć zmianę:

**ASP.NET Core 2. x:**

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Core 3,0:**

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host` używa jednego kontenera iniekcji zależności (DI) do kompilowania aplikacji. `WebHost` używa dwóch kontenerów: jeden dla hosta i jeden dla aplikacji. W efekcie Konstruktor `Startup` nie obsługuje już niestandardowego dodawania usług. Można wstrzyknąć tylko `IHostEnvironment`, `IWebHostEnvironment`i `IConfiguration`. Ta zmiana zapobiega występowaniu problemów, takich jak duplikowanie tworzenia pojedynczej usługi.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana jest konsekwencją zmiany platformy stosu sieci Web na ogólną bibliotekę hostów.

#### <a name="recommended-action"></a>Zalecane działanie

Wsuń usługi do sygnatury metody `Startup.Configure`. Na przykład:

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
