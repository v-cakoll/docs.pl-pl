---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901631"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="3010d-101">Autoryzacja: implementacje IAuthorizationPolicyProvider wymagają nowej metody</span><span class="sxs-lookup"><span data-stu-id="3010d-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="3010d-102">W ASP.NET Core 3,0 dodano nową `GetFallbackPolicyAsync` metodę do. `IAuthorizationPolicyProvider`</span><span class="sxs-lookup"><span data-stu-id="3010d-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="3010d-103">Te zasady powrotu są używane przez oprogramowanie pośredniczące autoryzacji, gdy nie określono zasad.</span><span class="sxs-lookup"><span data-stu-id="3010d-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="3010d-104">Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="3010d-104">For more information, see [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3010d-105">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="3010d-105">Version introduced</span></span>

<span data-ttu-id="3010d-106">3.0</span><span class="sxs-lookup"><span data-stu-id="3010d-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3010d-107">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="3010d-107">Old behavior</span></span>

<span data-ttu-id="3010d-108">Implementacje `IAuthorizationPolicyProvider` nie wymagały `GetFallbackPolicyAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="3010d-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3010d-109">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="3010d-109">New behavior</span></span>

<span data-ttu-id="3010d-110">Implementacje `IAuthorizationPolicyProvider` wymagają `GetFallbackPolicyAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="3010d-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3010d-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="3010d-111">Reason for change</span></span>

<span data-ttu-id="3010d-112">Nowa metoda była wymagana do użycia w przypadku `AuthorizationMiddleware` , gdy nie określono żadnych zasad.</span><span class="sxs-lookup"><span data-stu-id="3010d-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3010d-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="3010d-113">Recommended action</span></span>

<span data-ttu-id="3010d-114">Dodaj `GetFallbackPolicyAsync` metodę do implementacji programu `IAuthorizationPolicyProvider`.</span><span class="sxs-lookup"><span data-stu-id="3010d-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="3010d-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="3010d-115">Category</span></span>

<span data-ttu-id="3010d-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3010d-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3010d-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3010d-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
