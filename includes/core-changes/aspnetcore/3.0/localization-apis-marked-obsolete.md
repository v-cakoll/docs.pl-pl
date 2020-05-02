---
ms.openlocfilehash: d70a8d2a3031a5b3d47ab3fb7f40193dce6e311e
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728333"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Lokalizacja: ResourceManagerWithCultureStringLocalizer i WithCulture oznaczone jako przestarzałe

Klasa [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) i element członkowski interfejsu [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) często są źródłami pomyłek dla użytkowników lokalizacji, szczególnie podczas tworzenia własnej `IStringLocalizer` implementacji. Te elementy dają użytkownikowi wrażenie, że `IStringLocalizer` wystąpienie jest "w języku, na zasób". W rzeczywistości wystąpienia powinny mieć tylko wartość "dla zasobu". Wyszukiwany język jest określany na `CultureInfo.CurrentUICulture` podstawie czasu wykonywania. Aby wyeliminować Źródło pomyłek, interfejsy API zostały oznaczone jako przestarzałe w ASP.NET Core 3,0 wersja zapoznawcza 3. Interfejsy API zostaną usunięte w przyszłej wersji.

W przypadku kontekstu zobacz [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Metody nie zostały oznaczone `Obsolete`jako.

#### <a name="new-behavior"></a>Nowe zachowanie

Metody są oznaczone `Obsolete`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Interfejsy API przedstawiają przypadek użycia, który nie jest zalecany. Wystąpił problem z projektowaniem lokalizacji.

#### <a name="recommended-action"></a>Zalecana akcja

Zaleca się użycie `ResourceManagerStringLocalizer` zamiast tego. Pozwól, aby kultura była ustawiona przez `CurrentCulture`. Jeśli to nie jest opcja, Utwórz i Użyj kopii [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.0)
- [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.0)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
