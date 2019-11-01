---
ms.openlocfilehash: 74b989a2413d2192f7cf5208e400eaed879ea096
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198524"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Autoryzacja: implementacje IAuthorizationPolicyProvider wymagają nowej metody

W ASP.NET Core 3,0 dodano nową metodę `GetFallbackPolicyAsync` do `IAuthorizationPolicyProvider`. Te zasady powrotu są używane przez oprogramowanie pośredniczące autoryzacji, gdy nie określono zasad.

Aby uzyskać więcej informacji, zobacz [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Implementacje `IAuthorizationPolicyProvider` nie wymagały metody `GetFallbackPolicyAsync`.

#### <a name="new-behavior"></a>Nowe zachowanie

Implementacje `IAuthorizationPolicyProvider` wymagają metody `GetFallbackPolicyAsync`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Nowa metoda była wymagana dla nowego `AuthorizationMiddleware` do użycia, gdy nie określono żadnych zasad.

#### <a name="recommended-action"></a>Zalecana akcja

Dodaj metodę `GetFallbackPolicyAsync` do implementacji `IAuthorizationPolicyProvider`.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
