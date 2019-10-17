---
ms.openlocfilehash: 2945465bb6a3a362dc640641056712dffd73d559
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394200"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a><span data-ttu-id="0f84c-101">Uwierzytelnianie: Właściwość HttpContext. Authentication została usunięta</span><span class="sxs-lookup"><span data-stu-id="0f84c-101">Authentication: HttpContext.Authentication property removed</span></span>

<span data-ttu-id="0f84c-102">Właściwość "przestarzałe `Authentication`" w `HttpContext` została usunięta.</span><span class="sxs-lookup"><span data-stu-id="0f84c-102">The deprecated `Authentication` property on `HttpContext` has been removed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0f84c-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="0f84c-103">Change description</span></span>

<span data-ttu-id="0f84c-104">Jako część [ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504), właściwość przestarzała `Authentication` na `HttpContext` została usunięta.</span><span class="sxs-lookup"><span data-stu-id="0f84c-104">As part of [aspnet/AspNetCore#6504](https://github.com/aspnet/AspNetCore/pull/6504), the deprecated `Authentication` property on `HttpContext` has been removed.</span></span> <span data-ttu-id="0f84c-105">Właściwość `Authentication` została uznana za przestarzałą od 2,0.</span><span class="sxs-lookup"><span data-stu-id="0f84c-105">The `Authentication` property has been deprecated since 2.0.</span></span> <span data-ttu-id="0f84c-106">Opublikowano [Przewodnik migracji](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) w celu migrowania kodu przy użyciu tej przestarzałej właściwości do nowych interfejsów API wymiany.</span><span class="sxs-lookup"><span data-stu-id="0f84c-106">A [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) was published to migrate code using this deprecated property to the new replacement APIs.</span></span> <span data-ttu-id="0f84c-107">Pozostałe nieużywane klasy/interfejsy API powiązane ze starym stosem uwierzytelniania ASP.NET Core 1. x zostały usunięte w zatwierdzeniu [aspnet/AspNetCore@d7a7c65](https://github.com/aspnet/AspNetCore/commit/d7a7c65).</span><span class="sxs-lookup"><span data-stu-id="0f84c-107">The remaining unused classes / APIs related to the old ASP.NET Core 1.x authentication stack were removed in commit [aspnet/AspNetCore@d7a7c65](https://github.com/aspnet/AspNetCore/commit/d7a7c65).</span></span>

<span data-ttu-id="0f84c-108">W przypadku dyskusji zobacz [ASPNET/AspNetCore # 6533](https://github.com/aspnet/AspNetCore/issues/6533).</span><span class="sxs-lookup"><span data-stu-id="0f84c-108">For discussion, see [aspnet/AspNetCore#6533](https://github.com/aspnet/AspNetCore/issues/6533).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0f84c-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="0f84c-109">Version introduced</span></span>

<span data-ttu-id="0f84c-110">3.0</span><span class="sxs-lookup"><span data-stu-id="0f84c-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0f84c-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="0f84c-111">Reason for change</span></span>

<span data-ttu-id="0f84c-112">Interfejsy API ASP.NET Core 1,0 zostały zastąpione metodami rozszerzającymi w <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="0f84c-112">ASP.NET Core 1.0 APIs have been replaced by extension methods in <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0f84c-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="0f84c-113">Recommended action</span></span>

<span data-ttu-id="0f84c-114">Zapoznaj się z [przewodnikiem migracji](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span><span class="sxs-lookup"><span data-stu-id="0f84c-114">See the [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span></span>

#### <a name="category"></a><span data-ttu-id="0f84c-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="0f84c-115">Category</span></span>

<span data-ttu-id="0f84c-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0f84c-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f84c-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="0f84c-117">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpContext.Authentication?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler`
- `P:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext`
- `P:Microsoft.AspNetCore.Http.HttpContext.Authentication`

-->
