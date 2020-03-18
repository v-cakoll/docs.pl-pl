---
ms.openlocfilehash: 494e792d63a611cdaedf3e40aa607cfbb0420ae4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901645"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>Uwierzytelnianie: Zastępowane typy Newtonsoft.Json

W ASP.NET Core 3.0 `Newtonsoft.Json` typy używane w interfejsach API uwierzytelniania zostały zastąpione typami. `System.Text.Json` Z wyjątkiem następujących przypadków podstawowe użycie pakietów uwierzytelniania pozostaje nienaruszone:

* Klasy pochodzące od dostawców OAuth, takich jak te z [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).
* Zaawansowane implementacje manipulacji roszczeniami.

Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore#7105](https://github.com/dotnet/aspnetcore/pull/7105). Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#7289](https://github.com/dotnet/aspnetcore/issues/7289).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

W przypadku pochodnych implementacji OAuth najczęstszą `JObject.Parse` `JsonDocument.Parse` zmianą `CreateTicketAsync` jest zastąpienie w zastąpieniu, jak pokazano [poniżej](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40). `JsonDocument`implementuje `IDisposable`.

Poniższa lista przedstawia znane zmiany:

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType>staje `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`się . Dotyczy to podobnie `ClaimAction` wszystkich pochodnych implementacji.
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType>Staje się`MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType>Staje się`MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext>miał jeden stary konstruktor `JObject` usunięte, a drugi zastąpiony `JsonElement`. Właściwość `User` i `RunClaimActions` metoda zostały zaktualizowane do dopasowania.
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)>teraz akceptuje parametr typu `JsonDocument` zamiast `JObject`. Właściwość `Response` została zaktualizowana do dopasowania. `OAuthTokenResponse`jest teraz jednorazowe i zostaną `OAuthHandler`usunięte przez . Pochodne implementacje OAuth przesłaniania `ExchangeCodeAsync` nie `JsonDocument` `OAuthTokenResponse`trzeba usuwać lub .
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType>zmieniono `JObject` `JsonDocument`z .
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType>zmieniono `JObject` `JsonElement`z .
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType>zmieniono z `JObject` `JsonElement`akceptacji na .

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
