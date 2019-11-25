---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74282527"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a><span data-ttu-id="e681b-101">HTTP: niektóre ustawienia domyślne SameSite pliku cookie zmieniły się na brak</span><span class="sxs-lookup"><span data-stu-id="e681b-101">HTTP: Some cookie SameSite defaults changed to None</span></span>

<span data-ttu-id="e681b-102">`SameSite` jest opcją dla plików cookie, która może pomóc w zmniejszeniu liczby ataków na wiele witryn (CSRF).</span><span class="sxs-lookup"><span data-stu-id="e681b-102">`SameSite` is an option for cookies that can help mitigate some Cross-Site Request Forgery (CSRF) attacks.</span></span> <span data-ttu-id="e681b-103">W przypadku wybrania tej opcji, niespójne wartości domyślne są używane w różnych ASP.NET Core interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="e681b-103">When this option was initially introduced, inconsistent defaults were used across various ASP.NET Core APIs.</span></span> <span data-ttu-id="e681b-104">Niespójność spowodowała mylące wyniki.</span><span class="sxs-lookup"><span data-stu-id="e681b-104">The inconsistency has led to confusing results.</span></span> <span data-ttu-id="e681b-105">W przypadku ASP.NET Core 3,0 te wartości domyślne są lepiej wyrównane.</span><span class="sxs-lookup"><span data-stu-id="e681b-105">As of ASP.NET Core 3.0, these defaults are better aligned.</span></span> <span data-ttu-id="e681b-106">Należy zadecydować, aby ta funkcja była oparta na poszczególnych składnikach.</span><span class="sxs-lookup"><span data-stu-id="e681b-106">You must opt in to this feature on a per-component basis.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e681b-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e681b-107">Version introduced</span></span>

<span data-ttu-id="e681b-108">3.0</span><span class="sxs-lookup"><span data-stu-id="e681b-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e681b-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="e681b-109">Old behavior</span></span>

<span data-ttu-id="e681b-110">Podobne ASP.NET Core interfejsy API używały różnych domyślnych wartości <xref:Microsoft.AspNetCore.Http.SameSiteMode>.</span><span class="sxs-lookup"><span data-stu-id="e681b-110">Similar ASP.NET Core APIs used different default <xref:Microsoft.AspNetCore.Http.SameSiteMode> values.</span></span> <span data-ttu-id="e681b-111">Przykład niespójności jest widoczny w `HttpResponse.Cookies.Append(String, String)` i `HttpResponse.Cookies.Append(String, String, CookieOptions)`, które domyślnie są odpowiednio `SameSiteMode.None` i `SameSiteMode.Lax`.</span><span class="sxs-lookup"><span data-stu-id="e681b-111">An example of the inconsistency is seen in `HttpResponse.Cookies.Append(String, String)` and `HttpResponse.Cookies.Append(String, String, CookieOptions)`, which defaulted to `SameSiteMode.None` and `SameSiteMode.Lax`, respectively.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e681b-112">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="e681b-112">New behavior</span></span>

<span data-ttu-id="e681b-113">Wszystkie narażone interfejsy API domyślnie `SameSiteMode.None`.</span><span class="sxs-lookup"><span data-stu-id="e681b-113">All the affected APIs default to `SameSiteMode.None`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e681b-114">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="e681b-114">Reason for change</span></span>

<span data-ttu-id="e681b-115">Wartość domyślna została zmieniona, aby `SameSite` funkcję wyboru.</span><span class="sxs-lookup"><span data-stu-id="e681b-115">The default value was changed to make `SameSite` an opt-in feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e681b-116">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="e681b-116">Recommended action</span></span>

<span data-ttu-id="e681b-117">Każdy składnik, który emituje pliki cookie, musi zdecydować, czy `SameSite` jest odpowiedni dla swoich scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="e681b-117">Each component that emits cookies needs to decide if `SameSite` is appropriate for its scenarios.</span></span> <span data-ttu-id="e681b-118">Zapoznaj się z użyciem odpowiednich interfejsów API i ponownie skonfiguruj `SameSite` w razie konieczności.</span><span class="sxs-lookup"><span data-stu-id="e681b-118">Review your usage of the affected APIs and reconfigure `SameSite` as needed.</span></span>

#### <a name="category"></a><span data-ttu-id="e681b-119">Kategoria</span><span class="sxs-lookup"><span data-stu-id="e681b-119">Category</span></span>

<span data-ttu-id="e681b-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e681b-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e681b-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e681b-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
