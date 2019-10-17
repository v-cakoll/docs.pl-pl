---
ms.openlocfilehash: ad451329d7b9ec15bc8b3c49159346d79944d692
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394028"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="3861a-101">Uwierzytelnianie: zamieniono typy Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="3861a-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="3861a-102">W ASP.NET Core 3,0 typy `Newtonsoft.Json` używane w interfejsach API uwierzytelniania zostały zastąpione typami `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="3861a-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="3861a-103">Z wyjątkiem następujących przypadków podstawowe użycie pakietów uwierzytelniania pozostanie bez zmian:</span><span class="sxs-lookup"><span data-stu-id="3861a-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="3861a-104">Klasy pochodzące od dostawców OAuth, takie jak te z [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span><span class="sxs-lookup"><span data-stu-id="3861a-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="3861a-105">Zaawansowane implementacje operowania na żądaniach.</span><span class="sxs-lookup"><span data-stu-id="3861a-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="3861a-106">Aby uzyskać więcej informacji, zobacz [ASPNET/AspNetCore # 7105](https://github.com/aspnet/AspNetCore/pull/7105).</span><span class="sxs-lookup"><span data-stu-id="3861a-106">For more information, see [aspnet/AspNetCore#7105](https://github.com/aspnet/AspNetCore/pull/7105).</span></span> <span data-ttu-id="3861a-107">W przypadku dyskusji zobacz [ASPNET/AspNetCore # 7289](https://github.com/aspnet/AspNetCore/issues/7289).</span><span class="sxs-lookup"><span data-stu-id="3861a-107">For discussion, see [aspnet/AspNetCore#7289](https://github.com/aspnet/AspNetCore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3861a-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="3861a-108">Version introduced</span></span>

<span data-ttu-id="3861a-109">3.0</span><span class="sxs-lookup"><span data-stu-id="3861a-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3861a-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="3861a-110">Recommended action</span></span>

<span data-ttu-id="3861a-111">W przypadku pochodnych implementacji protokołu OAuth najbardziej typową zmianą jest zastąpienie `JObject.Parse` z `JsonDocument.Parse` w przesłonięciu `CreateTicketAsync`, jak pokazano [poniżej](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span><span class="sxs-lookup"><span data-stu-id="3861a-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="3861a-112">`JsonDocument` implementuje `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="3861a-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="3861a-113">Na poniższej liście przedstawiono znane zmiany:</span><span class="sxs-lookup"><span data-stu-id="3861a-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="3861a-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> zmieni się na `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span><span class="sxs-lookup"><span data-stu-id="3861a-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="3861a-115">Wszystkie pochodne implementacje `ClaimAction` mają podobny zakres.</span><span class="sxs-lookup"><span data-stu-id="3861a-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="3861a-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> zmieni się na `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="3861a-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="3861a-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> zmieni się na `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="3861a-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="3861a-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> został usunięty z jednego starego konstruktora, a pozostałe zamieniono `JObject` na `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="3861a-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="3861a-119">Właściwość `User` i Metoda `RunClaimActions` zostały zaktualizowane w celu dopasowania.</span><span class="sxs-lookup"><span data-stu-id="3861a-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="3861a-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> teraz akceptuje parametr typu `JsonDocument` zamiast `JObject`.</span><span class="sxs-lookup"><span data-stu-id="3861a-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="3861a-121">Właściwość `Response` została zaktualizowana w celu dopasowania.</span><span class="sxs-lookup"><span data-stu-id="3861a-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="3861a-122">`OAuthTokenResponse` jest teraz jednorazowy i zostanie usunięty przez `OAuthHandler`.</span><span class="sxs-lookup"><span data-stu-id="3861a-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="3861a-123">Pochodne implementacje OAuth zastępujące `ExchangeCodeAsync` nie muszą zbyć `JsonDocument` lub `OAuthTokenResponse`.</span><span class="sxs-lookup"><span data-stu-id="3861a-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="3861a-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> zmieniono z `JObject` na `JsonDocument`.</span><span class="sxs-lookup"><span data-stu-id="3861a-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="3861a-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> zmieniono z `JObject` na `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="3861a-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="3861a-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> zmieniono z akceptowania `JObject` na `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="3861a-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> changed from accepting `JObject` to `JsonElement`.</span></span>

#### <a name="category"></a><span data-ttu-id="3861a-127">Kategoria</span><span class="sxs-lookup"><span data-stu-id="3861a-127">Category</span></span>

<span data-ttu-id="3861a-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3861a-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3861a-129">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3861a-129">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Authentication.Facebook?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.MicrosoftAccount?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OAuth?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Twitter?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Facebook`
- `N:Microsoft.AspNetCore.Authentication.Google`
- `N:Microsoft.AspNetCore.Authentication.MicrosoftAccount`
- `N:Microsoft.AspNetCore.Authentication.OAuth`
- `N:Microsoft.AspNetCore.Authentication.OpenIdConnect`
- `N:Microsoft.AspNetCore.Authentication.Twitter`

-->
