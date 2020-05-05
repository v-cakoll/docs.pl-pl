---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901912"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Hosting: Host ogólny ogranicza iniekcję konstruktora startowego

Jedynym typem obsługiwanym przez hosta ogólnego dla `Startup` iniekcji konstruktora klasy `IHostEnvironment`są `IWebHostEnvironment`,, `IConfiguration`i. Aplikacje korzystające z programu `WebHost` pozostają bez zmian.

#### <a name="change-description"></a>Zmień opis

Przed ASP.NET Core 3,0, iniekcja konstruktora może zostać użyta dla dowolnego typu w `Startup` konstruktorze klasy. W ASP.NET Core 3,0 stos sieci Web został przeładowany do biblioteki ogólnego hosta. W pliku *program.cs* szablonów można zobaczyć zmianę:

**ASP.NET Core 2. x:**

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Core 3,0:**

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host`używa jednego kontenera iniekcji zależności (DI) do kompilowania aplikacji. `WebHost`używa dwóch kontenerów: jeden dla hosta i jeden dla aplikacji. W związku z tym `Startup` Konstruktor nie obsługuje już niestandardowego dodawania usług. Tylko `IHostEnvironment`, `IWebHostEnvironment`i `IConfiguration` można wstrzyknąć. Ta zmiana zapobiega występowaniu problemów, takich jak duplikowanie tworzenia pojedynczej usługi.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana jest konsekwencją zmiany platformy stosu sieci Web na ogólną bibliotekę hostów.

#### <a name="recommended-action"></a>Zalecana akcja

Wsuń usługi do sygnatury `Startup.Configure` metody. Przykład:

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
