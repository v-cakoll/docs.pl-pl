---
ms.openlocfilehash: 8cb0aca991f5adfe4561ef56090cb9f7b2e56283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902013"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a>Lokalizacja: ResourceManagerWithCultureStringLocalizer i WithCulture oznaczone jako przestarzałe

[Klasa ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) i element członkowski interfejsu [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) są często źródłem `IStringLocalizer` pomyłek dla użytkowników lokalizacji, szczególnie podczas tworzenia własnej implementacji. Te elementy dają użytkownikowi wrażenie, że wystąpienie `IStringLocalizer` jest "na język, na zasób". W rzeczywistości wystąpienia powinny być tylko "na zasób". Język wyszukiwany jest określana przez `CultureInfo.CurrentUICulture` w czasie wykonywania. Aby wyeliminować źródło zamieszania, interfejsy API zostały oznaczone jako przestarzałe w ASP.NET Core 3.0 Preview 3. Interfejsy API zostaną usunięte w przyszłej wersji.

Dla kontekstu zobacz [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324). Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Metody nie zostały oznaczone `Obsolete`jako .

#### <a name="new-behavior"></a>Nowe zachowanie

Metody są `Obsolete`oznaczone .

#### <a name="reason-for-change"></a>Przyczyna zmiany

Interfejsy API reprezentowałprzypadek użycia, który nie jest zalecane. Nie było zamieszania co do projektu lokalizacji.

#### <a name="recommended-action"></a>Zalecana akcja

Zaleca się zamiast `ResourceManagerStringLocalizer` tego użyć. Niech kultura być `CurrentCulture`ustawione przez . Jeśli nie jest to opcja, utwórz i użyj kopii [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).

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
