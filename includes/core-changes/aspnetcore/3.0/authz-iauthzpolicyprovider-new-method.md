---
ms.openlocfilehash: a16d443a37fb0bb5f6bdc4a39e7dcb4f91c54ead
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394245"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="9f596-101">Autoryzacja: implementacje IAuthorizationPolicyProvider wymagają nowej metody</span><span class="sxs-lookup"><span data-stu-id="9f596-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="9f596-102">W ASP.NET Core 3,0 dodano nową metodę `GetFallbackPolicyAsync` do `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="9f596-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="9f596-103">Te zasady powrotu są używane przez oprogramowanie pośredniczące autoryzacji, gdy nie określono zasad.</span><span class="sxs-lookup"><span data-stu-id="9f596-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="9f596-104">Aby uzyskać więcej informacji, zobacz [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="9f596-104">For more information, see [aspnet/AspNetCore#9759](https://github.com/aspnet/AspNetCore/pull/9759).</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="9f596-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="9f596-105">Version introduced</span></span>

<span data-ttu-id="9f596-106">3.0</span><span class="sxs-lookup"><span data-stu-id="9f596-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9f596-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="9f596-107">Old behavior</span></span>

<span data-ttu-id="9f596-108">Implementacje `IAuthorizationPolicyProvider` nie wymagały metody `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="9f596-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9f596-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="9f596-109">New behavior</span></span>

<span data-ttu-id="9f596-110">Implementacje `IAuthorizationPolicyProvider` wymagają metody `GetFallbackPolicyAsync`.</span><span class="sxs-lookup"><span data-stu-id="9f596-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9f596-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="9f596-111">Reason for change</span></span>

<span data-ttu-id="9f596-112">Nowa metoda była wymagana dla nowego `AuthorizationMiddleware` do użycia, gdy nie określono żadnych zasad.</span><span class="sxs-lookup"><span data-stu-id="9f596-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9f596-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="9f596-113">Recommended action</span></span>

<span data-ttu-id="9f596-114">Dodaj metodę `GetFallbackPolicyAsync` do implementacji `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="9f596-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="9f596-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="9f596-115">Category</span></span>

<span data-ttu-id="9f596-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9f596-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9f596-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="9f596-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
