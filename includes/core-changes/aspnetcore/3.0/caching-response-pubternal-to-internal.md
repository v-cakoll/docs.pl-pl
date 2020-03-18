---
ms.openlocfilehash: ae5a5fbf97ed4a03de7d35b9d5d5ca8de3aebc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394168"
---
### <a name="caching-responsecaching-pubternal-types-changed-to-internal"></a><span data-ttu-id="a87b0-101">Buforowanie: ResponseCaching "pubternal" typy zmienione na wewnętrzne</span><span class="sxs-lookup"><span data-stu-id="a87b0-101">Caching: ResponseCaching "pubternal" types changed to internal</span></span>

<span data-ttu-id="a87b0-102">W ASP.NET Core 3.0 typy "pubternal" `ResponseCaching` `internal`zostały zmienione na .</span><span class="sxs-lookup"><span data-stu-id="a87b0-102">In ASP.NET Core 3.0, "pubternal" types in `ResponseCaching` have been changed to `internal`.</span></span>

<span data-ttu-id="a87b0-103">Ponadto implementacje domyślne `IResponseCachingPolicyProvider` `IResponseCachingKeyProvider` i nie są już dodawane `AddResponseCaching` do usług jako część metody.</span><span class="sxs-lookup"><span data-stu-id="a87b0-103">In addition, default implementations of `IResponseCachingPolicyProvider` and `IResponseCachingKeyProvider` are no longer added to services as part of the `AddResponseCaching` method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a87b0-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="a87b0-104">Change description</span></span>

<span data-ttu-id="a87b0-105">W ASP.NET Core typy "pubternal" `public` są deklarowane jako, ale `.Internal`znajdują się w przestrzeni nazw sufiksu.</span><span class="sxs-lookup"><span data-stu-id="a87b0-105">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a namespace suffixed with `.Internal`.</span></span> <span data-ttu-id="a87b0-106">Chociaż te typy są publiczne, nie mają zasad wsparcia i podlegają zmianom powoduniam.</span><span class="sxs-lookup"><span data-stu-id="a87b0-106">While these types are public, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="a87b0-107">Niestety, przypadkowe użycie tych typów było powszechne, co spowodowało przełomowe zmiany w tych projektach i ograniczyło możliwość utrzymania struktury.</span><span class="sxs-lookup"><span data-stu-id="a87b0-107">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a87b0-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="a87b0-108">Version introduced</span></span>

<span data-ttu-id="a87b0-109">3.0</span><span class="sxs-lookup"><span data-stu-id="a87b0-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a87b0-110">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="a87b0-110">Old behavior</span></span>

<span data-ttu-id="a87b0-111">Te typy były publicznie widoczne, ale nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a87b0-111">These types were publicly visible, but unsupported.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a87b0-112">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="a87b0-112">New behavior</span></span>

<span data-ttu-id="a87b0-113">Te typy `internal`są teraz .</span><span class="sxs-lookup"><span data-stu-id="a87b0-113">These types are now `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a87b0-114">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="a87b0-114">Reason for change</span></span>

<span data-ttu-id="a87b0-115">Zakres `internal` lepiej odzwierciedla nieobsługiwane zasady.</span><span class="sxs-lookup"><span data-stu-id="a87b0-115">The `internal` scope better reflects the unsupported policy.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a87b0-116">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="a87b0-116">Recommended action</span></span>

<span data-ttu-id="a87b0-117">Kopiuj typy używane przez aplikację lub bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="a87b0-117">Copy types that are used by your app or library.</span></span>

#### <a name="category"></a><span data-ttu-id="a87b0-118">Kategoria</span><span class="sxs-lookup"><span data-stu-id="a87b0-118">Category</span></span>

<span data-ttu-id="a87b0-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a87b0-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a87b0-120">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a87b0-120">Affected APIs</span></span>

- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- <xref:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.%23ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- `M:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)",
"nameWithType": "ResponseCachingMiddleware.ResponseCachingMiddleware(RequestDelegate, IOptions<ResponseCachingOptions>, ILoggerFactory, IResponseCachingPolicyProvider, IResponseCache, IResponseCachingKeyProvider)`

-->
