---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394230"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Tożsamość: SignInAsync zgłasza wyjątek dla nieuwierzytelnionej tożsamości

Domyślnie `SignInAsync` zgłasza wyjątek dla podmiotów zabezpieczeń/tożsamości, w których `IsAuthenticated` jest `false`.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`SignInAsync` akceptuje wszelkie podmioty zabezpieczeń/tożsamości, w tym tożsamości, w których `IsAuthenticated` jest `false`.

#### <a name="new-behavior"></a>Nowe zachowanie

Domyślnie `SignInAsync` zgłasza wyjątek dla podmiotów zabezpieczeń/tożsamości, w których `IsAuthenticated` jest `false`. Istnieje nowa flaga, która pozwala pominąć to zachowanie, ale zachowanie domyślne zostało zmienione.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Stare zachowanie było przyczyną problemów, ponieważ domyślnie te podmioty zabezpieczeń zostały odrzucone przez `[Authorize]` / `RequireAuthenticatedUser()`.

#### <a name="recommended-action"></a>Zalecane działanie

W ASP.NET Core 3,0 w wersji zapoznawczej 6 istnieje flaga `RequireAuthenticatedSignIn` na `AuthenticationOptions` `true` domyślnie. Ustaw tę flagę na `false`, aby przywrócić stare zachowanie.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
