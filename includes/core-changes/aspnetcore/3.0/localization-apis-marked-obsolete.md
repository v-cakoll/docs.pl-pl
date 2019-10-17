---
ms.openlocfilehash: da1ec7908b3082fc61313cb805773aa600bc1b5d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394420"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Lokalizacja: ResourceManagerWithCultureStringLocalizer i WithCulture oznaczone jako przestarzałe

Klasa [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) i element członkowski interfejsu [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) często są źródłami pomyłek dla użytkowników lokalizacji, szczególnie podczas tworzenia własnej implementacji `IStringLocalizer`. Te elementy dają użytkownikowi wrażenie, że wystąpienie `IStringLocalizer` ma wartość "w poszczególnych językach". W rzeczywistości wystąpienia powinny mieć tylko wartość "dla zasobu". Wyszukiwany język jest określany przez `CultureInfo.CurrentUICulture` w czasie wykonywania. Aby wyeliminować Źródło pomyłek, interfejsy API zostały oznaczone jako przestarzałe w ASP.NET Core 3,0 wersja zapoznawcza 3. Interfejsy API zostaną usunięte w przyszłej wersji.

W przypadku kontekstu zobacz [ASPNET/AspNetCore # 3324](https://github.com/aspnet/AspNetCore/issues/3324). W przypadku dyskusji zobacz [ASPNET/AspNetCore # 7756](https://github.com/aspnet/AspNetCore/issues/7756).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Metody nie zostały oznaczone jako `Obsolete`.

#### <a name="new-behavior"></a>Nowe zachowanie

Metody są oznaczone `Obsolete`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Interfejsy API przedstawiają przypadek użycia, który nie jest zalecany. Wystąpił problem z projektowaniem lokalizacji.

#### <a name="recommended-action"></a>Zalecana akcja

Zaleca się używanie `ResourceManagerStringLocalizer` zamiast. Pozwól, aby kultura była ustawiona przez `CurrentCulture`. Jeśli to nie jest opcja, Utwórz i Użyj kopii [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

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
