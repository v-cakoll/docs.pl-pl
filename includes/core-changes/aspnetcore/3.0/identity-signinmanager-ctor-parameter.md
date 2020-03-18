---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901712"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Tożsamość: Konstruktor SignInManager akceptuje nowy parametr

Począwszy od ASP.NET Core 3.0, `IUserConfirmation<TUser>` nowy `SignInManager` parametr został dodany do konstruktora. Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="reason-for-change"></a>Przyczyna zmiany

Motywacją do zmiany było dodanie obsługi nowych przepływów e-mail / potwierdzenie w tożsamości.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli ręcznie konstruowanie `SignInManager`, należy `IUserConfirmation` podać implementację lub pobrać jeden z iniekcji zależności, aby zapewnić.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
