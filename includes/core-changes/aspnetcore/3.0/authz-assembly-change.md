---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74101294"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Autoryzacja: Przeciążenie metody addauthorization przeniesiono do innego zestawu

Nazwy podstawowych metod `AddAuthorization`, które były używane do znajdowania w `Microsoft.AspNetCore.Authorization`, zostały zmienione na `AddAuthorizationCore`. Stare metody `AddAuthorization` nadal istnieją, ale znajdują się w zestawie `Microsoft.AspNetCore.Authorization.Policy`. Aplikacje korzystające z obu tych metod powinny nie mieć wpływu. Należy pamiętać, że `Microsoft.AspNetCore.Authorization.Policy` teraz jest dostarczany w środowisku współdzielonym, a nie jako pakiet autonomiczny, zgodnie z opisem w temacie [Shared Framework: zestawy usunięte z Microsoft. AspNetCore. app](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).

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
