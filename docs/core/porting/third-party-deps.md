---
title: Eksportowanie .NET Core - analizowanie zależności innych firm
description: Dowiedz się, jak analizować zależności innych firm w celu portu projekty w programie .NET Framework do platformy .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.openlocfilehash: a5affd8f1c493a87b2a4f7cd4096d168d404626a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="analyze-your-third-party-dependencies"></a>Analizowanie zależności innych firm

Jeśli szukasz portu kodu platformy .NET Core lub .NET Standard, pierwszym krokiem w procesie przenoszenia jest zrozumienie zależności innych firm. Zależności innych firm są albo [pakietów NuGet](#analyze-referenced-nuget-packages-on-your-project) lub [biblioteki dll](#analyze-dependencies-that-arent-nuget-packages) odwołujesz w projekcie. Oceń poszczególne zależności i opracować plan gotowości zależności, które nie są zgodne z platformą .NET Core. W tym artykule przedstawiono sposób określania, czy zależność jest zgodna z platformą .NET Core.

## <a name="analyze-referenced-nuget-packages-in-your-project"></a>Analizowanie przywoływanego pakietów NuGet w projekcie

W przypadku odwołania do pakietów NuGet w projekcie, należy sprawdzić, czy są one zgodne z platformą .NET Core.
Istnieją dwa sposoby realizacji tego:

* [Przy użyciu Eksploratora pakietów NuGet aplikacji](#analyze-nuget-packages-using-nuget-package-explorer) (najbardziej niezawodna metoda).
* [Przy użyciu witryny nuget.org](#analyze-nuget-packages-using-nugetorg).

Po przeanalizowaniu pakietów, jeśli nie są one zgodne z platformy .NET Core i tylko docelowej platformy .NET Framework, można sprawdzić, czy [.NET Framework w trybie zgodności](#net-framework-compatibility-mode) może pomóc w procesie przenoszenia.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analiza pakietów NuGet przy użyciu Eksploratora pakietów NuGet

Pakiet NuGet to zestaw folderów, które zawierają zestawy specyficzne dla platformy. Dlatego należy sprawdzić, jeśli istnieje folder zawierający zgodny zestaw w pakiecie.

Najprostszym sposobem sprawdzić folderów pakiet NuGet jest użycie [Explorer pakietu NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) narzędzia. Po jego zainstalowaniu, wykonaj następujące kroki, aby wyświetlić nazwy folderu:

1. Otwórz Eksploratora pakietu NuGet.
2. Kliknij przycisk **Otwórz pakiet ze strumieniowego źródła online**.
3. Wyszukaj nazwę pakietu.
4. Wybierz nazwę pakietu w wynikach wyszukiwania, a następnie kliknij przycisk **Otwórz**.
5. Rozwiń węzeł *lib* folderu na prawej stronie i Przeglądaj nazwy folderów.

Wyszukaj folder z dowolnymi z następujących nazw:

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
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Te wartości są [docelowej Framework monikerów (TFMs)](../../standard/frameworks.md) mapowania wersje [.NET Standard](../../standard/net-standard.md), oprogramowanie .NET Core i tradycyjnych profile przenośnej biblioteki klasy (PCL), które są zgodne z platformą .NET Core.

> [!IMPORTANT]
> Podczas przeglądania TFMs, które obsługuje pakiet, należy pamiętać, że `netcoreapp*`, podczas zgodny, jest tylko projekty .NET Core, a nie projektów .NET Standard.
> Biblioteka, przeznaczonego tylko `netcoreapp*` i nie `netstandard*` mogą być używane tylko przez inne aplikacje .NET Core.

Dostępne są również niektórych starszych TFMs używane w wersji wstępnych programu .NET Core, które mogą być niezgodne:

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

Gdy te TFMs mogą pracować z kodu, nie ma żadnej gwarancji zgodności. Pakiety z tych TFMs zostały skompilowane z pakietami .NET Core wersji wstępnej. Zwróć uwagę, gdy (lub) przy użyciu tych TFMs pakiety zostaną zaktualizowane, aby być oparta na .NET Standard.

> [!NOTE]
> Pakiet tradycyjnych PCL lub docelowej platformy .NET Core wersji wstępnej, możesz korzystać `PackageTargetFallback` elementu MSBuild w pliku projektu.
> Aby uzyskać więcej informacji o tym elemencie MSBuild, zobacz [ `PackageTargetFallback` ](../tools/csproj.md#packagetargetfallback).

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analiza pakietów NuGet przy użyciu nuget.org

Możesz również zapoznać się TFMs, obsługiwanych przez każdy pakiet na [nuget.org](https://www.nuget.org/) w obszarze **zależności** sekcji strony pakietu.

Mimo że za pomocą witryny jest łatwiejsze metody, aby sprawdzić zgodność, **zależności** informacje nie są dostępne w witrynie wszystkich pakietów.

### <a name="net-framework-compatibility-mode"></a>Tryb zgodności .NET framework

Po przeanalizowaniu pakietów NuGet, może się okazać, że ich tylko dla środowiska .NET Framework, tak jak większość pakietów NuGet.

Począwszy od .NET 2.0 standardowy, tryb zgodności .NET Framework został wprowadzony. Ten tryb zgodności umożliwia .NET Standard i .NET Core projekty do odwołania do bibliotek .NET Framework. Odwołania do bibliotek .NET Framework nie działa dla wszystkich projektów, np. Jeśli biblioteka używa Windows Presentation Foundation (WPF) interfejsów API, ale odblokować wiele scenariuszy przenoszenia.

Podczas odwoływania się pakietów NuGet, które odnoszą się do programu .NET Framework w projekcie, takich jak [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), zostanie wyświetlone ostrzeżenie rezerwowy pakietu ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) podobny do poniższego przykładu:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Tego ostrzeżenie jest wyświetlane, gdy Dodaj pakiet i każdym utworzeniu upewnij się, że test tego pakietu z projektu. Projekt działa zgodnie z oczekiwaniami, można pominąć tego ostrzeżenia, edytując właściwości pakietu w programie Visual Studio lub ręcznie, edytując plik projektu w edytorze kodu dotyczącego elementów ulubionych.

Aby pominąć to ostrzeżenie, edytując plik projektu, należy znaleźć `PackageReference` wpis pakietu chcesz pominąć to ostrzeżenie dla i dodać `NoWarn` atrybutu. `NoWarn` Atrybut akceptuje listę wszystkich ostrzeżenie identyfikatorów rozdzielonych przecinkami. Poniższy przykład przedstawia sposób pomijania `NU1701` ostrzeżenia dla `Huitian.PowerCollections` pakietu przez ręcznego edytowania pliku projektu:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Aby uzyskać więcej informacji na temat sposobu pomijanie ostrzeżeń kompilatora w programie Visual Studio, zobacz [pomijanie ostrzeżeń dla pakietów NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Co robić, jeśli zależność pakietu NuGet nie działa na .NET Core

Istnieje kilka rzeczy, które można wykonać, jeśli pakiet NuGet, które zależą od nie działa na .NET Core:

1. Projekt jest typu open source, takie jak GitHub hostowany deweloperzy mogą prowadzić bezpośrednio.
2. Można skontaktować się z autorem bezpośrednio na [nuget.org](https://www.nuget.org/). Wyszukaj pakiet i kliknij przycisk **właścicieli skontaktuj się z** w lewej części strony pakietu.
3. Możesz wyszukać inny pakiet, który jest uruchamiany na .NET Core, które spełniają to samo zadanie pakietu, który był używany.
4. Możesz spróbować pisanie kodu, że pakiet wykonywanych samodzielnie.
5. Zależność od pakietu można wyeliminować, zmieniając funkcji aplikacji, co najmniej do momentu udostępnienia zgodnej wersji pakietu.

Należy pamiętać, że projekt open source maintainers i wydawców pakietu NuGet często ochotników. Przyczyniają się, ponieważ interesujących danej domeny, należy go bezpłatnie i często mają różne zadania dziennych. Dlatego należy mając na uwadze, że podczas kontaktowania się z ich do żądania pomocy technicznej platformy .NET Core.

Jeśli nie możesz rozwiązać problemu za pomocą dowolnego z powyższych, może być konieczne port .NET Core w późniejszym terminie.

Zespół .NET chcesz dowiedzieć się, które biblioteki są najważniejsze obsługuje z platformą .NET Core. Możesz wysłać wiadomość e-mail na adres dotnet@microsoft.com o bibliotekach chcesz użyć.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analizowanie zależności, które nie są pakietów NuGet

Może mieć zależności, która nie jest pakietem NuGet, takich jak biblioteki DLL w systemie plików. Jedynym sposobem, aby określić przenośność Zależność ta jest uruchomienie [analizator przenośność .NET](https://github.com/Microsoft/dotnet-apiport) narzędzia. Narzędzie można analizować zestawy, które odnoszą się do programu .NET Framework i zidentyfikować interfejsów API, które nie są przenośne do innych platform .NET, takich jak .NET Core. Narzędzie można uruchomić jako aplikacji konsoli lub [rozszerzenie programu Visual Studio](../../standard/analyzers/portability-analyzer.md).

## <a name="next-steps"></a>Następne kroki

Jeśli w przypadku przenoszenia biblioteki, zapoznaj się [eksportowanie bibliotek](libraries.md).
