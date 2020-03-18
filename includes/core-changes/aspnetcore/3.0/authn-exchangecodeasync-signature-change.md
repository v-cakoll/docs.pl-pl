---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394282"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>Uwierzytelnianie: Zmieniono podpis programu OAuthHandler ExchangeCodeAsync

W ASP.NET Core 3.0 `OAuthHandler.ExchangeCodeAsync` podpis został zmieniony z:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

Do:

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`code` Ciągi `redirectUri` i zostały przekazane jako oddzielne argumenty.

#### <a name="new-behavior"></a>Nowe zachowanie

`Code`i `RedirectUri` są właściwości, które `OAuthCodeExchangeContext` mogą `OAuthCodeExchangeContext` być ustawione za pomocą konstruktora. Nowy `OAuthCodeExchangeContext` typ jest jedynym argumentem przekazanym do `OAuthHandler.ExchangeCodeAsync`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana umożliwia dodatkowe parametry, które mają być dostarczone w sposób nieprzerywający. Nie ma potrzeby tworzenia `ExchangeCodeAsync` nowych przeciążeń.

#### <a name="recommended-action"></a>Zalecana akcja

Skonstruować `OAuthCodeExchangeContext` z `code` `redirectUri` odpowiednimi i wartości. Należy <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> podać wystąpienie. To `OAuthCodeExchangeContext` pojedyncze wystąpienie można `OAuthHandler.ExchangeCodeAsync` przekazać do zamiast wielu argumentów.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
