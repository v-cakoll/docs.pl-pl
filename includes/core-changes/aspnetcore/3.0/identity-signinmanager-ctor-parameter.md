---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901712"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Tożsamość: Konstruktor SignInManager akceptuje nowy parametr

Począwszy od ASP.NET Core 3,0, dodano nowy parametr `IUserConfirmation<TUser>` do konstruktora `SignInManager`. Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

Celem zmiany było dodanie obsługi nowych przepływów poczty e-mail/potwierdzenia w tożsamości.

#### <a name="recommended-action"></a>Zalecane działanie

W przypadku ręcznego konstruowania `SignInManager`Podaj implementację `IUserConfirmation` lub Przechwyć jeden z iniekcji zależności, aby zapewnić.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
