---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282527"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a><span data-ttu-id="0f4ab-101">HTTP: Niektóre ustawienia domyślne tej samej witryny zostały zmienione na Brak</span><span class="sxs-lookup"><span data-stu-id="0f4ab-101">HTTP: Some cookie SameSite defaults changed to None</span></span>

<span data-ttu-id="0f4ab-102">`SameSite`jest opcją dla plików cookie, które mogą pomóc w ograniczeniu niektórych ataków csrf (Cross-Site Request Forgery).</span><span class="sxs-lookup"><span data-stu-id="0f4ab-102">`SameSite` is an option for cookies that can help mitigate some Cross-Site Request Forgery (CSRF) attacks.</span></span> <span data-ttu-id="0f4ab-103">Gdy ta opcja została początkowo wprowadzona, niespójne wartości domyślne były używane w różnych ASP.NET podstawowych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-103">When this option was initially introduced, inconsistent defaults were used across various ASP.NET Core APIs.</span></span> <span data-ttu-id="0f4ab-104">Niespójność doprowadziła do mylących wyników.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-104">The inconsistency has led to confusing results.</span></span> <span data-ttu-id="0f4ab-105">Od ASP.NET Core 3.0 te wartości domyślne są lepiej wyrównane.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-105">As of ASP.NET Core 3.0, these defaults are better aligned.</span></span> <span data-ttu-id="0f4ab-106">Należy wyrazić zgodę na tę funkcję na podstawie pojmą.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-106">You must opt in to this feature on a per-component basis.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0f4ab-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="0f4ab-107">Version introduced</span></span>

<span data-ttu-id="0f4ab-108">3.0</span><span class="sxs-lookup"><span data-stu-id="0f4ab-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0f4ab-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="0f4ab-109">Old behavior</span></span>

<span data-ttu-id="0f4ab-110">Podobne ASP.NET podstawowe interfejsy <xref:Microsoft.AspNetCore.Http.SameSiteMode> API używały różnych wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-110">Similar ASP.NET Core APIs used different default <xref:Microsoft.AspNetCore.Http.SameSiteMode> values.</span></span> <span data-ttu-id="0f4ab-111">Przykład niespójności jest widoczny `HttpResponse.Cookies.Append(String, String)` w `HttpResponse.Cookies.Append(String, String, CookieOptions)`i , `SameSiteMode.None` które `SameSiteMode.Lax`domyślnie do i , odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-111">An example of the inconsistency is seen in `HttpResponse.Cookies.Append(String, String)` and `HttpResponse.Cookies.Append(String, String, CookieOptions)`, which defaulted to `SameSiteMode.None` and `SameSiteMode.Lax`, respectively.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0f4ab-112">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="0f4ab-112">New behavior</span></span>

<span data-ttu-id="0f4ab-113">Wszystkie interfejsy API, których dotyczy problem, domyślnie . `SameSiteMode.None`</span><span class="sxs-lookup"><span data-stu-id="0f4ab-113">All the affected APIs default to `SameSiteMode.None`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0f4ab-114">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="0f4ab-114">Reason for change</span></span>

<span data-ttu-id="0f4ab-115">Wartość domyślna została `SameSite` zmieniona, aby wprowadzić funkcję opt-in.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-115">The default value was changed to make `SameSite` an opt-in feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0f4ab-116">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="0f4ab-116">Recommended action</span></span>

<span data-ttu-id="0f4ab-117">Każdy składnik, który emituje pliki `SameSite` cookie musi zdecydować, czy jest odpowiedni dla jego scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-117">Each component that emits cookies needs to decide if `SameSite` is appropriate for its scenarios.</span></span> <span data-ttu-id="0f4ab-118">Przejrzyj użycie interfejsów API, których dotyczy problem, i ponownie skonfiguruj `SameSite` w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="0f4ab-118">Review your usage of the affected APIs and reconfigure `SameSite` as needed.</span></span>

#### <a name="category"></a><span data-ttu-id="0f4ab-119">Kategoria</span><span class="sxs-lookup"><span data-stu-id="0f4ab-119">Category</span></span>

<span data-ttu-id="0f4ab-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0f4ab-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f4ab-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="0f4ab-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
