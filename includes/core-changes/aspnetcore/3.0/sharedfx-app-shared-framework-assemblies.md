---
ms.openlocfilehash: a8146db1fb54d63d4716b879ce793f7d817cef59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937283"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>Struktura współużytkowana: zestawy usunięte z aplikacji Microsoft.AspNetCore.App

Począwszy od ASP.NET Core 3.0,`Microsoft.AspNetCore.App`ASP.NET Core shared framework ( ) zawiera tylko zestawy innych firm, które są w pełni rozwinięte, obsługiwane i obsługiwane przez firmę Microsoft.

#### <a name="change-description"></a>Zmień opis

Pomyśl o zmianie jako o przedefiniowaniu granic dla ASP.NET Core "platforma". Współużytkowana struktura będzie [można budować przez nikogo za pośrednictwem usługi GitHub](https://github.com/dotnet/source-build) i będzie nadal oferować istniejące zalety platform współużytkowych .NET Core do aplikacji. Niektóre korzyści obejmują mniejszy rozmiar wdrożenia, scentralizowane stosowanie poprawek i krótszy czas uruchamiania.

W ramach zmiany wprowadzono kilka istotnych przełomowych zmian w . `Microsoft.AspNetCore.App`

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Projekty odwołuje `Microsoft.AspNetCore.App` się `<PackageReference>` za pomocą elementu w pliku projektu.

Ponadto `Microsoft.AspNetCore.App` zawierałnastępujące podskładniki:

- Json.NET`Newtonsoft.Json`( )
- Entity Framework Core (zestawy `Microsoft.EntityFrameworkCore.`poprzedzone )
- Roslyn`Microsoft.CodeAnalysis`( )

#### <a name="new-behavior"></a>Nowe zachowanie

Odwołanie do `Microsoft.AspNetCore.App` nie wymaga `<PackageReference>` już elementu w pliku projektu. Zestaw SDK .NET Core obsługuje `<FrameworkReference>`nowy element o `<PackageReference>`nazwie , który zastępuje użycie .

Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).

Entity Framework Core jest dostarczany jako pakiety NuGet. Ta zmiana wyrównuje model wysyłki ze wszystkimi innymi bibliotekami dostępu do danych w programie .NET. Zapewnia entity framework core najprostszą ścieżkę, aby kontynuować innowacje podczas obsługi różnych platform .NET. Przenoszenie entity framework core z udostępnionej struktury nie ma wpływu na jego stan jako biblioteki opracowanej przez firmę Microsoft, obsługiwane i nadające się do obsługi. [Zasady pomocy technicznej .NET Core](https://www.microsoft.com/net/platform/support-policy) nadal go obejmują.

Json.NET i Entity Framework Core nadal współpracują z ASP.NET Core. Nie zostaną one jednak uwzględnione we wspólnych ramach.

Aby uzyskać więcej informacji, zobacz [Przyszłość JSON w .NET Core 3.0](https://github.com/dotnet/announcements/issues/90). Zobacz również [pełną listę plików binarnych](https://github.com/dotnet/aspnetcore/issues/3755) usuniętych z udostępnionej struktury.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana upraszcza zużycie `Microsoft.AspNetCore.App` i zmniejsza powielanie pakietów NuGet i udostępnionych struktur.

Aby uzyskać więcej informacji na temat motywacji tej zmiany, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="recommended-action"></a>Zalecana akcja

Nie będzie konieczne dla projektów do używania `Microsoft.AspNetCore.App` zestawów w jako pakiety NuGet. Aby uprościć kierowanie i korzystanie z ASP.NET framework shared Core, wiele pakietów NuGet dostarczonych od ASP.NET Core 1.0 nie są już produkowane. Interfejsy API, które zapewniają te pakiety, `Microsoft.AspNetCore.App`są nadal dostępne dla aplikacji przy użyciu do `<FrameworkReference>` . Typowe przykłady interfejsu API obejmują Kestrel, MVC i Razor.

Ta zmiana nie dotyczy wszystkich plików binarnych, do których odwołuje się `Microsoft.AspNetCore.App` ASP.NET Core 2.x. Godne uwagi wyjątki obejmują:

- `Microsoft.Extensions`biblioteki, które nadal są przeznaczone dla programu .NET https://github.com/dotnet/extensions)Standard, będą dostępne jako pakiety NuGet (zobacz .
- Interfejsy API tworzone przez zespół ASP.NET `Microsoft.AspNetCore.App`Core, które nie są częścią pliku . Na przykład następujące składniki są dostępne jako pakiety NuGet:
  - Entity Framework Core
  - Interfejsy API zapewniające integrację innych firm
  - Funkcje eksperymentalne
  - Interfejsy API z zależnościami, które nie mogą [spełnić wymagań, aby być w ramach udostępnionych](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)
- Rozszerzenia do MVC, które utrzymują obsługę Json.NET. Interfejs API zostanie dostarczony jako pakiet NuGet do obsługi przy użyciu Json.NET i MVC.
- Klient SignalR .NET będzie nadal obsługiwać .NET Standard i wysyłać jako pakiet NuGet. Jest przeznaczony do użytku w wielu plikach uruchomieniowych .NET, takich jak Xamarin i UWP.

Aby uzyskać więcej informacji, zobacz [Zatrzymywanie produkcji pakietów dla zestawów udostępnionych w 3.0](https://github.com/dotnet/aspnetcore/issues/3756). Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).

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
