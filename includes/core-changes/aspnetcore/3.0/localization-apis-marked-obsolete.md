---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902013"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="b0245-101">Lokalizacja: ResourceManagerWithCultureStringLocalizer i WithCulture oznaczone jako przestarzałe</span><span class="sxs-lookup"><span data-stu-id="b0245-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="b0245-102">[Klasa ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) i element członkowski interfejsu [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) są często źródłem `IStringLocalizer` pomyłek dla użytkowników lokalizacji, szczególnie podczas tworzenia własnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="b0245-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="b0245-103">Te elementy dają użytkownikowi wrażenie, że wystąpienie `IStringLocalizer` jest "na język, na zasób".</span><span class="sxs-lookup"><span data-stu-id="b0245-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="b0245-104">W rzeczywistości wystąpienia powinny być tylko "na zasób".</span><span class="sxs-lookup"><span data-stu-id="b0245-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="b0245-105">Język wyszukiwany jest określana przez `CultureInfo.CurrentUICulture` w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b0245-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="b0245-106">Aby wyeliminować źródło zamieszania, interfejsy API zostały oznaczone jako przestarzałe w ASP.NET Core 3.0 Preview 3.</span><span class="sxs-lookup"><span data-stu-id="b0245-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="b0245-107">Interfejsy API zostaną usunięte w przyszłej wersji.</span><span class="sxs-lookup"><span data-stu-id="b0245-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="b0245-108">Dla kontekstu zobacz [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="b0245-108">For context, see [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="b0245-109">Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="b0245-109">For discussion, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b0245-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="b0245-110">Version introduced</span></span>

<span data-ttu-id="b0245-111">3.0</span><span class="sxs-lookup"><span data-stu-id="b0245-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b0245-112">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="b0245-112">Old behavior</span></span>

<span data-ttu-id="b0245-113">Metody nie zostały oznaczone `Obsolete`jako .</span><span class="sxs-lookup"><span data-stu-id="b0245-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b0245-114">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="b0245-114">New behavior</span></span>

<span data-ttu-id="b0245-115">Metody są `Obsolete`oznaczone .</span><span class="sxs-lookup"><span data-stu-id="b0245-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b0245-116">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="b0245-116">Reason for change</span></span>

<span data-ttu-id="b0245-117">Interfejsy API reprezentowałprzypadek użycia, który nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="b0245-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="b0245-118">Nie było zamieszania co do projektu lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="b0245-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b0245-119">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="b0245-119">Recommended action</span></span>

<span data-ttu-id="b0245-120">Zaleca się zamiast `ResourceManagerStringLocalizer` tego użyć.</span><span class="sxs-lookup"><span data-stu-id="b0245-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="b0245-121">Niech kultura być `CurrentCulture`ustawione przez .</span><span class="sxs-lookup"><span data-stu-id="b0245-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="b0245-122">Jeśli nie jest to opcja, utwórz i użyj kopii [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span><span class="sxs-lookup"><span data-stu-id="b0245-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="b0245-123">Kategoria</span><span class="sxs-lookup"><span data-stu-id="b0245-123">Category</span></span>

<span data-ttu-id="b0245-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b0245-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b0245-125">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b0245-125">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
