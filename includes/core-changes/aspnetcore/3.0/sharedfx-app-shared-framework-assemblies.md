---
ms.openlocfilehash: 8344fdedcff34f102b73f977b688abc15563bd4c
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198534"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="59d07-101">Udostępnione środowisko: zestawy usunięte z Microsoft. AspNetCore. App</span><span class="sxs-lookup"><span data-stu-id="59d07-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="59d07-102">Począwszy od ASP.NET Core 3,0, ASP.NET Core Shared Framework (`Microsoft.AspNetCore.App`) zawiera tylko zestawy pierwszej firmy, które są w pełni opracowane, obsługiwane i obsługujące przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="59d07-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="59d07-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="59d07-103">Change description</span></span>

<span data-ttu-id="59d07-104">Należy zastanowić się nad zmianą podczas ponownego definiowania granic dla ASP.NET Core "platformy".</span><span class="sxs-lookup"><span data-stu-id="59d07-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="59d07-105">Udostępniona platforma będzie [budować Źródło przez każdy za pośrednictwem usługi GitHub](https://github.com/dotnet/source-build) i będzie w dalszym ciągu oferować istniejące zalety platformy .NET Core dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="59d07-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="59d07-106">Niektóre korzyści obejmują mniejszy rozmiar wdrożenia, scentralizowaną poprawkę i krótszy czas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="59d07-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="59d07-107">W ramach zmiany niektóre istotne zmiany są wprowadzane w `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="59d07-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="59d07-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="59d07-108">Version introduced</span></span>

<span data-ttu-id="59d07-109">3.0</span><span class="sxs-lookup"><span data-stu-id="59d07-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="59d07-110">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="59d07-110">Old behavior</span></span>

<span data-ttu-id="59d07-111">Projekty, do których odwołuje się `Microsoft.AspNetCore.App` za pośrednictwem elementu `<PackageReference>` w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="59d07-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="59d07-112">Ponadto `Microsoft.AspNetCore.App` zawiera następujące podskładniki:</span><span class="sxs-lookup"><span data-stu-id="59d07-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="59d07-113">Json.NET (`Newtonsoft.Json`)</span><span class="sxs-lookup"><span data-stu-id="59d07-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="59d07-114">Entity Framework Core (zestawy z prefiksem `Microsoft.EntityFrameworkCore.`)</span><span class="sxs-lookup"><span data-stu-id="59d07-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="59d07-115">Roslyn (`Microsoft.CodeAnalysis`)</span><span class="sxs-lookup"><span data-stu-id="59d07-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="59d07-116">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="59d07-116">New behavior</span></span>

