---
ms.openlocfilehash: b4499637cd5fff015335e0cdb3c6cf1c3ea6cff0
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637187"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>Uwierzytelnianie: zamieniono typy Newtonsoft. JSON

W ASP.NET Core 3,0 `Newtonsoft.Json` typy używane w interfejsach API uwierzytelniania zostały zastąpione `System.Text.Json` typami. Z wyjątkiem następujących przypadków podstawowe użycie pakietów uwierzytelniania pozostanie bez zmian:

* Klasy pochodzące od dostawców OAuth, takie jak te z [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).
* Zaawansowane implementacje operowania na żądaniach.

Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore # 7105](https://github.com/dotnet/aspnetcore/pull/7105). Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 7289](https://github.com/dotnet/aspnetcore/issues/7289).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

W przypadku pochodnych implementacji protokołu OAuth najbardziej typową zmianą jest `JObject.Parse` zastąpienie `JsonDocument.Parse` w ramach `CreateTicketAsync` przesłonięcia, jak pokazano [tutaj](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40). `JsonDocument`implementuje `IDisposable`.

Na poniższej liście przedstawiono znane zmiany:

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType>zmieni `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`się. Wszystkie implementacje pochodne `ClaimAction` mają podobny zakres.
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType>stanowi`MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType>stanowi`MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext>ma jeden stary Konstruktor, a drugi został zastąpiony `JObject` przez `JsonElement`. `User` Właściwość i `RunClaimActions` Metoda zostały zaktualizowane w celu dopasowania.
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)>teraz akceptuje parametr typu `JsonDocument` , a nie. `JObject` `Response` Właściwość została zaktualizowana tak, aby była zgodna. `OAuthTokenResponse`jest teraz jednorazowe i zostanie usunięty przez `OAuthHandler`. Przesłaniające `ExchangeCodeAsync` implementacje implementacji OAuth nie muszą `JsonDocument` wyprowadzać `OAuthTokenResponse`lub.
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType>zmieniono z `JObject` na `JsonDocument`.
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType>zmieniono z `JObject` na `JsonElement`.
- Ostatni parametr [TwitterHandler. CreateTicketAsync (identyfikator oświadczenia, AuthenticationProperties, AccessToken, JObject)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.authentication.twitter.twitterhandler.createticketasync?view=aspnetcore-2.2#Microsoft_AspNetCore_Authentication_Twitter_TwitterHandler_CreateTicketAsync_System_Security_Claims_ClaimsIdentity_Microsoft_AspNetCore_Authentication_AuthenticationProperties_Microsoft_AspNetCore_Authentication_Twitter_AccessToken_Newtonsoft_Json_Linq_JObject_) został zmieniony z `JObject` na `JsonElement`. Metoda zastępująca to <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,System.Text.Json.JsonElement)?displayProperty=nameWithType>.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

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
