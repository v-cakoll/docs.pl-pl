---
ms.openlocfilehash: a16d443a37fb0bb5f6bdc4a39e7dcb4f91c54ead
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394245"
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
