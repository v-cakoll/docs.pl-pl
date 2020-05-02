---
ms.openlocfilehash: 6deeb7debce9b731f3871b7de0ad8df8a8cdafea
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728293"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a><span data-ttu-id="6c724-101">Lokalizacja: Usunięto klasę ResourceManagerWithCultureStringLocalizer i element członkowski interfejsu WithCulture</span><span class="sxs-lookup"><span data-stu-id="6c724-101">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>

<span data-ttu-id="6c724-102">Klasa [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) i Metoda [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) zostały usunięte w programie .NET 5,0 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="6c724-102">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were removed in .NET 5.0 Preview 1.</span></span>

<span data-ttu-id="6c724-103">W przypadku kontekstu zobacz [ASPNET/anonse # 346](https://github.com/aspnet/Announcements/issues/346) i [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="6c724-103">For context, see [aspnet/Announcements#346](https://github.com/aspnet/Announcements/issues/346) and [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="6c724-104">Aby uzyskać więcej dyskusji na temat tej zmiany, zobacz [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="6c724-104">For discussion on this change, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6c724-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="6c724-105">Version introduced</span></span>

<span data-ttu-id="6c724-106">5,0 wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="6c724-106">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6c724-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="6c724-107">Old behavior</span></span>

<span data-ttu-id="6c724-108">`ResourceManagerWithCultureStringLocalizer` Klasa i `ResourceManagerStringLocalizer.WithCulture` Metoda są [przestarzałe w programie .NET Core 3,0 w wersji zapoznawczej 3 i nowszych](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span><span class="sxs-lookup"><span data-stu-id="6c724-108">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method are [obsolete in .NET Core 3.0 Preview 3 and later](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6c724-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="6c724-109">New behavior</span></span>

<span data-ttu-id="6c724-110">`ResourceManagerWithCultureStringLocalizer` Klasa i `ResourceManagerStringLocalizer.WithCulture` Metoda zostały usunięte w programie .NET 5,0 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="6c724-110">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method have been removed in .NET 5.0 Preview 1.</span></span> <span data-ttu-id="6c724-111">Aby uzyskać spis zmian wprowadzonych w programie, zobacz żądanie ściągnięcia w programie [dotnet/Extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files).</span><span class="sxs-lookup"><span data-stu-id="6c724-111">For an inventory of the changes made, see the pull request at [dotnet/extensions#2562](https://github.com/dotnet/extensions/pull/2562/files).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6c724-112">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="6c724-112">Reason for change</span></span>

<span data-ttu-id="6c724-113">Metody [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) i [ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) często są źródłami pomyłek dla użytkowników lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="6c724-113">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were often sources of confusion for users of localization.</span></span> <span data-ttu-id="6c724-114">Pomyłka była szczególnie wysoka podczas tworzenia niestandardowej <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementacji.</span><span class="sxs-lookup"><span data-stu-id="6c724-114">The confusion was especially high when creating a custom <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementation.</span></span> <span data-ttu-id="6c724-115">Ta klasa i Metoda zapewniają konsumentom wrażenie, że `IStringLocalizer` wystąpienie jest oczekiwane na "dla poszczególnych zasobów".</span><span class="sxs-lookup"><span data-stu-id="6c724-115">This class and method give consumers the impression that an `IStringLocalizer` instance is expected to be "per-language, per-resource".</span></span> <span data-ttu-id="6c724-116">W rzeczywistości wystąpienie powinno mieć tylko wartość "dla zasobu".</span><span class="sxs-lookup"><span data-stu-id="6c724-116">In reality, the instance should only be "per-resource".</span></span> <span data-ttu-id="6c724-117">W czasie wykonywania <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> Właściwość określa język, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="6c724-117">At run time, the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> property determines the language to be used.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6c724-118">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="6c724-118">Recommended action</span></span>

<span data-ttu-id="6c724-119">Zatrzymaj korzystanie z `ResourceManagerWithCultureStringLocalizer` klasy i `ResourceManagerStringLocalizer.WithCulture` metody.</span><span class="sxs-lookup"><span data-stu-id="6c724-119">Stop using the `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method.</span></span>

#### <a name="category"></a><span data-ttu-id="6c724-120">Kategoria</span><span class="sxs-lookup"><span data-stu-id="6c724-120">Category</span></span>

<span data-ttu-id="6c724-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6c724-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6c724-122">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6c724-122">Affected APIs</span></span>

- [<span data-ttu-id="6c724-123">ResourceManagerWithCultureStringLocalizer</span><span class="sxs-lookup"><span data-stu-id="6c724-123">ResourceManagerWithCultureStringLocalizer</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [<span data-ttu-id="6c724-124">ResourceManagerStringLocalizer.WithCulture</span><span class="sxs-lookup"><span data-stu-id="6c724-124">ResourceManagerStringLocalizer.WithCulture</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
