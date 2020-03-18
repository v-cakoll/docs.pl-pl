---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394230"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Tożsamość: SignInAsync zgłasza wyjątek dla nieuwierzytelnionej tożsamości

Domyślnie `SignInAsync` zgłasza wyjątek dla podmiotów /tożsamości, `IsAuthenticated` w `false`których jest .

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

`SignInAsync`akceptuje wszelkie podmioty/tożsamości, w tym `IsAuthenticated` tożsamości, w których jest `false`.

#### <a name="new-behavior"></a>Nowe zachowanie

Domyślnie `SignInAsync` zgłasza wyjątek dla podmiotów /tożsamości, `IsAuthenticated` w `false`których jest . Istnieje nowa flaga, aby pominąć to zachowanie, ale domyślne zachowanie uległo zmianie.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Stare zachowanie było problematyczne, ponieważ domyślnie podmioty `[Authorize]`  /  `RequireAuthenticatedUser()`te zostały odrzucone przez .

#### <a name="recommended-action"></a>Zalecana akcja

W ASP.NET Core 3.0 Preview 6 `RequireAuthenticatedSignIn` jest `AuthenticationOptions` `true` domyślnie flaga. Ustaw tę `false` flagę, aby przywrócić stare zachowanie.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
