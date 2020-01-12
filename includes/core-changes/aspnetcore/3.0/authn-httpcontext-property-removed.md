---
ms.openlocfilehash: 60ebcd9fc9ca18c33d31b82ba5020426d22a7d5a
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902059"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a><span data-ttu-id="c75f4-101">Uwierzytelnianie: Właściwość HttpContext. Authentication została usunięta</span><span class="sxs-lookup"><span data-stu-id="c75f4-101">Authentication: HttpContext.Authentication property removed</span></span>

<span data-ttu-id="c75f4-102">Właściwość `Authentication` przestarzała w `HttpContext` została usunięta.</span><span class="sxs-lookup"><span data-stu-id="c75f4-102">The deprecated `Authentication` property on `HttpContext` has been removed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c75f4-103">Opis zmiany</span><span class="sxs-lookup"><span data-stu-id="c75f4-103">Change description</span></span>

<span data-ttu-id="c75f4-104">W ramach programu [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504)właściwość przestarzałe `Authentication` w `HttpContext` została usunięta.</span><span class="sxs-lookup"><span data-stu-id="c75f4-104">As part of [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504), the deprecated `Authentication` property on `HttpContext` has been removed.</span></span> <span data-ttu-id="c75f4-105">Właściwość `Authentication` została uznana za przestarzałą od 2,0.</span><span class="sxs-lookup"><span data-stu-id="c75f4-105">The `Authentication` property has been deprecated since 2.0.</span></span> <span data-ttu-id="c75f4-106">Opublikowano [Przewodnik migracji](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) w celu migrowania kodu przy użyciu tej przestarzałej właściwości do nowych interfejsów API wymiany.</span><span class="sxs-lookup"><span data-stu-id="c75f4-106">A [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) was published to migrate code using this deprecated property to the new replacement APIs.</span></span> <span data-ttu-id="c75f4-107">Pozostałe nieużywane klasy/interfejsy API powiązane ze starym stosem uwierzytelniania ASP.NET Core 1. x zostały usunięte w [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65)zatwierdzania.</span><span class="sxs-lookup"><span data-stu-id="c75f4-107">The remaining unused classes / APIs related to the old ASP.NET Core 1.x authentication stack were removed in commit [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65).</span></span>

<span data-ttu-id="c75f4-108">Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 6533](https://github.com/dotnet/aspnetcore/issues/6533).</span><span class="sxs-lookup"><span data-stu-id="c75f4-108">For discussion, see [dotnet/aspnetcore#6533](https://github.com/dotnet/aspnetcore/issues/6533).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c75f4-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="c75f4-109">Version introduced</span></span>

<span data-ttu-id="c75f4-110">3.0</span><span class="sxs-lookup"><span data-stu-id="c75f4-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c75f4-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="c75f4-111">Reason for change</span></span>

<span data-ttu-id="c75f4-112">Interfejsy API ASP.NET Core 1,0 zostały zastąpione metodami rozszerzającymi w <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="c75f4-112">ASP.NET Core 1.0 APIs have been replaced by extension methods in <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c75f4-113">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="c75f4-113">Recommended action</span></span>

<span data-ttu-id="c75f4-114">Zapoznaj się z [przewodnikiem migracji](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span><span class="sxs-lookup"><span data-stu-id="c75f4-114">See the [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span></span>

#### <a name="category"></a><span data-ttu-id="c75f4-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="c75f4-115">Category</span></span>

<span data-ttu-id="c75f4-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c75f4-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c75f4-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c75f4-117">Affected APIs</span></span>

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
