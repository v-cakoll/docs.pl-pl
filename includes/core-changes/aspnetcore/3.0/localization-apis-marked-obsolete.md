---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902013"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Lokalizacja: ResourceManagerWithCultureStringLocalizer i WithCulture oznaczone jako przestarzałe

Klasa [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) i element członkowski interfejsu [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) często są źródłami pomyłek dla użytkowników lokalizacji, szczególnie podczas tworzenia własnych implementacji `IStringLocalizer`. Te elementy dają użytkownikowi wrażenie, że wystąpienie `IStringLocalizer` ma wartość "w poszczególnych językach". W rzeczywistości wystąpienia powinny mieć tylko wartość "dla zasobu". Wyszukiwany język jest określany przez `CultureInfo.CurrentUICulture` w czasie wykonywania. Aby wyeliminować Źródło pomyłek, interfejsy API zostały oznaczone jako przestarzałe w ASP.NET Core 3,0 wersja zapoznawcza 3. Interfejsy API zostaną usunięte w przyszłej wersji.

W przypadku kontekstu zobacz [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Metody nie zostały oznaczone jako `Obsolete`.

#### <a name="new-behavior"></a>Nowe zachowanie

Metody są oznaczone `Obsolete`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Interfejsy API przedstawiają przypadek użycia, który nie jest zalecany. Wystąpił problem z projektowaniem lokalizacji.

#### <a name="recommended-action"></a>Zalecane działanie

Zaleca się użycie `ResourceManagerStringLocalizer` zamiast tego. Pozwól, aby kultura była ustawiona przez `CurrentCulture`. Jeśli to nie jest opcja, Utwórz i Użyj kopii [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