<span data-ttu-id="59d07-117">Odwołanie do `Microsoft.AspNetCore.App` nie wymaga już elementu `<PackageReference>` w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="59d07-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="59d07-118">Zestaw .NET Core SDK obsługuje nowy element o nazwie `<FrameworkReference>`, który zastępuje użycie `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="59d07-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="59d07-119">Aby uzyskać więcej informacji, zobacz [ASPNET/AspNetCore # 3612](https://github.com/aspnet/AspNetCore/issues/3612).</span><span class="sxs-lookup"><span data-stu-id="59d07-119">For more information, see [aspnet/AspNetCore#3612](https://github.com/aspnet/AspNetCore/issues/3612).</span></span>

<span data-ttu-id="59d07-120">Entity Framework Core są dostarczane jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="59d07-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="59d07-121">Ta zmiana powoduje wyrównanie modelu wysyłki do wszystkich innych bibliotek dostępu do danych w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="59d07-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="59d07-122">Zapewnia Entity Framework Core najprostszą ścieżkę, aby kontynuować innowacje, jednocześnie obsługując różne platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="59d07-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="59d07-123">Przenoszenie Entity Framework Core z platformy udostępnionej nie ma wpływu na jego stan jako biblioteka opracowana przez firmę Microsoft, którą można obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="59d07-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="59d07-124">[Zasady pomocy technicznej platformy .NET Core](https://www.microsoft.com/net/platform/support-policy) w dalszym ciągu pokrywają się z nią.</span><span class="sxs-lookup"><span data-stu-id="59d07-124">The [.NET Core support policy](https://www.microsoft.com/net/platform/support-policy) continues to cover it.</span></span>

<span data-ttu-id="59d07-125">Json.NET i Entity Framework Core Kontynuuj pracę z ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="59d07-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="59d07-126">Nie będą jednak uwzględniane w strukturze udostępnionej.</span><span class="sxs-lookup"><span data-stu-id="59d07-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="59d07-127">Aby uzyskać więcej informacji, zobacz [przyszłość JSON w programie .NET Core 3,0](https://github.com/dotnet/announcements/issues/90).</span><span class="sxs-lookup"><span data-stu-id="59d07-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="59d07-128">Zapoznaj [się również z pełną listą plików binarnych](https://github.com/aspnet/AspNetCore/issues/3755) usuniętych z udostępnionej platformy.</span><span class="sxs-lookup"><span data-stu-id="59d07-128">Also see [the complete list of binaries](https://github.com/aspnet/AspNetCore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="59d07-129">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="59d07-129">Reason for change</span></span>

<span data-ttu-id="59d07-130">Ta zmiana upraszcza użycie `Microsoft.AspNetCore.App` i zmniejsza duplikowanie między pakietami NuGet i udostępnionymi strukturami.</span><span class="sxs-lookup"><span data-stu-id="59d07-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="59d07-131">Aby uzyskać więcej informacji na temat motywacji tej zmiany, zobacz [ten wpis w blogu](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).</span><span class="sxs-lookup"><span data-stu-id="59d07-131">For more information on the motivation for this change, see [this blog post](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="59d07-132">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="59d07-132">Recommended action</span></span>

<span data-ttu-id="59d07-133">Nie jest konieczne, aby projekty korzystały z zestawów w `Microsoft.AspNetCore.App` jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="59d07-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="59d07-134">Aby uprościć Określanie elementów docelowych i użycie ASP.NET Core udostępnionej platformy, wiele pakietów NuGet dostarczonych od ASP.NET Core 1,0 nie jest już generowanych.</span><span class="sxs-lookup"><span data-stu-id="59d07-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="59d07-135">Interfejsy API udostępniane przez te pakiety są nadal dostępne dla aplikacji przy użyciu `<FrameworkReference>` do `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="59d07-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="59d07-136">Typowe przykłady interfejsów API to Kestrel, MVC i Razor.</span><span class="sxs-lookup"><span data-stu-id="59d07-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="59d07-137">Ta zmiana nie ma zastosowania do wszystkich plików binarnych, do których odwołuje się `Microsoft.AspNetCore.App` w ASP.NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="59d07-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="59d07-138">Do istotnych wyjątków należą:</span><span class="sxs-lookup"><span data-stu-id="59d07-138">Notable exceptions include:</span></span>

- <span data-ttu-id="59d07-139">biblioteki `Microsoft.Extensions`, które są dalej docelowe .NET Standard będą dostępne jako pakiety NuGet (zobacz https://github.com/aspnet/Extensions).</span><span class="sxs-lookup"><span data-stu-id="59d07-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see https://github.com/aspnet/Extensions).</span></span>
- <span data-ttu-id="59d07-140">Interfejsy API produkowane przez zespół ASP.NET Core, które nie są częścią `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="59d07-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="59d07-141">Na przykład następujące składniki są dostępne jako pakiety NuGet:</span><span class="sxs-lookup"><span data-stu-id="59d07-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="59d07-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="59d07-142">Entity Framework Core</span></span>
  - <span data-ttu-id="59d07-143">Interfejsy API zapewniające integrację innych firm</span><span class="sxs-lookup"><span data-stu-id="59d07-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="59d07-144">Funkcje eksperymentalne</span><span class="sxs-lookup"><span data-stu-id="59d07-144">Experimental features</span></span>
  - <span data-ttu-id="59d07-145">Interfejsy API z zależnościami, które nie mogą [spełnić wymagań, które mają być zawarte w strukturze udostępnionej](https://github.com/aspnet/AspNetCore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span><span class="sxs-lookup"><span data-stu-id="59d07-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/aspnet/AspNetCore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="59d07-146">Rozszerzenia MVC obsługujące obsługę Json.NET.</span><span class="sxs-lookup"><span data-stu-id="59d07-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="59d07-147">Interfejs API zostanie dostarczony jako pakiet NuGet do obsługi Json.NET i MVC.</span><span class="sxs-lookup"><span data-stu-id="59d07-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="59d07-148">Klient platformy .NET sygnalizujący będzie nadal obsługiwał .NET Standard i dostarczać jako pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="59d07-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="59d07-149">Jest ona przeznaczona do użycia w wielu środowiskach uruchomieniowych platformy .NET, takich jak Xamarin i platformy UWP.</span><span class="sxs-lookup"><span data-stu-id="59d07-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="59d07-150">Aby uzyskać więcej informacji, zobacz sekcję [Zatrzymaj tworzenie pakietów dla zestawów udostępnionych struktur w 3,0](https://github.com/aspnet/AspNetCore/issues/3756).</span><span class="sxs-lookup"><span data-stu-id="59d07-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/aspnet/AspNetCore/issues/3756).</span></span> <span data-ttu-id="59d07-151">W przypadku dyskusji zobacz [ASPNET/AspNetCore # 3757](https://github.com/aspnet/AspNetCore/issues/3757).</span><span class="sxs-lookup"><span data-stu-id="59d07-151">For discussion, see [aspnet/AspNetCore#3757](https://github.com/aspnet/AspNetCore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="59d07-152">Kategoria</span><span class="sxs-lookup"><span data-stu-id="59d07-152">Category</span></span>

<span data-ttu-id="59d07-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="59d07-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="59d07-154">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="59d07-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
