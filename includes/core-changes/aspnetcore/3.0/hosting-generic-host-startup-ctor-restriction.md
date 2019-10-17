---
ms.openlocfilehash: be9a79f6ead3e72d7ffaade758704f0c1e2477f0
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394309"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Hosting: Host ogólny ogranicza iniekcję konstruktora startowego

Jedyne Typy obsługiwane przez hosta generycznego dla iniekcji konstruktora klasy `Startup` są `IHostEnvironment`, `IWebHostEnvironment` i `IConfiguration`. Aplikacje korzystające z `WebHost` pozostają bez zmian.

#### <a name="change-description"></a>Zmień opis

Przed ASP.NET Core 3,0, iniekcja konstruktora może zostać użyta dla dowolnego typu w konstruktorze klasy `Startup`. W ASP.NET Core 3,0 stos sieci Web został przeładowany do biblioteki ogólnego hosta. W pliku *program.cs* szablonów można zobaczyć zmianę:

**ASP.NET Core 2. x:**

<https://github.com/aspnet/AspNetCore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Core 3,0:**

<https://github.com/aspnet/AspNetCore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host` używa jednego kontenera iniekcji zależności (DI) do kompilowania aplikacji. `WebHost` używa dwóch kontenerów: jeden dla hosta i jeden dla aplikacji. W efekcie Konstruktor `Startup` nie obsługuje już niestandardowego dodawania usług. Można wstrzyknąć tylko `IHostEnvironment`, `IWebHostEnvironment` i `IConfiguration`. Ta zmiana zapobiega występowaniu problemów, takich jak duplikowanie tworzenia pojedynczej usługi.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana jest konsekwencją zmiany platformy stosu sieci Web na ogólną bibliotekę hostów.

#### <a name="recommended-action"></a>Zalecana akcja

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
