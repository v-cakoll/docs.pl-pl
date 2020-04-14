---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275310"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Tożsamość: Konstruktor SignInManager akceptuje nowy parametr

Począwszy od ASP.NET Core 3.0, `IUserConfirmation<TUser>` nowy parametr `SignInManager` został dodany do konstruktora. Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="reason-for-change"></a>Powód zmiany

Motywacją do zmiany było dodanie wsparcia dla nowych przepływów e-mail / potwierdzenia w tożsamości.

#### <a name="recommended-action"></a>Zalecana akcja

Jeśli ręcznie konstruowania `SignInManager`, zapewnić `IUserConfirmation` implementację lub pobrać jeden z iniekcji zależności, aby zapewnić.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
