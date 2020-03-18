---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901690"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="b3a13-101">MVC: Typy "Pubternal" zmienione na wewnętrzne</span><span class="sxs-lookup"><span data-stu-id="b3a13-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="b3a13-102">W ASP.NET Core 3.0 wszystkie typy "pubternal" w MVC zostały zaktualizowane, aby być `public` w obsługiwanej przestrzeni nazw lub `internal` w stosownych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="b3a13-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b3a13-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="b3a13-103">Change description</span></span>

<span data-ttu-id="b3a13-104">W ASP.NET Core typy "pubternal" `public` są deklarowane `.Internal`jako, ale znajdują się w przestrzeni nazw -sufiks.</span><span class="sxs-lookup"><span data-stu-id="b3a13-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="b3a13-105">Chociaż te `public`typy są , nie mają żadnych zasad wsparcia i podlegają przełomowym zmianom.</span><span class="sxs-lookup"><span data-stu-id="b3a13-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="b3a13-106">Niestety, przypadkowe użycie tych typów było powszechne, co spowodowało przełomowe zmiany w tych projektach i ograniczyło możliwość utrzymania struktury.</span><span class="sxs-lookup"><span data-stu-id="b3a13-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b3a13-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="b3a13-107">Version introduced</span></span>

<span data-ttu-id="b3a13-108">3.0</span><span class="sxs-lookup"><span data-stu-id="b3a13-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b3a13-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="b3a13-109">Old behavior</span></span>

<span data-ttu-id="b3a13-110">Niektóre typy w `public` MVC `.Internal` były, ale w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b3a13-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="b3a13-111">Tego typu nie miały żadnych zasad wsparcia i podlegały przełomowym zmianom.</span><span class="sxs-lookup"><span data-stu-id="b3a13-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b3a13-112">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="b3a13-112">New behavior</span></span>

<span data-ttu-id="b3a13-113">Wszystkie takie typy są aktualizowane w `public` obsługiwanej przestrzeni `internal`nazw lub oznaczone jako .</span><span class="sxs-lookup"><span data-stu-id="b3a13-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b3a13-114">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="b3a13-114">Reason for change</span></span>

<span data-ttu-id="b3a13-115">Przypadkowe użycie typów "pubternal" było powszechne, co spowodowało zerwanie zmian w tych projektach i ograniczenie możliwości utrzymania struktury.</span><span class="sxs-lookup"><span data-stu-id="b3a13-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b3a13-116">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="b3a13-116">Recommended action</span></span>

<span data-ttu-id="b3a13-117">Jeśli używasz typów, które stały `public` się naprawdę i zostały przeniesione do nowego, obsługiwanego obszaru nazw, zaktualizuj odwołania, aby dopasować je do nowych obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="b3a13-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="b3a13-118">Jeśli używasz typów, które zostały `internal`oznaczone jako , musisz znaleźć alternatywę.</span><span class="sxs-lookup"><span data-stu-id="b3a13-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="b3a13-119">Wcześniej typy "pubternal" nigdy nie były obsługiwane do użytku publicznego.</span><span class="sxs-lookup"><span data-stu-id="b3a13-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="b3a13-120">Jeśli istnieją określone typy w tych przestrzeniach nazw, które mają kluczowe znaczenie dla aplikacji, należy zgłosić problem w [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="b3a13-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span> <span data-ttu-id="b3a13-121">Można zastanowić się nad dokonaniem `public`żądanych typów .</span><span class="sxs-lookup"><span data-stu-id="b3a13-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="b3a13-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="b3a13-122">Category</span></span>

<span data-ttu-id="b3a13-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b3a13-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b3a13-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b3a13-124">Affected APIs</span></span>

<span data-ttu-id="b3a13-125">Ta zmiana obejmuje typy w następujących obszarach nazw:</span><span class="sxs-lookup"><span data-stu-id="b3a13-125">This change includes types in the following namespaces:</span></span>

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->
