---
ms.openlocfilehash: 494e792d63a611cdaedf3e40aa607cfbb0420ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901645"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="8241e-101">Uwierzytelnianie: Zastępowane typy Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="8241e-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="8241e-102">W ASP.NET Core 3.0 `Newtonsoft.Json` typy używane w interfejsach API uwierzytelniania zostały zastąpione typami. `System.Text.Json`</span><span class="sxs-lookup"><span data-stu-id="8241e-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="8241e-103">Z wyjątkiem następujących przypadków podstawowe użycie pakietów uwierzytelniania pozostaje nienaruszone:</span><span class="sxs-lookup"><span data-stu-id="8241e-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="8241e-104">Klasy pochodzące od dostawców OAuth, takich jak te z [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span><span class="sxs-lookup"><span data-stu-id="8241e-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="8241e-105">Zaawansowane implementacje manipulacji roszczeniami.</span><span class="sxs-lookup"><span data-stu-id="8241e-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="8241e-106">Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105).</span><span class="sxs-lookup"><span data-stu-id="8241e-106">For more information, see [dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105).</span></span> <span data-ttu-id="8241e-107">Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).</span><span class="sxs-lookup"><span data-stu-id="8241e-107">For discussion, see [dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8241e-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="8241e-108">Version introduced</span></span>

<span data-ttu-id="8241e-109">3.0</span><span class="sxs-lookup"><span data-stu-id="8241e-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8241e-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="8241e-110">Recommended action</span></span>

<span data-ttu-id="8241e-111">W przypadku pochodnych implementacji OAuth najczęstszą `JObject.Parse` `JsonDocument.Parse` zmianą `CreateTicketAsync` jest zastąpienie w zastąpieniu, jak pokazano [poniżej](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span><span class="sxs-lookup"><span data-stu-id="8241e-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="8241e-112">`JsonDocument`implementuje `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="8241e-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="8241e-113">Poniższa lista przedstawia znane zmiany:</span><span class="sxs-lookup"><span data-stu-id="8241e-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="8241e-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType>staje `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`się .</span><span class="sxs-lookup"><span data-stu-id="8241e-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="8241e-115">Dotyczy to podobnie `ClaimAction` wszystkich pochodnych implementacji.</span><span class="sxs-lookup"><span data-stu-id="8241e-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="8241e-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType>Staje się`MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="8241e-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="8241e-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType>Staje się`MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span><span class="sxs-lookup"><span data-stu-id="8241e-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="8241e-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext>miał jeden stary konstruktor `JObject` usunięte, a drugi zastąpiony `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="8241e-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="8241e-119">Właściwość `User` i `RunClaimActions` metoda zostały zaktualizowane do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="8241e-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="8241e-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)>teraz akceptuje parametr typu `JsonDocument` zamiast `JObject`.</span><span class="sxs-lookup"><span data-stu-id="8241e-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="8241e-121">Właściwość `Response` została zaktualizowana do dopasowania.</span><span class="sxs-lookup"><span data-stu-id="8241e-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="8241e-122">`OAuthTokenResponse`jest teraz jednorazowe i zostaną `OAuthHandler`usunięte przez .</span><span class="sxs-lookup"><span data-stu-id="8241e-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="8241e-123">Pochodne implementacje OAuth przesłaniania `ExchangeCodeAsync` nie `JsonDocument` `OAuthTokenResponse`trzeba usuwać lub .</span><span class="sxs-lookup"><span data-stu-id="8241e-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="8241e-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType>zmieniono `JObject` `JsonDocument`z .</span><span class="sxs-lookup"><span data-stu-id="8241e-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="8241e-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType>zmieniono `JObject` `JsonElement`z .</span><span class="sxs-lookup"><span data-stu-id="8241e-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="8241e-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType>zmieniono z `JObject` `JsonElement`akceptacji na .</span><span class="sxs-lookup"><span data-stu-id="8241e-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> changed from accepting `JObject` to `JsonElement`.</span></span>

#### <a name="category"></a><span data-ttu-id="8241e-127">Kategoria</span><span class="sxs-lookup"><span data-stu-id="8241e-127">Category</span></span>

<span data-ttu-id="8241e-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8241e-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8241e-129">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="8241e-129">Affected APIs</span></span>

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
