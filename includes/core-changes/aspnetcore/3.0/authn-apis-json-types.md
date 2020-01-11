---
ms.openlocfilehash: 494e792d63a611cdaedf3e40aa607cfbb0420ae4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901645"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>Uwierzytelnianie: zamieniono typy Newtonsoft. JSON

W ASP.NET Core 3,0 typy `Newtonsoft.Json` używane w interfejsach API uwierzytelniania zostały zastąpione typami `System.Text.Json`. Z wyjątkiem następujących przypadków podstawowe użycie pakietów uwierzytelniania pozostanie bez zmian:

* Klasy pochodzące od dostawców OAuth, takie jak te z [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).
* Zaawansowane implementacje operowania na żądaniach.

Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore # 7105](https://github.com/dotnet/aspnetcore/pull/7105). Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 7289](https://github.com/dotnet/aspnetcore/issues/7289).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecane działanie

W przypadku pochodnych implementacji protokołu OAuth najbardziej typową zmianą jest zamienienie `JObject.Parse` z `JsonDocument.Parse` w przesłonięciu `CreateTicketAsync`, jak pokazano [poniżej](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40). `JsonDocument` implementuje `IDisposable`.

Na poniższej liście przedstawiono znane zmiany:

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`. Wszystkie pochodne implementacje `ClaimAction` są analogiczne.
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> zostanie `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> zostanie `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> ma jednego starego konstruktora, a pozostałe zamieniono `JObject` z `JsonElement`. Właściwość `User` i Metoda `RunClaimActions` zostały zaktualizowane w celu dopasowania.
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> teraz akceptuje parametr typu `JsonDocument` zamiast `JObject`. Właściwość `Response` została zaktualizowana tak, aby była zgodna. `OAuthTokenResponse` jest teraz jednorazowy i zostanie usunięty przez `OAuthHandler`. W przypadku pochodnych implementacji OAuth zastępowanie `ExchangeCodeAsync` nie trzeba zbyć `JsonDocument` lub `OAuthTokenResponse`.
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> zmienić z `JObject` na `JsonDocument`.
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> zmienić z `JObject` na `JsonElement`.
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> zmienić z akceptowania `JObject` do `JsonElement`.

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
