---
title: Analizowanie zależności kodu portów w celu platformy .NET Core
description: Dowiedz się, jak analizować zależnościami zewnętrznymi w celu portu projekty w programie .NET Framework i .NET Core.
author: cartermp
ms.date: 12/04/2018
ms.custom: seodec18
ms.openlocfilehash: dce8e6cd4986b15cf926154b378964db4beef398
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170330"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>Analizowanie zależności kodu portów w celu platformy .NET Core

Do portu kodu platformy .NET Core lub .NET Standard, należy zrozumieć zależności. Zależności zewnętrzne to [pakiety NuGet](#analyze-referenced-nuget-packages-on-your-project) lub [biblioteki dll](#analyze-dependencies-that-arent-nuget-packages) odwołania w projekcie, ale nie kompilacji. Oceń poszczególne zależności i opracować plan awaryjny te, które nie są zgodne z platformą .NET Core. Poniżej przedstawiono sposób ustalić, czy zależność jest zgodna z platformą .NET Core.

## <a name="analyze-referenced-nuget-packages-in-your-projects"></a>Analizowanie odwołania pakietów NuGet w projektach

Jeśli odwołujesz pakietów NuGet w projekcie, należy sprawdzić, jeśli są one zgodne z platformą .NET Core.
Istnieją dwa sposoby, aby to zrobić:

* [Za pomocą narzędzia NuGet Tworzenie pakietu aplikacji Eksploratora](#analyze-nuget-packages-using-nuget-package-explorer)
* [Przy użyciu witryny nuget.org](#analyze-nuget-packages-using-nugetorg)

Po przeanalizowaniu pakietów, jeśli tak nie jest zgodny z platformy .NET Core i docelowego środowiska .NET Framework, można sprawdzić Jeśli [.NET Framework w trybie zgodności](#net-framework-compatibility-mode) może pomóc w procesie przenoszenia.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analiza pakietów NuGet za pomocą Eksploratora pakietów NuGet

Pakiet NuGet jest zestaw folderów, które zawierają zestawy specyficzne dla platformy. Zatem należy sprawdzić, czy istnieje folder, który zawiera zestaw zgodnych wewnątrz pakietu.

Najprostszym sposobem Sprawdź foldery pakietu NuGet jest użycie [Eksplorator pakietów NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) narzędzia. Po zainstalowaniu, należy użyć następujących kroków, aby wyświetlić nazwy folderów:

1. Otwórz Eksplorator pakietów NuGet.
2. Kliknij przycisk **Otwórz pakiet z kanału informacyjnego online**.
3. Wyszukaj nazwę pakietu.
4. Wybierz nazwę pakietu w wynikach wyszukiwania, a następnie kliknij przycisk **Otwórz**.
5. Rozwiń *lib* folderu na po prawej stronie i spójrz na nazwy folderu.

Zwróć uwagę na folder z dowolnymi z następujących nazw:

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

Te wartości są [Target Framework monikerów (krótkich nazw)](../../standard/frameworks.md) mapowania wersje [.NET Standard](../../standard/net-standard.md), .NET Core i tradycyjne profile biblioteki klas przenośnych (PCL), które są zgodne z platformą .NET Core.

> [!IMPORTANT]
> Po wyświetleniu krótkich nazw, obsługiwanych przez pakiet, należy pamiętać, że `netcoreapp*`, podczas gdy zgodne, jest tylko dla projektów .NET Core, a nie projektów .NET Standard.
> Biblioteki, który jest przeznaczony tylko dla `netcoreapp*` i nie `netstandard*` mogą być używane tylko przez inne aplikacje platformy .NET Core.

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analizowanie pakietów NuGet za pomocą nuget.org

Możesz również zapoznać się krótkich nazw, obsługiwanych przez każdy pakiet na [nuget.org](https://www.nuget.org/) w obszarze **zależności** części pakietu.

Mimo że za pomocą witryny jest łatwiejszy sposób sprawdzić zgodność, **zależności** informacje nie są dostępne w witrynie dla wszystkich pakietów.

### <a name="net-framework-compatibility-mode"></a>Tryb zgodności w programie .NET framework

Po przeanalizowaniu pakietów NuGet, może się okazać że ich tylko dla środowiska .NET Framework, tak jak większość pakietów NuGet.

Począwszy od .NET Standard 2.0 wprowadzono tryb zgodności w programie .NET Framework. Ten tryb zgodności umożliwia projektów .NET Standard i .NET Core odwoływać się do bibliotek .NET Framework. Odwołujące się do bibliotek .NET Framework nie działa dla wszystkich projektów, takich jak if biblioteki korzysta z Windows Presentation Foundation (WPF) interfejsów API, ale go odblokować wiele scenariuszy przenoszenia.

Gdy odwołujesz się pakiety NuGet dla środowiska .NET Framework w projekcie, takie jak [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), zostanie wyświetlone ostrzeżenie rezerwowego pakietu ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) podobny do poniższego przykładu:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Tego ostrzeżenie jest wyświetlane, gdy dodasz pakiet za każdym razem, gdy tworzysz, aby upewnić się, testowanie tego pakietu z projektem. Jeśli projekt działa zgodnie z oczekiwaniami, możesz pominąć tego ostrzeżenia, edytując właściwości pakietu w programie Visual Studio lub ręcznie, edytując plik projektu w wybrany edytor kodu.

Aby pominąć to ostrzeżenie, edytując plik projektu, znaleźć `PackageReference` wpis dla pakietu, którą chcesz pominąć ostrzeżenia dla, a następnie dodaj `NoWarn` atrybutu. `NoWarn` Atrybutu akceptuje rozdzielaną przecinkami listę wszystkie ostrzeżenia identyfikatorów. Poniższy przykład pokazuje, jak pomijanie `NU1701` ostrzeżenia dla `Huitian.PowerCollections` pakietu, ręcznie edytując plik projektu:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Aby uzyskać więcej informacji na temat sposobu pomijanie ostrzeżeń kompilatora w programie Visual Studio, zobacz [pomijanie ostrzeżeń dla pakietów NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).

### <a name="port-your-packages-to-packagereference"></a>Pakietów do portu `PackageReference`

Korzysta z platformy .NET core [PackageReference](/nuget/consume-packages/package-references-in-project-files) do określania zależności pakietów. Jeśli używasz [packages.config](/nuget/reference/packages-config) do określenia pakietów, musisz przekonwertować za pośrednictwem `PackageReference`.

Dowiedz się więcej na [migracja z pliku packages.config na PackageReference](/nuget/reference/migrate-packages-config-to-package-reference).

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Co zrobić, gdy Twoje zależności pakietów NuGet nie zostanie uruchomiona na platformie .NET Core

Istnieje kilka rzeczy, które można zrobić, jeśli pakiet NuGet, których zależysz nie działa na platformie .NET Core:

1. Jeśli projekt jest typu open source i hostowany takich jak GitHub, deweloperzy mogą angażować bezpośrednio.
2. Możesz skontaktować się bezpośrednio na autora [nuget.org](https://www.nuget.org/). Wyszukaj pakiet, a następnie kliknij przycisk **skontaktuj się z właścicielami** po lewej stronie strony pakietu.
3. Możesz wyszukać inny pakiet, który działa na platformie .NET Core, która w ramach tego samego zadania jako pakiet, który był używany.
4. Możesz spróbować napisać kod, który pakiet wykonywanych samodzielnie.
5. Można wyeliminować zależność od pakietu, zmieniając działaniem aplikacji, co najmniej do momentu udostępnienia zgodnej wersji pakietu.

Należy pamiętać, że maintainers projektu open-source i wydawców pakietu NuGet często ochotników. Przyczyniają się, ponieważ o danej domeny, to zrobić za darmo i często mają różne zadania dziennych. Dlatego należy w trosce o tym, że podczas kontaktowania się z ich poprosić o obsłudze programu .NET Core.

Jeśli nie możesz rozwiązać problemu z powyższych elementów, może być konieczne port platformy .NET Core w późniejszym terminie.

Zespół .NET chce wiedzieć, które biblioteki są najważniejsze dla pomocy technicznej za pomocą programu .NET Core. Możesz wysłać wiadomość e-mail na adres dotnet@microsoft.com o bibliotekach, o których chcesz użyć.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analizowanie zależności, które nie są pakiety NuGet

Może mieć zależność, która nie jest pakiet NuGet, takich jak biblioteki DLL w systemie plików. Jedynym sposobem ustalenia przenoszenia tej zależności jest uruchomienie [narzędzia .NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) narzędzia. Narzędzie można analizować zestawów, które obsługują program .NET Framework i zidentyfikować interfejsy API, które nie są przenośne na innych platformach .NET, takich jak .NET Core. Narzędzie można uruchomić jako aplikację konsolową w języku lub [rozszerzenia programu Visual Studio](../../standard/analyzers/portability-analyzer.md).

## <a name="next-steps"></a>Następne kroki

Jeśli masz przenoszenie biblioteki, zapoznaj się z [przenoszenie bibliotek](libraries.md).
