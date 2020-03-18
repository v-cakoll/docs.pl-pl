---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901912"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a><span data-ttu-id="7fdf9-101">Hosting: Host ogólny ogranicza iniekcji konstruktora uruchamiania</span><span class="sxs-lookup"><span data-stu-id="7fdf9-101">Hosting: Generic host restricts Startup constructor injection</span></span>

<span data-ttu-id="7fdf9-102">Jedynymi typami obsługiwanymi `Startup` przez hosta `IHostEnvironment` `IWebHostEnvironment`ogólnego `IConfiguration`dla iniekcji konstruktora klas są , i .</span><span class="sxs-lookup"><span data-stu-id="7fdf9-102">The only types the generic host supports for `Startup` class constructor injection are `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration`.</span></span> <span data-ttu-id="7fdf9-103">Aplikacje `WebHost` korzystające z aplikacji pozostają nienaruszone.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-103">Apps using `WebHost` are unaffected.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7fdf9-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="7fdf9-104">Change description</span></span>

<span data-ttu-id="7fdf9-105">Przed ASP.NET Core 3.0, iniekcji konstruktora może służyć do dowolnego typu w konstruktorze `Startup` klasy.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-105">Prior to ASP.NET Core 3.0, constructor injection could be used for arbitrary types in the `Startup` class's constructor.</span></span> <span data-ttu-id="7fdf9-106">W ASP.NET Core 3.0 stos sieci web został ponownie zapośrednictwem biblioteki hosta ogólnego.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-106">In ASP.NET Core 3.0, the web stack was replatformed onto the generic host library.</span></span> <span data-ttu-id="7fdf9-107">Możesz zobaczyć zmianę w *pliku Program.cs* szablonów:</span><span class="sxs-lookup"><span data-stu-id="7fdf9-107">You can see the change in the *Program.cs* file of the templates:</span></span>

<span data-ttu-id="7fdf9-108">**ASP.NET Core 2.x:**</span><span class="sxs-lookup"><span data-stu-id="7fdf9-108">**ASP.NET Core 2.x:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

<span data-ttu-id="7fdf9-109">**ASP.NET Core 3.0:**</span><span class="sxs-lookup"><span data-stu-id="7fdf9-109">**ASP.NET Core 3.0:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

<span data-ttu-id="7fdf9-110">`Host`używa jednego kontenera iniekcji zależności (DI) do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-110">`Host` uses one dependency injection (DI) container to build the app.</span></span> <span data-ttu-id="7fdf9-111">`WebHost`używa dwóch kontenerów: jednego dla hosta i jednego dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-111">`WebHost` uses two containers: one for the host and one for the app.</span></span> <span data-ttu-id="7fdf9-112">W rezultacie `Startup` konstruktor nie obsługuje już niestandardowego iniekcji usługi.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-112">As a result, the `Startup` constructor no longer supports custom service injection.</span></span> <span data-ttu-id="7fdf9-113">Tylko `IHostEnvironment` `IWebHostEnvironment`, `IConfiguration` i może być wstrzykiwany.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-113">Only `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration` can be injected.</span></span> <span data-ttu-id="7fdf9-114">Ta zmiana zapobiega problemom DI, takim jak zduplikowane tworzenie usługi singleton.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-114">This change prevents DI issues such as the duplicate creation of a singleton service.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7fdf9-115">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="7fdf9-115">Version introduced</span></span>

<span data-ttu-id="7fdf9-116">3.0</span><span class="sxs-lookup"><span data-stu-id="7fdf9-116">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7fdf9-117">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="7fdf9-117">Reason for change</span></span>

<span data-ttu-id="7fdf9-118">Ta zmiana jest konsekwencją ponownego platformowania stosu sieci web na biblioteki hosta ogólne.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-118">This change is a consequence of replatforming the web stack onto the generic host library.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7fdf9-119">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="7fdf9-119">Recommended action</span></span>

<span data-ttu-id="7fdf9-120">Wstrzyknąć usługi do podpisu `Startup.Configure` metody.</span><span class="sxs-lookup"><span data-stu-id="7fdf9-120">Inject services into the `Startup.Configure` method signature.</span></span> <span data-ttu-id="7fdf9-121">Przykład:</span><span class="sxs-lookup"><span data-stu-id="7fdf9-121">For example:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a><span data-ttu-id="7fdf9-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="7fdf9-122">Category</span></span>

<span data-ttu-id="7fdf9-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7fdf9-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7fdf9-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7fdf9-124">Affected APIs</span></span>

<span data-ttu-id="7fdf9-125">Brak</span><span class="sxs-lookup"><span data-stu-id="7fdf9-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
