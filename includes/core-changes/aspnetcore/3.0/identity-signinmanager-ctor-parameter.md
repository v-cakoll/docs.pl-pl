---
ms.openlocfilehash: 56b394c4698f60baeb70d3c17d1abee5d867deb7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394063"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Tożsamość: Konstruktor SignInManager akceptuje nowy parametr

Począwszy od ASP.NET Core 3,0, dodano nowy parametr `IUserConfirmation<TUser>` do konstruktora `SignInManager`. Aby uzyskać więcej informacji, zobacz [ASPNET/AspNetCore # 8356](https://github.com/aspnet/AspNetCore/issues/8356).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

Celem zmiany było dodanie obsługi nowych przepływów poczty e-mail/potwierdzenia w tożsamości.

#### <a name="recommended-action"></a>Zalecana akcja

W przypadku ręcznego konstruowania `SignInManager` wprowadź implementację `IUserConfirmation` lub Przechwyć jeden z iniekcji zależności, aby zapewnić.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
