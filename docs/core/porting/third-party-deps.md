---
title: Analizowanie zależności w celu przeniesienia kodu portu do programu .NET Core
description: Dowiedz się, jak analizować zależności zewnętrzne w celu przeniesienia projektu z .NET Framework do .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: 2aa09e551a99358d3a6961fafcfc0aa8dbd976b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398966"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>Analizowanie zależności w celu przeniesienia kodu do .NET Core

Aby przenieść kod do .NET Core lub .NET Standard, należy zrozumieć zależności. Zależności zewnętrzne są pakiety NuGet lub `.dll` pliki, do których odwołujesz się w projekcie, ale nie tworzą samodzielnie.

## <a name="migrate-your-nuget-packages-to-packagereference"></a>Migrowanie pakietów NuGet do`PackageReference`

Program .NET Core używa [PackageReference](/nuget/consume-packages/package-references-in-project-files) do określania zależności pakietów. Jeśli używasz [packages.config,](/nuget/reference/packages-config) aby określić pakiety w projekcie, `PackageReference` przekonwertuj go na format, ponieważ `packages.config` nie jest obsługiwany w programie .NET Core.

Aby dowiedzieć się, jak przeprowadzić migrację, zobacz [migracji z packages.config do PackageReference](/nuget/reference/migrate-packages-config-to-package-reference) artykułu.

## <a name="upgrade-your-nuget-packages"></a>Uaktualnij swoje pakiety NuGet

Po migracji projektu do `PackageReference` formatu sprawdź, czy pakiety są zgodne z .NET Core.

Najpierw uaktualnij pakiety do najnowszej wersji, którą możesz. Można to zrobić za pomocą interfejsu interfejsu menedżera pakietów NuGet w programie Visual Studio. Jest prawdopodobne, że nowsze wersje zależności pakietu są już zgodne z .NET Core.

## <a name="analyze-your-package-dependencies"></a>Analizowanie zależności pakietów

Jeśli nie masz jeszcze zweryfikowania, czy przekonwertowane i uaktualnione zależności pakietów działają na .NET Core, można to osiągnąć na kilka sposobów:

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analizowanie pakietów NuGet przy użyciu nuget.org

