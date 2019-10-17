---
ms.openlocfilehash: be9a79f6ead3e72d7ffaade758704f0c1e2477f0
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394309"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a><span data-ttu-id="74e85-101">Hosting: Host ogólny ogranicza iniekcję konstruktora startowego</span><span class="sxs-lookup"><span data-stu-id="74e85-101">Hosting: Generic host restricts Startup constructor injection</span></span>

<span data-ttu-id="74e85-102">Jedyne Typy obsługiwane przez hosta generycznego dla iniekcji konstruktora klasy `Startup` są `IHostEnvironment`, `IWebHostEnvironment` i `IConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="74e85-102">The only types the generic host supports for `Startup` class constructor injection are `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration`.</span></span> <span data-ttu-id="74e85-103">Aplikacje korzystające z `WebHost` pozostają bez zmian.</span><span class="sxs-lookup"><span data-stu-id="74e85-103">Apps using `WebHost` are unaffected.</span></span>

#### <a name="change-description"></a><span data-ttu-id="74e85-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="74e85-104">Change description</span></span>

<span data-ttu-id="74e85-105">Przed ASP.NET Core 3,0, iniekcja konstruktora może zostać użyta dla dowolnego typu w konstruktorze klasy `Startup`.</span><span class="sxs-lookup"><span data-stu-id="74e85-105">Prior to ASP.NET Core 3.0, constructor injection could be used for arbitrary types in the `Startup` class's constructor.</span></span> <span data-ttu-id="74e85-106">W ASP.NET Core 3,0 stos sieci Web został przeładowany do biblioteki ogólnego hosta.</span><span class="sxs-lookup"><span data-stu-id="74e85-106">In ASP.NET Core 3.0, the web stack was replatformed onto the generic host library.</span></span> <span data-ttu-id="74e85-107">W pliku *program.cs* szablonów można zobaczyć zmianę:</span><span class="sxs-lookup"><span data-stu-id="74e85-107">You can see the change in the *Program.cs* file of the templates:</span></span>

<span data-ttu-id="74e85-108">**ASP.NET Core 2. x:**</span><span class="sxs-lookup"><span data-stu-id="74e85-108">**ASP.NET Core 2.x:**</span></span>

<https://github.com/aspnet/AspNetCore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

<span data-ttu-id="74e85-109">**ASP.NET Core 3,0:**</span><span class="sxs-lookup"><span data-stu-id="74e85-109">**ASP.NET Core 3.0:**</span></span>

<https://github.com/aspnet/AspNetCore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

<span data-ttu-id="74e85-110">`Host` używa jednego kontenera iniekcji zależności (DI) do kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="74e85-110">`Host` uses one dependency injection (DI) container to build the app.</span></span> <span data-ttu-id="74e85-111">`WebHost` używa dwóch kontenerów: jeden dla hosta i jeden dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="74e85-111">`WebHost` uses two containers: one for the host and one for the app.</span></span> <span data-ttu-id="74e85-112">W efekcie Konstruktor `Startup` nie obsługuje już niestandardowego dodawania usług.</span><span class="sxs-lookup"><span data-stu-id="74e85-112">As a result, the `Startup` constructor no longer supports custom service injection.</span></span> <span data-ttu-id="74e85-113">Można wstrzyknąć tylko `IHostEnvironment`, `IWebHostEnvironment` i `IConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="74e85-113">Only `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration` can be injected.</span></span> <span data-ttu-id="74e85-114">Ta zmiana zapobiega występowaniu problemów, takich jak duplikowanie tworzenia pojedynczej usługi.</span><span class="sxs-lookup"><span data-stu-id="74e85-114">This change prevents DI issues such as the duplicate creation of a singleton service.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="74e85-115">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="74e85-115">Version introduced</span></span>

<span data-ttu-id="74e85-116">3.0</span><span class="sxs-lookup"><span data-stu-id="74e85-116">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="74e85-117">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="74e85-117">Reason for change</span></span>

<span data-ttu-id="74e85-118">Ta zmiana jest konsekwencją zmiany platformy stosu sieci Web na ogólną bibliotekę hostów.</span><span class="sxs-lookup"><span data-stu-id="74e85-118">This change is a consequence of replatforming the web stack onto the generic host library.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="74e85-119">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="74e85-119">Recommended action</span></span>

<span data-ttu-id="74e85-120">Wsuń usługi do sygnatury metody `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="74e85-120">Inject services into the `Startup.Configure` method signature.</span></span> <span data-ttu-id="74e85-121">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="74e85-121">For example:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a><span data-ttu-id="74e85-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="74e85-122">Category</span></span>

<span data-ttu-id="74e85-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="74e85-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="74e85-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="74e85-124">Affected APIs</span></span>

<span data-ttu-id="74e85-125">Brak</span><span class="sxs-lookup"><span data-stu-id="74e85-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
