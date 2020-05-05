---
ms.openlocfilehash: 64e854b06895ca54a9ab9870b85868788a731c00
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549597"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>Udostępnione środowisko: zestawy usunięte z Microsoft. AspNetCore. App

Począwszy od ASP.NET Core 3,0, ASP.NET Core Shared Framework (`Microsoft.AspNetCore.App`) zawiera tylko zestawy pierwszej jednostki, które są w pełni opracowane, obsługiwane i udostępniane przez firmę Microsoft.

#### <a name="change-description"></a>Zmień opis

Należy zastanowić się nad zmianą podczas ponownego definiowania granic dla ASP.NET Core "platformy". Udostępniona platforma będzie [budować Źródło przez każdy za pośrednictwem usługi GitHub](https://github.com/dotnet/source-build) i będzie w dalszym ciągu oferować istniejące zalety platformy .NET Core dla aplikacji. Niektóre korzyści obejmują mniejszy rozmiar wdrożenia, scentralizowaną poprawkę i krótszy czas uruchamiania.

W ramach zmiany niektóre istotne zmiany są wprowadzane w `Microsoft.AspNetCore.App`.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Projekty, `Microsoft.AspNetCore.App` `<PackageReference>` do których odwołuje się element w pliku projektu.

Ponadto `Microsoft.AspNetCore.App` zawarte są następujące podskładniki:

- Json.NET (`Newtonsoft.Json`)
- Entity Framework Core (zestawy poprzedzone prefiksem `Microsoft.EntityFrameworkCore.`)
- Roslyn (`Microsoft.CodeAnalysis`)

#### <a name="new-behavior"></a>Nowe zachowanie

Odwołanie do `Microsoft.AspNetCore.App` nie wymaga już `<PackageReference>` elementu w pliku projektu. Zestaw .NET Core SDK obsługuje nowy element o nazwie `<FrameworkReference>`, który zastępuje użycie. `<PackageReference>`

Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore # 3612](https://github.com/dotnet/aspnetcore/issues/3612).

Entity Framework Core są dostarczane jako pakiety NuGet. Ta zmiana powoduje wyrównanie modelu wysyłki do wszystkich innych bibliotek dostępu do danych w programie .NET. Zapewnia Entity Framework Core najprostszą ścieżkę, aby kontynuować innowacje, jednocześnie obsługując różne platformy .NET. Przenoszenie Entity Framework Core z platformy udostępnionej nie ma wpływu na jego stan jako biblioteka opracowana przez firmę Microsoft, którą można obsługiwać. [Zasady pomocy technicznej platformy .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) w dalszym ciągu pokrywają się z nią.

Json.NET i Entity Framework Core Kontynuuj pracę z ASP.NET Core. Nie będą jednak uwzględniane w strukturze udostępnionej.

Aby uzyskać więcej informacji, zobacz [przyszłość JSON w programie .NET Core 3,0](https://github.com/dotnet/announcements/issues/90). Zapoznaj [się również z pełną listą plików binarnych](https://github.com/dotnet/aspnetcore/issues/3755) usuniętych z udostępnionej platformy.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana upraszcza użycie `Microsoft.AspNetCore.App` i zmniejsza duplikowanie między pakietami NuGet i współdzielonymi strukturami.

Aby uzyskać więcej informacji na temat motywacji tej zmiany, zobacz [ten wpis w blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="recommended-action"></a>Zalecana akcja

Nie jest konieczne, aby projekty korzystały z zestawów `Microsoft.AspNetCore.App` w programie jako pakiety NuGet. Aby uprościć Określanie elementów docelowych i użycie ASP.NET Core udostępnionej platformy, wiele pakietów NuGet dostarczonych od ASP.NET Core 1,0 nie jest już generowanych. Interfejsy API udostępniane przez te pakiety są nadal dostępne dla aplikacji za pomocą `<FrameworkReference>` programu `Microsoft.AspNetCore.App`do. Typowe przykłady interfejsów API to Kestrel, MVC i Razor.

Ta zmiana nie ma zastosowania do wszystkich plików binarnych, do których odwołuje się `Microsoft.AspNetCore.App` w ASP.NET Core 2. x. Do istotnych wyjątków należą:

- `Microsoft.Extensions`biblioteki, które przejdźą do .NET Standard będą dostępne jako pakiety NuGet (patrz https://github.com/dotnet/extensions).
- Interfejsy API produkowane przez zespół ASP.NET Core, które nie są `Microsoft.AspNetCore.App`częścią programu. Na przykład następujące składniki są dostępne jako pakiety NuGet:
  - Entity Framework Core
  - Interfejsy API zapewniające integrację innych firm
  - Funkcje eksperymentalne
  - Interfejsy API z zależnościami, które nie mogą [spełnić wymagań, które mają być zawarte w strukturze udostępnionej](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)
- Rozszerzenia MVC obsługujące obsługę Json.NET. Interfejs API zostanie dostarczony jako pakiet NuGet do obsługi Json.NET i MVC.
- Klient platformy .NET sygnalizujący będzie nadal obsługiwał .NET Standard i dostarczać jako pakiet NuGet. Jest ona przeznaczona do użycia w wielu środowiskach uruchomieniowych platformy .NET, takich jak Xamarin i platformy UWP.

Aby uzyskać więcej informacji, zobacz sekcję [Zatrzymaj tworzenie pakietów dla zestawów udostępnionych struktur w 3,0](https://github.com/dotnet/aspnetcore/issues/3756). Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 3757](https://github.com/dotnet/aspnetcore/issues/3757).

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
