---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901912"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Hosting: Host ogólny ogranicza iniekcji konstruktora uruchamiania

Jedynymi typami obsługiwanymi `Startup` przez hosta `IHostEnvironment` `IWebHostEnvironment`ogólnego `IConfiguration`dla iniekcji konstruktora klas są , i . Aplikacje `WebHost` korzystające z aplikacji pozostają nienaruszone.

#### <a name="change-description"></a>Zmień opis

Przed ASP.NET Core 3.0, iniekcji konstruktora może służyć do dowolnego typu w konstruktorze `Startup` klasy. W ASP.NET Core 3.0 stos sieci web został ponownie zapośrednictwem biblioteki hosta ogólnego. Możesz zobaczyć zmianę w *pliku Program.cs* szablonów:

**ASP.NET Core 2.x:**

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Core 3.0:**

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host`używa jednego kontenera iniekcji zależności (DI) do tworzenia aplikacji. `WebHost`używa dwóch kontenerów: jednego dla hosta i jednego dla aplikacji. W rezultacie `Startup` konstruktor nie obsługuje już niestandardowego iniekcji usługi. Tylko `IHostEnvironment` `IWebHostEnvironment`, `IConfiguration` i może być wstrzykiwany. Ta zmiana zapobiega problemom DI, takim jak zduplikowane tworzenie usługi singleton.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana jest konsekwencją ponownego platformowania stosu sieci web na biblioteki hosta ogólne.

#### <a name="recommended-action"></a>Zalecana akcja

Wstrzyknąć usługi do podpisu `Startup.Configure` metody. Przykład:

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
