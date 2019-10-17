---
ms.openlocfilehash: 09fd95ba5f3aee59f2abdfbb4e64eb6202e2b873
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394035"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="3312f-101">MVC: typy "Pubternal" zostały zmienione na wewnętrzne</span><span class="sxs-lookup"><span data-stu-id="3312f-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="3312f-102">W ASP.NET Core 3,0 wszystkie typy "pubternal" w MVC zostały zaktualizowane do `public` w obsługiwanej przestrzeni nazw lub `internal`, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="3312f-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3312f-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="3312f-103">Change description</span></span>

<span data-ttu-id="3312f-104">W ASP.NET Core typy "pubternal" są deklarowane jako `public`, ale znajdują się w @no__t przestrzeni nazw z sufiksem -1.</span><span class="sxs-lookup"><span data-stu-id="3312f-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="3312f-105">Chociaż te typy są `public`, nie mają żadnych zasad pomocy technicznej i podlegają nieprzerwanym zmianom.</span><span class="sxs-lookup"><span data-stu-id="3312f-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="3312f-106">Niestety, przypadkowe użycie tych typów było wspólne, co spowodowało istotne zmiany w tych projektach i ograniczenie możliwości utrzymania struktury.</span><span class="sxs-lookup"><span data-stu-id="3312f-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3312f-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="3312f-107">Version introduced</span></span>

<span data-ttu-id="3312f-108">3.0</span><span class="sxs-lookup"><span data-stu-id="3312f-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3312f-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="3312f-109">Old behavior</span></span>

<span data-ttu-id="3312f-110">Niektóre typy w MVC zostały `public`, ale w przestrzeni nazw `.Internal`.</span><span class="sxs-lookup"><span data-stu-id="3312f-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="3312f-111">Te typy nie miały zasad pomocy technicznej i podlegają istotnym zmianom.</span><span class="sxs-lookup"><span data-stu-id="3312f-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3312f-112">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="3312f-112">New behavior</span></span>

<span data-ttu-id="3312f-113">Wszystkie takie typy są aktualizowane do `public` w obsługiwanej przestrzeni nazw lub oznaczone jako `internal`.</span><span class="sxs-lookup"><span data-stu-id="3312f-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3312f-114">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="3312f-114">Reason for change</span></span>

<span data-ttu-id="3312f-115">Przypadkowe użycie typów "pubternal" jest wspólne, co skutkuje istotnymi zmianami w tych projektach i ograniczeniem możliwości utrzymania struktury.</span><span class="sxs-lookup"><span data-stu-id="3312f-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3312f-116">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="3312f-116">Recommended action</span></span>

<span data-ttu-id="3312f-117">Jeśli używasz typów, które staną się naprawdę `public` i zostały przeniesione do nowej, obsługiwanej przestrzeni nazw, zaktualizuj odwołania, aby odpowiadały nowym przestrzeniom nazw.</span><span class="sxs-lookup"><span data-stu-id="3312f-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="3312f-118">Jeśli używasz typów, które zostały oznaczone jako `internal`, musisz znaleźć alternatywę.</span><span class="sxs-lookup"><span data-stu-id="3312f-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="3312f-119">Wcześniej typy "pubternal" nigdy nie były obsługiwane do użytku publicznego.</span><span class="sxs-lookup"><span data-stu-id="3312f-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="3312f-120">Jeśli istnieją określone typy w tych obszarach nazw, które mają krytyczne znaczenie dla aplikacji, należy rozwiązać problem na [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span><span class="sxs-lookup"><span data-stu-id="3312f-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span></span> <span data-ttu-id="3312f-121">W przypadku tworzenia żądanych typów `public`.</span><span class="sxs-lookup"><span data-stu-id="3312f-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="3312f-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="3312f-122">Category</span></span>

<span data-ttu-id="3312f-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3312f-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3312f-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3312f-124">Affected APIs</span></span>

<span data-ttu-id="3312f-125">Ta zmiana obejmuje typy w następujących przestrzeniach nazw:</span><span class="sxs-lookup"><span data-stu-id="3312f-125">This change includes types in the following namespaces:</span></span>

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
