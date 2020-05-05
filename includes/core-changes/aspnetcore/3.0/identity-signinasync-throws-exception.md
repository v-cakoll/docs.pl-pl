---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394230"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Tożsamość: SignInAsync zgłasza wyjątek dla nieuwierzytelnionej tożsamości

Domyślnie program `SignInAsync` zgłasza wyjątek dla podmiotów zabezpieczeń/tożsamości, w których `IsAuthenticated` jest. `false`

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`SignInAsync`akceptuje wszelkie podmioty zabezpieczeń/tożsamości, w tym tożsamości, `IsAuthenticated` w `false`których jest.

#### <a name="new-behavior"></a>Nowe zachowanie

Domyślnie program `SignInAsync` zgłasza wyjątek dla podmiotów zabezpieczeń/tożsamości, w których `IsAuthenticated` jest. `false` Istnieje nowa flaga, która pozwala pominąć to zachowanie, ale zachowanie domyślne zostało zmienione.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Stare zachowanie było przyczyną problemów, ponieważ domyślnie te podmioty zabezpieczeń zostały odrzucone przez `[Authorize]`  /  `RequireAuthenticatedUser()`.

#### <a name="recommended-action"></a>Zalecana akcja

W ASP.NET Core 3,0 w wersji zapoznawczej 6 `RequireAuthenticatedSignIn` znajduje się `AuthenticationOptions` flaga, `true` która jest domyślnie. Ustaw tę flagę `false` na, aby przywrócić stare zachowanie.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
