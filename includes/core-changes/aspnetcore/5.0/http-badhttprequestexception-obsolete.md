---
ms.openlocfilehash: c4e7864262a11aafa4b7f1f4bdf632fbf084c560
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507098"
---
### <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a><span data-ttu-id="38288-101">HTTP: Kestrel i IIS BadHttpRequestException typy oznaczone jako przestarzałe i zastąpione</span><span class="sxs-lookup"><span data-stu-id="38288-101">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>

<span data-ttu-id="38288-102">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`i `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` zostały oznaczone jako przestarzałe i zmienione na pochodne `Microsoft.AspNetCore.Http.BadHttpRequestException`od.</span><span class="sxs-lookup"><span data-stu-id="38288-102">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` have been marked obsolete and changed to derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span> <span data-ttu-id="38288-103">Serwery Kestrel i IIS nadal generują stare typy wyjątków w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="38288-103">The Kestrel and IIS servers still throw their old exception types for backwards compatibility.</span></span> <span data-ttu-id="38288-104">Przestarzałe typy zostaną usunięte w przyszłej wersji.</span><span class="sxs-lookup"><span data-stu-id="38288-104">The obsolete types will be removed in a future release.</span></span>

<span data-ttu-id="38288-105">Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).</span><span class="sxs-lookup"><span data-stu-id="38288-105">For discussion, see [dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="38288-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="38288-106">Version introduced</span></span>

<span data-ttu-id="38288-107">5,0 wersja zapoznawcza 4</span><span class="sxs-lookup"><span data-stu-id="38288-107">5.0 Preview 4</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="38288-108">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="38288-108">Old behavior</span></span>

<span data-ttu-id="38288-109">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`i `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` pochodzące od <xref:System.IO.IOException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="38288-109">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` derived from <xref:System.IO.IOException?displayProperty=nameWithType>.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="38288-110">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="38288-110">New behavior</span></span>

<span data-ttu-id="38288-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`i `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` są przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="38288-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` are obsolete.</span></span> <span data-ttu-id="38288-112">Typy pochodzą z `Microsoft.AspNetCore.Http.BadHttpRequestException`, które pochodzą z `System.IO.IOException`.</span><span class="sxs-lookup"><span data-stu-id="38288-112">The types also derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`, which derives from `System.IO.IOException`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="38288-113">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="38288-113">Reason for change</span></span>

<span data-ttu-id="38288-114">Wprowadzono zmianę w:</span><span class="sxs-lookup"><span data-stu-id="38288-114">The change was made to:</span></span>

* <span data-ttu-id="38288-115">Konsolidowanie zduplikowanych typów.</span><span class="sxs-lookup"><span data-stu-id="38288-115">Consolidate duplicate types.</span></span>
* <span data-ttu-id="38288-116">Ujednolicenie zachowania między implementacjami serwera.</span><span class="sxs-lookup"><span data-stu-id="38288-116">Unify behavior across server implementations.</span></span>

<span data-ttu-id="38288-117">Aplikacja może teraz przechwycić wyjątek `Microsoft.AspNetCore.Http.BadHttpRequestException` podstawowy podczas korzystania z usługi Kestrel lub IIS.</span><span class="sxs-lookup"><span data-stu-id="38288-117">An app can now catch the base exception `Microsoft.AspNetCore.Http.BadHttpRequestException` when using either Kestrel or IIS.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="38288-118">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="38288-118">Recommended action</span></span>

<span data-ttu-id="38288-119">Zamień Użycie elementów `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` i `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` na. `Microsoft.AspNetCore.Http.BadHttpRequestException`</span><span class="sxs-lookup"><span data-stu-id="38288-119">Replace usages of `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` with `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span>

#### <a name="category"></a><span data-ttu-id="38288-120">Kategoria</span><span class="sxs-lookup"><span data-stu-id="38288-120">Category</span></span>

<span data-ttu-id="38288-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="38288-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="38288-122">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="38288-122">Affected APIs</span></span>

- [<span data-ttu-id="38288-123">Microsoft. AspNetCore. Server. IIS. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="38288-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [<span data-ttu-id="38288-124">Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="38288-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
