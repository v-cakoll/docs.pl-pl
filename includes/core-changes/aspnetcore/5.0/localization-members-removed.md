---
ms.openlocfilehash: 6deeb7debce9b731f3871b7de0ad8df8a8cdafea
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728293"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a>Lokalizacja: Usunięto klasę ResourceManagerWithCultureStringLocalizer i element członkowski interfejsu WithCulture

Klasa [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) i Metoda [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) zostały usunięte w programie .NET 5,0 Preview 1.

W przypadku kontekstu zobacz [ASPNET/anonse # 346](https://github.com/aspnet/Announcements/issues/346) i [dotnet/aspnetcore # 3324](https://github.com/dotnet/aspnetcore/issues/3324). Aby uzyskać więcej dyskusji na temat tej zmiany, zobacz [dotnet/aspnetcore # 7756](https://github.com/dotnet/aspnetcore/issues/7756).

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 1

#### <a name="old-behavior"></a>Stare zachowanie

`ResourceManagerWithCultureStringLocalizer` Klasa i `ResourceManagerStringLocalizer.WithCulture` Metoda są [przestarzałe w programie .NET Core 3,0 w wersji zapoznawczej 3 i nowszych](/dotnet/core/compatibility/2.2-3.0#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).

#### <a name="new-behavior"></a>Nowe zachowanie

`ResourceManagerWithCultureStringLocalizer` Klasa i `ResourceManagerStringLocalizer.WithCulture` Metoda zostały usunięte w programie .NET 5,0 Preview 1. Aby uzyskać spis zmian wprowadzonych w programie, zobacz żądanie ściągnięcia w programie [dotnet/Extensions # 2562](https://github.com/dotnet/extensions/pull/2562/files).

#### <a name="reason-for-change"></a>Przyczyna zmiany

Metody [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) i [ResourceManagerStringLocalizer. WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) często są źródłami pomyłek dla użytkowników lokalizacji. Pomyłka była szczególnie wysoka podczas tworzenia niestandardowej <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementacji. Ta klasa i Metoda zapewniają konsumentom wrażenie, że `IStringLocalizer` wystąpienie jest oczekiwane na "dla poszczególnych zasobów". W rzeczywistości wystąpienie powinno mieć tylko wartość "dla zasobu". W czasie wykonywania <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> Właściwość określa język, który ma być używany.

#### <a name="recommended-action"></a>Zalecana akcja

Zatrzymaj korzystanie z `ResourceManagerWithCultureStringLocalizer` klasy i `ResourceManagerStringLocalizer.WithCulture` metody.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
