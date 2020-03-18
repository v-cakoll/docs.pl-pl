---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74101294"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autoryzacja: Przeciążenie AddAuthorization przeniesione do innego zestawu

Podstawowe `AddAuthorization` metody, które były używane `Microsoft.AspNetCore.Authorization` do przebywania w zostały zmienione na `AddAuthorizationCore`. Stare `AddAuthorization` metody nadal istnieją, ale `Microsoft.AspNetCore.Authorization.Policy` są w zestawie zamiast tego. Aplikacje używające obu metod nie powinny mieć wpływu. Należy `Microsoft.AspNetCore.Authorization.Policy` zauważyć, że teraz jest dostarczany w ramach udostępnionych, a nie w pakiecie autonomicznym, jak omówiono w [ramach udostępnionych: zestawy usunięte z microsoft.aspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie
`AddAuthorization`metody istniały `Microsoft.AspNetCore.Authorization`w .

#### <a name="new-behavior"></a>Nowe zachowanie

`AddAuthorization`istnieją metody `Microsoft.AspNetCore.Authorization.Policy`w . `AddAuthorizationCore`to nowa nazwa starych metod.

#### <a name="reason-for-change"></a>Przyczyna zmiany

`AddAuthorization`jest lepszą nazwą metody dodawania wszystkich wspólnych usług potrzebnych do autoryzacji.

#### <a name="recommended-action"></a>Zalecana akcja

Dodaj odwołanie do `Microsoft.AspNetCore.Authorization.Policy` lub `AddAuthorizationCore` zamiast tego użyj.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
