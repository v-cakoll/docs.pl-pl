---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394282"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a>Uwierzytelnianie: OAuthHandler ExchangeCodeAsync zmieniono sygnaturę

W ASP.NET Core 3,0 sygnatura `OAuthHandler.ExchangeCodeAsync` została zmieniona z:

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

Ciągi `code` i `redirectUri` zostały przekazane jako oddzielne argumenty.

#### <a name="new-behavior"></a>Nowe zachowanie

`Code`i `RedirectUri` są właściwościami `OAuthCodeExchangeContext` , które można ustawić za pośrednictwem `OAuthCodeExchangeContext` konstruktora. Nowy `OAuthCodeExchangeContext` typ jest jedynym argumentem przesłanym do `OAuthHandler.ExchangeCodeAsync`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana pozwala na dostarczenie dodatkowych parametrów w sposób rozdzielny. Nie ma potrzeby tworzenia nowych `ExchangeCodeAsync` przeciążeń.

#### <a name="recommended-action"></a>Zalecana akcja

Utwórz `OAuthCodeExchangeContext` z odpowiednimi `code` wartościami i. `redirectUri` Należy <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> podać wystąpienie. To pojedyncze `OAuthCodeExchangeContext` wystąpienie można przesłać `OAuthHandler.ExchangeCodeAsync` zamiast wielu argumentów.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