Można zobaczyć menikers platformy docelowej (TFM), że każdy pakiet obsługuje [na nuget.org](https://www.nuget.org/) w sekcji **zależności** na stronie pakietu.

Chociaż korzystanie z witryny jest łatwiejsza metoda weryfikacji zgodności, **informacje o zależnościach** nie są dostępne w witrynie dla wszystkich pakietów.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analizowanie pakietów NuGet przy użyciu Eksploratora pakietów NuGet

Pakiet NuGet sam zestaw folderów, które zawierają zestawy specyficzne dla platformy. Sprawdź, czy istnieje folder, który zawiera zgodny zestaw wewnątrz pakietu.

Najprostszym sposobem sprawdzenia folderów pakietów NuGet jest użycie narzędzia [NuGet Package Explorer.](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) Po zainstalowaniu go, należy wykonać następujące kroki, aby wyświetlić nazwy folderów:

1. Otwórz Eksploratora pakietów NuGet.
2. Kliknij **pozycję Otwórz pakiet z pliku danych online**.
3. Wyszukaj nazwę pakietu.
4. Wybierz nazwę pakietu z wyników wyszukiwania i kliknij **przycisk Otwórz**przycisk Otwórz .
5. Rozwiń folder *lib* po prawej stronie i spójrz na nazwy folderów.

Poszukaj folderu z nazwami `netstandardX.Y` przy `netcoreappX.Y`użyciu jednego z następujących wzorców: lub .

Wartości te są [target Framework Monikers (TFM),](../../standard/frameworks.md) które mapują do wersji [.NET Standard](../../standard/net-standard.md), .NET Core i tradycyjnych przenośnych bibliotek klas (PCL) profile, które są zgodne z .NET Core.

> [!IMPORTANT]
> Patrząc na TFM, że pakiet obsługuje, należy pamiętać, że `netcoreapp*`, podczas gdy zgodne, jest tylko dla projektów .NET Core, a nie dla projektów .NET Standard.
> Biblioteka, która `netcoreapp*` jest `netstandard*` przeznaczona tylko dla osób docelowych i nie może być używana tylko przez inne aplikacje .NET Core.

## <a name="net-framework-compatibility-mode"></a>Tryb zgodności .NET Framework

Po przeanalizowaniu pakietów NuGet może się okazać, że są one przeznaczone tylko dla .NET Framework.

Począwszy od .NET Standard 2.0 wprowadzono tryb zgodności .NET Framework. Ten tryb zgodności umożliwia projektom .NET Standard i .NET Core odwoływanie się do bibliotek .NET Framework. Odwoływanie się do bibliotek .NET Framework nie działa dla wszystkich projektów, na przykład jeśli biblioteka używa interfejsów API Programu Windows Presentation Foundation (WPF), ale odblokowuje wiele scenariuszy przenoszenia.

Podczas odwoływania się do pakietów NuGet, które są przeznaczone dla programu .NET Framework w projekcie, takich jak [Huitian.PowerCollections,](https://www.nuget.org/packages/Huitian.PowerCollections)otrzymasz ostrzeżenie rezerwowe pakietu ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) podobne do następującego przykładu:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

To ostrzeżenie jest wyświetlane po dodaniu pakietu i za każdym razem, gdy tworzysz, aby upewnić się, że testujesz ten pakiet z projektem. Jeśli projekt działa zgodnie z oczekiwaniami, można pominąć to ostrzeżenie, edytując właściwości pakietu w programie Visual Studio lub ręcznie edytując plik projektu w edytorze ulubionych kodów.

Aby pominąć ostrzeżenie, edytując `PackageReference` plik projektu, znajdź wpis dla pakietu, `NoWarn` dla którego chcesz pominąć ostrzeżenie i dodać atrybut. Atrybut `NoWarn` akceptuje listę wszystkich identyfikatorów ostrzeżeń rozdzielonych przecinkami. W poniższym przykładzie pokazano, jak pominąć `NU1701` ostrzeżenie dla pakietu, `Huitian.PowerCollections` edytując plik projektu ręcznie:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Aby uzyskać więcej informacji na temat pomijania ostrzeżeń kompilatora w programie Visual Studio, zobacz [Pomijanie ostrzeżeń dla pakietów NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Co zrobić, gdy zależność pakietu NuGet nie działa na .NET Core

Istnieje kilka czynności, które można zrobić, jeśli pakiet NuGet, od którego zależy, nie jest uruchamiany w ustom .NET Core:

- Jeśli projekt jest open source i hostowane gdzieś jak GitHub, można zaangażować deweloperów bezpośrednio.
- Możesz skontaktować się z autorem bezpośrednio na [nuget.org](https://www.nuget.org/). Wyszukaj pakiet i kliknij **pozycję Skontaktuj się z właścicielami** po lewej stronie strony pakietu.
- Można wyszukać inny pakiet, który działa na .NET Core, który realizuje to samo zadanie, co pakiet, którego używasz.
- Można spróbować napisać kod pakiet robił samodzielnie.
- Można wyeliminować zależność od pakietu, zmieniając funkcjonalność aplikacji, przynajmniej do momentu udostępnienia zgodnej wersji pakietu.

Należy pamiętać, że opiekunowie projektów typu open source i wydawcy pakietów NuGet są często wolontariuszami. Przyczyniają się, ponieważ dbają o daną domenę, robią to za darmo i często mają inną pracę w ciągu dnia. Należy o tym pamiętać podczas kontaktowania się z nimi, aby poprosić o pomoc techniczną .NET Core.

Jeśli nie możesz rozwiązać problemu z którąkolwiek z tych opcji, może być trzeba przenieść do .NET Core w późniejszym terminie.

Zespół .NET chciałby wiedzieć, które biblioteki są najważniejsze do obsługi z .NET Core. Możesz wysłać wiadomość dotnet@microsoft.com e-mail do o bibliotekach, których chcesz użyć.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analizowanie zależności, które nie są pakietami NuGet

Może mieć zależność, która nie jest pakietem NuGet, takich jak dll w systemie plików. Jedynym sposobem określenia przenośności tej zależności jest uruchomienie narzędzia [Analizator przenośności .NET.](https://github.com/Microsoft/dotnet-apiport) Narzędzie analizuje zestawy, które są przeznaczone dla programu .NET Framework i identyfikuje interfejsy API, które nie są przenośne dla innych platform .NET, takich jak .NET Core. Narzędzie można uruchomić jako aplikację konsoli lub jako [rozszerzenie programu Visual Studio.](../../standard/analyzers/portability-analyzer.md)

## <a name="next-steps"></a>Następne kroki

>[!div class="nextstepaction"]
>[Przenoszenie bibliotek](libraries.md)
