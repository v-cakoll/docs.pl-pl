---
ms.openlocfilehash: 64e854b06895ca54a9ab9870b85868788a731c00
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549597"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>Współużytkowana struktura: zestawy usunięte z pliku Microsoft.AspNetCore.App

Począwszy od ASP.NET Core 3.0, ASP.NET Core shared`Microsoft.AspNetCore.App`framework ( ) zawiera tylko zestawy innych firm, które są w pełni opracowane, obsługiwane i obsługiwane przez firmę Microsoft.

#### <a name="change-description"></a>Zmień opis

Pomyśl o zmianie jako o przedefiniowaniu granic dla ASP.NET Core "platformy". Współużytkowana struktura będzie [można utworzyć ze źródła przez nikogo za pośrednictwem usługi GitHub](https://github.com/dotnet/source-build) i będzie nadal oferować istniejące korzyści z platform współużytkowych .NET Core dla aplikacji. Niektóre korzyści obejmują mniejszy rozmiar wdrożenia, scentralizowane poprawki i krótszy czas uruchamiania.

W ramach zmiany wprowadza się kilka znaczących istotnych zmian w `Microsoft.AspNetCore.App`.

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Projekty, `Microsoft.AspNetCore.App` do `<PackageReference>` których odwołuje się element w pliku projektu.

`Microsoft.AspNetCore.App` Dodatkowo, zawarte następujące podskładnik:

- Json.NET (`Newtonsoft.Json`)
- Core framework jednostki (zestawy `Microsoft.EntityFrameworkCore.`poprzedzone)
- Roslyn`Microsoft.CodeAnalysis`( )

#### <a name="new-behavior"></a>Nowe zachowanie

Odwołanie do `Microsoft.AspNetCore.App` nie wymaga `<PackageReference>` już elementu w pliku projektu. Zestaw SDK .NET Core obsługuje `<FrameworkReference>`nowy element o `<PackageReference>`nazwie , który zastępuje użycie programu .

Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).

Entity Framework Core jest dostarczany jako pakiety NuGet. Ta zmiana wyrównuje model wysyłki ze wszystkimi innymi bibliotekami dostępu do danych w programie .NET. Zapewnia Entity Framework Core najprostszą ścieżkę do kontynuowania innowacji podczas obsługi różnych platform .NET. Przeniesienie entity framework core z udostępnionej struktury nie ma wpływu na jego stan jako biblioteki opracowanej, obsługiwanej i zbywalnej przez firmę Microsoft. [Zasady pomocy technicznej .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) nadal go obejmują.

Json.NET i Entity Framework Core nadal współpracują z ASP.NET Core. Nie zostaną one jednak uwzględnione we wspólnych ramach.

Aby uzyskać więcej informacji, zobacz [Przyszłość JSON w .NET Core 3.0](https://github.com/dotnet/announcements/issues/90). Zobacz też [pełną listę plików binarnych usuniętych](https://github.com/dotnet/aspnetcore/issues/3755) z udostępnionej struktury.

#### <a name="reason-for-change"></a>Powód zmiany

Ta zmiana upraszcza `Microsoft.AspNetCore.App` zużycie i zmniejsza powielanie między pakietami NuGet i udostępnionych struktur.

Aby uzyskać więcej informacji na temat motywacji do tej zmiany, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="recommended-action"></a>Zalecana akcja

Nie będzie konieczne dla projektów do korzystania `Microsoft.AspNetCore.App` z zestawów w pakietach NuGet. Aby uprościć kierowanie i korzystanie z platformy udostępnionej ASP.NET Core, wiele pakietów NuGet wysłanych od ASP.NET Core 1.0 nie są już produkowane. Interfejsy API, które zapewniają te pakiety, `<FrameworkReference>` `Microsoft.AspNetCore.App`są nadal dostępne dla aplikacji przy użyciu przycisku do . Typowe przykłady interfejsu API obejmują Kestrel, MVC i Razor.

Ta zmiana nie ma zastosowania do wszystkich `Microsoft.AspNetCore.App` plików binarnych, do których odwołuje się ASP.NET Core 2.x. Godne uwagi wyjątki obejmują:

- `Microsoft.Extensions`biblioteki, które nadal są przeznaczone dla platformy .NET https://github.com/dotnet/extensions)Standard, będą dostępne jako pakiety NuGet (zobacz .
- Interfejsy API produkowane przez zespół ASP.NET Core, które `Microsoft.AspNetCore.App`nie są częścią . Na przykład następujące składniki są dostępne jako pakiety NuGet:
  - Entity Framework Core
  - Interfejsy API zapewniające integrację z osobami zewnętrznymi
  - Funkcje eksperymentalne
  - Interfejsy API z zależnościami, które nie mogą [spełniać wymagań, które mają być w ramach udostępnionych](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)
- Rozszerzenia do MVC, które utrzymują obsługę Json.NET. Interfejs API zostanie dostarczony jako pakiet NuGet do obsługi przy użyciu Json.NET i MVC.
- Klient SignalR .NET będzie nadal obsługiwać .NET Standard i wysyłać jako pakiet NuGet. Jest przeznaczony do użytku w wielu środowiskach uruchomieniowych platformy .NET, takich jak platformy Xamarin i platformy uniwersalnej systemu wyurzcie.It's intended for use on many .NET runtimes, such as Xamarin and UWP.

Aby uzyskać więcej informacji, zobacz [Zaprzestanie tworzenia pakietów dla zestawów współużytkowanych struktur w 3.0](https://github.com/dotnet/aspnetcore/issues/3756). Aby do dyskusji, zobacz [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
