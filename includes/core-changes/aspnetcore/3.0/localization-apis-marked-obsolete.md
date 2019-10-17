---
ms.openlocfilehash: da1ec7908b3082fc61313cb805773aa600bc1b5d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394420"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="f9cff-101">Lokalizacja: ResourceManagerWithCultureStringLocalizer i WithCulture oznaczone jako przestarzałe</span><span class="sxs-lookup"><span data-stu-id="f9cff-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="f9cff-102">Klasa [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) i element członkowski interfejsu [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) często są źródłami pomyłek dla użytkowników lokalizacji, szczególnie podczas tworzenia własnej implementacji `IStringLocalizer`.</span><span class="sxs-lookup"><span data-stu-id="f9cff-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="f9cff-103">Te elementy dają użytkownikowi wrażenie, że wystąpienie `IStringLocalizer` ma wartość "w poszczególnych językach".</span><span class="sxs-lookup"><span data-stu-id="f9cff-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="f9cff-104">W rzeczywistości wystąpienia powinny mieć tylko wartość "dla zasobu".</span><span class="sxs-lookup"><span data-stu-id="f9cff-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="f9cff-105">Wyszukiwany język jest określany przez `CultureInfo.CurrentUICulture` w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f9cff-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="f9cff-106">Aby wyeliminować Źródło pomyłek, interfejsy API zostały oznaczone jako przestarzałe w ASP.NET Core 3,0 wersja zapoznawcza 3.</span><span class="sxs-lookup"><span data-stu-id="f9cff-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="f9cff-107">Interfejsy API zostaną usunięte w przyszłej wersji.</span><span class="sxs-lookup"><span data-stu-id="f9cff-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="f9cff-108">W przypadku kontekstu zobacz [ASPNET/AspNetCore # 3324](https://github.com/aspnet/AspNetCore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="f9cff-108">For context, see [aspnet/AspNetCore#3324](https://github.com/aspnet/AspNetCore/issues/3324).</span></span> <span data-ttu-id="f9cff-109">W przypadku dyskusji zobacz [ASPNET/AspNetCore # 7756](https://github.com/aspnet/AspNetCore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="f9cff-109">For discussion, see [aspnet/AspNetCore#7756](https://github.com/aspnet/AspNetCore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f9cff-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="f9cff-110">Version introduced</span></span>

<span data-ttu-id="f9cff-111">3.0</span><span class="sxs-lookup"><span data-stu-id="f9cff-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f9cff-112">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="f9cff-112">Old behavior</span></span>

<span data-ttu-id="f9cff-113">Metody nie zostały oznaczone jako `Obsolete`.</span><span class="sxs-lookup"><span data-stu-id="f9cff-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f9cff-114">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="f9cff-114">New behavior</span></span>

<span data-ttu-id="f9cff-115">Metody są oznaczone `Obsolete`.</span><span class="sxs-lookup"><span data-stu-id="f9cff-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f9cff-116">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="f9cff-116">Reason for change</span></span>

<span data-ttu-id="f9cff-117">Interfejsy API przedstawiają przypadek użycia, który nie jest zalecany.</span><span class="sxs-lookup"><span data-stu-id="f9cff-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="f9cff-118">Wystąpił problem z projektowaniem lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="f9cff-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f9cff-119">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="f9cff-119">Recommended action</span></span>

<span data-ttu-id="f9cff-120">Zaleca się używanie `ResourceManagerStringLocalizer` zamiast.</span><span class="sxs-lookup"><span data-stu-id="f9cff-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="f9cff-121">Pozwól, aby kultura była ustawiona przez `CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="f9cff-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="f9cff-122">Jeśli to nie jest opcja, Utwórz i Użyj kopii [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span><span class="sxs-lookup"><span data-stu-id="f9cff-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="f9cff-123">Kategoria</span><span class="sxs-lookup"><span data-stu-id="f9cff-123">Category</span></span>

<span data-ttu-id="f9cff-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f9cff-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f9cff-125">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f9cff-125">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
