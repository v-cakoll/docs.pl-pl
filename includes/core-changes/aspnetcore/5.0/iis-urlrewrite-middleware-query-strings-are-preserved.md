---
ms.openlocfilehash: 29908ed916690e67db3cc5d72ebe1b1c6aea45c6
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325220"
---
### <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a><span data-ttu-id="9b777-101">IIS: UrlRewrite ciągi zapytania oprogramowania pośredniczącego są zachowywane</span><span class="sxs-lookup"><span data-stu-id="9b777-101">IIS: UrlRewrite middleware query strings are preserved</span></span>

<span data-ttu-id="9b777-102">Usterka oprogramowania pośredniczącego usług IIS UrlRewrite uniemożliwiła zachowywanie ciągu zapytania w regułach ponownego zapisywania.</span><span class="sxs-lookup"><span data-stu-id="9b777-102">An IIS UrlRewrite middleware defect prevented the query string from being preserved in rewrite rules.</span></span> <span data-ttu-id="9b777-103">Ta usterka została naprawiona w celu zachowania spójności z zachowaniem modułu UrlRewrite IIS.</span><span class="sxs-lookup"><span data-stu-id="9b777-103">That defect has been fixed to maintain consistency with the IIS UrlRewrite Module's behavior.</span></span>

<span data-ttu-id="9b777-104">Aby zapoznać się z omówieniem, zobacz temat Issue [dotnet/aspnetcore # 22972](https://github.com/dotnet/aspnetcore/issues/22972).</span><span class="sxs-lookup"><span data-stu-id="9b777-104">For discussion, see issue [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9b777-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="9b777-105">Version introduced</span></span>

<span data-ttu-id="9b777-106">ASP.NET Core 5,0 wersja zapoznawcza 7</span><span class="sxs-lookup"><span data-stu-id="9b777-106">ASP.NET Core 5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9b777-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="9b777-107">Old behavior</span></span>

<span data-ttu-id="9b777-108">Weź pod uwagę następujące zasady ponownego zapisywania:</span><span class="sxs-lookup"><span data-stu-id="9b777-108">Consider the following rewrite rule:</span></span>

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

<span data-ttu-id="9b777-109">Poprzednia reguła nie dołącza ciągu zapytania.</span><span class="sxs-lookup"><span data-stu-id="9b777-109">The preceding rule doesn't append the query string.</span></span> <span data-ttu-id="9b777-110">Identyfikator URI, taki jak `/about?id=1` przekieruje do `/contact` , zamiast `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="9b777-110">A URI like `/about?id=1` redirects to `/contact` instead of `/contact?id=1`.</span></span> <span data-ttu-id="9b777-111">`appendQueryString`Atrybut jest również domyślnie `true` .</span><span class="sxs-lookup"><span data-stu-id="9b777-111">The `appendQueryString` attribute defaults to `true` as well.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9b777-112">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="9b777-112">New behavior</span></span>

<span data-ttu-id="9b777-113">Ciąg zapytania jest zachowywany.</span><span class="sxs-lookup"><span data-stu-id="9b777-113">The query string is preserved.</span></span> <span data-ttu-id="9b777-114">Identyfikator URI z przykładu w [starym zachowaniu](#old-behavior) będzie miał wartość `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="9b777-114">The URI from the example in [Old behavior](#old-behavior) would be `/contact?id=1`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9b777-115">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="9b777-115">Reason for change</span></span>

<span data-ttu-id="9b777-116">Stare zachowanie nie jest zgodne z zachowaniem modułu UrlRewrite IIS.</span><span class="sxs-lookup"><span data-stu-id="9b777-116">The old behavior didn't match the IIS UrlRewrite Module's behavior.</span></span> <span data-ttu-id="9b777-117">Do obsługi portów między programami i modułem pośredniczącym celem jest zachowanie spójnych zachowań.</span><span class="sxs-lookup"><span data-stu-id="9b777-117">To support porting between the middleware and module, the goal is to maintain consistent behaviors.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9b777-118">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="9b777-118">Recommended action</span></span>

<span data-ttu-id="9b777-119">Jeśli preferowane jest zachowanie usunięcia ciągu zapytania, należy ustawić `action` element na `appendQueryString="false"` .</span><span class="sxs-lookup"><span data-stu-id="9b777-119">If the behavior of removing the query string is preferred, set the `action` element to `appendQueryString="false"`.</span></span>

#### <a name="category"></a><span data-ttu-id="9b777-120">Kategoria</span><span class="sxs-lookup"><span data-stu-id="9b777-120">Category</span></span>

<span data-ttu-id="9b777-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9b777-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9b777-122">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="9b777-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
