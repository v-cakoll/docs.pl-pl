---
title: Analizowanie zależności w kodzie portu do programu .NET Core
description: Dowiedz się, jak analizować zależności zewnętrzne w celu przenoszenia projektu z .NET Framework do programu .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 36d1c1d2090a0fb9e6f48fe519d15897579df2d5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521472"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>Analizowanie zależności w kodzie portu do programu .NET Core

Aby przenieść kod do programu .NET Core lub .NET Standard, musisz zrozumieć zależności. Zależności zewnętrzne to [pakiety NuGet](#analyze-referenced-nuget-packages-in-your-projects) lub [biblioteki DLL](#analyze-dependencies-that-arent-nuget-packages) , do których odwołuje się w projekcie, ale nie są kompilowane. Oceń każdą zależność i opracowuj plan awaryjny dla tych, które nie są zgodne z platformą .NET Core. Oto jak ustalić, czy zależność jest zgodna z platformą .NET Core.

## <a name="analyze-referenced-nuget-packages-in-your-projects"></a>Analizowanie przywoływanych pakietów NuGet w projektach

W przypadku odwoływania się do pakietów NuGet w projekcie należy sprawdzić, czy są one zgodne z platformą .NET Core.
Istnieją dwa sposoby osiągnięcia tego:

- [Korzystanie z aplikacji Eksplorator pakietów NuGet](#analyze-nuget-packages-using-nuget-package-explorer)
- [Korzystanie z witryny nuget.org](#analyze-nuget-packages-using-nugetorg)

Po przeanalizowaniu pakietów, jeśli nie są zgodne z platformą .NET Core i są przeznaczone tylko dla .NET Framework, można sprawdzić, czy [.NET Framework tryb zgodności](#net-framework-compatibility-mode) może ułatwić proces przenoszenia.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analizowanie pakietów NuGet przy użyciu Eksploratora pakietów NuGet

Pakiet NuGet jest samym zestawem folderów, które zawierają zestawy specyficzne dla platformy. Należy sprawdzić, czy w pakiecie znajduje się folder zawierający zgodny zestaw.

Najprostszym sposobem sprawdzenia folderów pakietów NuGet jest użycie narzędzia [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) . Po zainstalowaniu programu wykonaj następujące kroki, aby wyświetlić nazwy folderów:

1. Otwórz Eksploratora pakietów NuGet.
2. Kliknij pozycję **Otwórz pakiet ze źródła online**.
3. Wyszukaj nazwę pakietu.
4. Wybierz nazwę pakietu z wyników wyszukiwania, a następnie kliknij przycisk **Otwórz**.
5. Rozwiń folder *lib* po prawej stronie i Sprawdź nazwy folderów.

Poszukaj folderu z dowolną z następujących nazw:

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
netcoreapp2.1
netcoreapp2.2
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Te wartości są [monikerami struktury docelowej (TFMs)](../../standard/frameworks.md) , które są mapowane na wersje [.NET Standard](../../standard/net-standard.md), .NET Core i tradycyjnych profilów biblioteki klas przenośnych (PCL), które są zgodne z platformą .NET Core.

> [!IMPORTANT]
> Podczas przeglądania TFMs, który obsługuje pakiet, należy pamiętać, że `netcoreapp*`, chociaż jest zgodny, jest przeznaczony tylko dla projektów .NET Core, a nie dla projektów .NET Standard.
> Biblioteka przeznaczona tylko dla `netcoreapp*` i nie `netstandard*` może być używana przez inne aplikacje platformy .NET Core.

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analizowanie pakietów NuGet przy użyciu nuget.org

Alternatywnie można zobaczyć TFMs, że każdy pakiet obsługuje w [NuGet.org](https://www.nuget.org/) w sekcji **zależności** strony pakietu.

Chociaż korzystanie z lokacji jest łatwiejsze w celu sprawdzenia zgodności, informacje o **zależnościach** nie są dostępne w lokacji dla wszystkich pakietów.

### <a name="net-framework-compatibility-mode"></a>.NET Framework tryb zgodności

Po przeanalizowaniu pakietów NuGet może się okazać, że są one przeznaczone tylko do .NET Framework, jak większość pakietów NuGet.

Począwszy od .NET Standard 2,0, wprowadzono .NET Framework tryb zgodności. Ten tryb zgodności umożliwia projektom .NET Standard i .NET Core odwoływanie się do bibliotek .NET Framework. Odwoływanie się do bibliotek .NET Framework nie działa dla wszystkich projektów, takich jak jeśli biblioteka używa interfejsów API Windows Presentation Foundation (WPF), ale odblokowuje wiele scenariuszy przenoszenia.

W przypadku odwoływania się do pakietów NuGet, które są przeznaczone dla .NET Framework w projekcie, takich jak [Huitian. PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), otrzymujesz ostrzeżenie powrotu do pakietu ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) podobne do następującego przykładu:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

To ostrzeżenie jest wyświetlane, gdy dodajesz pakiet i za każdym razem, gdy kompilujesz, aby upewnić się, że ten pakiet został przetestowany z projektem. Jeśli projekt działa zgodnie z oczekiwaniami, możesz pominąć to ostrzeżenie, edytując właściwości pakietu w Visual Studio lub edytując plik projektu ręcznie w ulubionym edytorze kodu.

Aby pominąć ostrzeżenie przez edytowanie pliku projektu, Znajdź wpis `PackageReference` dla pakietu, dla którego chcesz pominąć ostrzeżenie, i Dodaj atrybut `NoWarn`. Atrybut `NoWarn` akceptuje rozdzieloną przecinkami listę wszystkich identyfikatorów ostrzeżeń. Poniższy przykład pokazuje, jak pominąć `NU1701` Ostrzeżenie dla pakietu `Huitian.PowerCollections`, edytując plik projektu ręcznie:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Aby uzyskać więcej informacji na temat pomijania ostrzeżeń kompilatora w programie Visual Studio, zobacz [pomijanie ostrzeżeń dla pakietów NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).

## <a name="port-your-packages-to-packagereference"></a>Przenoszenie pakietów do `PackageReference`

Program .NET Core używa [PackageReference](/nuget/consume-packages/package-references-in-project-files) , aby określić zależności pakietów. Jeśli używasz [pliku Packages. config](/nuget/reference/packages-config) do określania pakietów, musisz przekonwertować go na `PackageReference`.

Więcej informacji można znaleźć w części [Migrowanie z pliku Packages. config do PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Co zrobić, gdy zależność pakietu NuGet nie jest uruchamiana na platformie .NET Core

Istnieje kilka rzeczy, które można wykonać, jeśli pakiet NuGet, od którego jest zależny, nie jest uruchamiany w programie .NET Core:

1. Jeśli projekt jest typu open source, który jest hostowany w witrynie GitHub, możesz bezpośrednio przyangażować deweloperów.
2. Można skontaktować się z autorem bezpośrednio w witrynie [NuGet.org](https://www.nuget.org/). Wyszukaj pakiet, a następnie kliknij pozycję **skontaktuj się z właścicielem** po lewej stronie pakietu.
3. Możesz wyszukać inny pakiet uruchomiony w programie .NET Core, który wykonuje to samo zadanie co używany pakiet.
4. Możesz spróbować napisać kod, który pakiet wykonywał.
5. Możesz wyeliminować zależność od pakietu, zmieniając funkcjonalność aplikacji, co najmniej do momentu udostępnienia zgodnej wersji pakietu.

Pamiętaj, że obsłudze projektów open source i wydawcy pakietów NuGet często są ochotnikami. Przyczyniają się one do tego, że zadbają o daną domenę, wykonują ją bezpłatnie i często mają inne zadania dzienne. Należy więc wiedzieć, że podczas kontaktowania się z nimi w celu uzyskania pomocy technicznej dla platformy .NET Core.

Jeśli nie możesz rozwiązać problemu przy użyciu któregokolwiek z powyższych, być może trzeba będzie przenieść port do programu .NET Core w późniejszym terminie.

Zespół platformy .NET chce wiedzieć, które biblioteki są najważniejsze do obsługi platformy .NET Core. Możesz wysłać wiadomość e-mail w celu dotnet@microsoft.com informacji o bibliotekach, których chcesz użyć.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analizowanie zależności, które nie są pakietami NuGet

Może istnieć zależność, która nie jest pakietem NuGet, taka jak biblioteka DLL w systemie plików. Jedynym sposobem określenia przenośności tej zależności jest uruchomienie narzędzia [analizatora przenośności platformy .NET](https://github.com/Microsoft/dotnet-apiport) . Narzędzie może analizować zestawy przeznaczone dla .NET Framework i identyfikować interfejsy API, które nie są przenośne na inne platformy .NET, takie jak .NET Core. Narzędzie można uruchomić jako aplikację konsolową lub jako [rozszerzenie programu Visual Studio](../../standard/analyzers/portability-analyzer.md).

>[!div class="step-by-step"]
>[Next](libraries.md)
