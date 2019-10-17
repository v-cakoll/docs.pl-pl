---
ms.openlocfilehash: 65bac44c84589fb55d2b04c39088c2825c451a6b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393922"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autoryzacja: Przeciążenie metody addauthorization przeniesiono do innego zestawu

Nazwy podstawowych metod `AddAuthorization`, które były używane do znajdowania w `Microsoft.AspNetCore.Authorization`, zostały zmienione na `AddAuthorizationCore`. Nadal istnieją stare metody `AddAuthorization`, ale w pakiecie `Microsoft.AspNetCore.Authorization.Policy`. Aplikacje korzystające z obu tych metod powinny nie mieć wpływu. Aplikacje, które nie korzystały z pakietu zasad, muszą przełączać się do korzystania z `AddAuthorizationCore`.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Metody `AddAuthorization` istniały w `Microsoft.AspNetCore.Authorization`.

#### <a name="new-behavior"></a>Nowe zachowanie

Metody `AddAuthorization` istnieją w `Microsoft.AspNetCore.Authorization.Policy`. `AddAuthorizationCore` to nowa nazwa dla starych metod.

#### <a name="reason-for-change"></a>Przyczyna zmiany

`AddAuthorization` to lepsza nazwa metody do dodawania wszystkich typowych usług wymaganych do autoryzacji.

#### <a name="recommended-action"></a>Zalecana akcja

Dodaj odwołanie do `Microsoft.AspNetCore.Authorization.Policy` lub użyj `AddAuthorizationCore`.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
