---
ms.openlocfilehash: 74b989a2413d2192f7cf5208e400eaed879ea096
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198524"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="d0c10-101">Autoryzacja: implementacje IAuthorizationPolicyProvider wymagają nowej metody</span><span class="sxs-lookup"><span data-stu-id="d0c10-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="d0c10-102">W ASP.NET Core 3,0 dodano nową metodę `GetFallbackPolicyAsync` do `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="d0c10-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="d0c10-103">Te zasady powrotu są używane przez oprogramowanie pośredniczące autoryzacji, gdy nie określono zasad.</span><span class="sxs-lookup"><span data-stu-id="d0c10-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="d0c10-104">Aby uzyskać więcej informacji, zobacz [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="d0c10-104">For more information, see [aspnet/AspNetCore#9759](https://github.com/aspnet/AspNetCore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d0c10-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="d0c10-105">Version introduced</span></span>

<span data-ttu-id="d0c10-106">3.0</span><span class="sxs-lookup"><span data-stu-id="d0c10-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d0c10-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="d0c10-107">Old behavior</span></span>

<span data-ttu-id="d0c10-108">Implementacje `IAuthorizationPolicyProvider` nie wymagały metody `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="d0c10-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d0c10-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="d0c10-109">New behavior</span></span>

<span data-ttu-id="d0c10-110">Implementacje `IAuthorizationPolicyProvider` wymagają metody `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="d0c10-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d0c10-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="d0c10-111">Reason for change</span></span>

<span data-ttu-id="d0c10-112">Nowa metoda była wymagana dla nowego `AuthorizationMiddleware` do użycia, gdy nie określono żadnych zasad.</span><span class="sxs-lookup"><span data-stu-id="d0c10-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d0c10-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="d0c10-113">Recommended action</span></span>

<span data-ttu-id="d0c10-114">Dodaj metodę `GetFallbackPolicyAsync` do implementacji `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="d0c10-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="d0c10-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d0c10-115">Category</span></span>

<span data-ttu-id="d0c10-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d0c10-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d0c10-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d0c10-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
