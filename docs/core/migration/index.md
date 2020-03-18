---
title: Migracja programu .NET Core z projektu.json
description: Dowiedz się, jak przeprowadzić migrację starszego projektu programu .NET Core przy użyciu projektu project.json
ms.date: 07/19/2017
ms.openlocfilehash: 8a9dc05c82fd5476a70ee36a294a287abbfb68c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77450690"
---
# <a name="migrating-net-core-projects-from-projectjson"></a>Migrowanie projektów programu .NET Core z projektu.json

Ten dokument obejmuje następujące trzy scenariusze migracji dla projektów .NET Core:

1. [Migracja z prawidłowego najnowszego schematu *project.json* do *csproj*](#migration-from-projectjson-to-csproj)
2. [Migracja z DNX do csproj](#migration-from-dnx-to-csproj)
3. [Migracja z RC3 i poprzednich projektów csproj .NET Core do formatu końcowego](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

Ten dokument ma zastosowanie tylko do starszych projektów .NET Core, które używają project.json. Nie ma zastosowania do migracji z .NET Framework do .NET Core.

## <a name="migration-from-projectjson-to-csproj"></a>Migracja z project.json do csproj

Migracja z *project.json* do *.csproj* można wykonać za pomocą jednej z następujących metod:

- [Visual Studio](#visual-studio)
- [narzędzie wiersza polecenia dotnet](#dotnet-migrate)

Obie metody używają tego samego aparatu podstawowego do migracji projektów, więc wyniki będą takie same dla obu. W większości przypadków przy użyciu jednego z tych dwóch sposobów migracji *project.json* do *csproj* jest jedyną rzeczą, która jest potrzebna i nie jest konieczna dalsza ręczna edycja pliku projektu. Wynikowy plik *csproj* będzie miał taką samą nazwę jak nazwa katalogu zawierającego.

### <a name="visual-studio"></a>Visual Studio

Po otwarciu pliku *xproj* lub pliku rozwiązania odwoływanego do plików *xproj* w programie Visual Studio 2017 lub Visual Studio 2019 w wersji 16.2 i wcześniejszych zostanie wyświetlone okno dialogowe **uaktualniania jednokierunkowego.** W oknie dialogowym są wyświetlane projekty, które mają zostać poddane migracji. Jeśli otworzysz plik rozwiązania, zostaną wyświetlone wszystkie projekty określone w pliku rozwiązania. Przejrzyj listę projektów do migracji i wybierz **przycisk OK**.

![Okno dialogowe uaktualniania jednokierunkowego z listą projektów do migracji](media/one-way-upgrade.jpg)

Program Visual Studio automatycznie migruje wybrane projekty. Podczas migracji rozwiązania, jeśli nie wybierzesz wszystkich projektów, zostanie wyświetlone to samo okno dialogowe z prośbą o uaktualnienie pozostałych projektów z tego rozwiązania. Po migracji projektu można wyświetlić i zmodyfikować jego zawartość, klikając prawym przyciskiem myszy projekt w oknie **Eksploratora rozwiązań** i wybierając **pozycję Edycja \<nazwy projektu>.csproj**.

Pliki, które zostały poddane migracji (*project.json*, *global.json*, *xproj*i plik rozwiązania) są przenoszone do folderu *Kopia zapasowa.* Zmigrowany plik rozwiązania zostanie uaktualniony do programu Visual Studio 2017 lub Visual Studio 2019 i nie będzie można otworzyć tego pliku rozwiązania w programie Visual Studio 2015 lub wcześniejszych wersjach. Plik o nazwie *UpgradeLog.htm* zawierający raport migracji jest również zapisywany i otwierany automatycznie.

> [!IMPORTANT]
> W programie Visual Studio 2019 w wersji 16.3 i nowszych nie można załadować ani przeprowadzić migracji pliku *xproj.* Ponadto program Visual Studio 2015 nie zapewnia możliwości migracji pliku *xproj.* Jeśli używasz jednej z tych wersji programu Visual Studio, zainstaluj odpowiednią wersję programu Visual Studio lub użyj narzędzia do migracji wiersza polecenia opisanego dalej.

### <a name="dotnet-migrate"></a>dotnet migrate

W scenariuszu wiersza polecenia można [`dotnet migrate`](../tools/dotnet-migrate.md) użyć polecenia. Migruje projekt, rozwiązanie lub zestaw folderów w tej kolejności, w zależności od tego, które z nich zostały znalezione. Podczas migracji projektu projekt i wszystkie jego zależności są migrowane.

Pliki, które zostały poddane migracji (*project.json*, *global.json*i *.xproj*) są przenoszone do folderu *kopii zapasowej.*

> [!NOTE]
> Jeśli używasz kodu programu Visual `dotnet migrate` Studio, polecenie nie modyfikuje plików specyficznych dla kodu programu Visual Studio, takich jak *tasks.json*. Pliki te należy zmienić ręcznie.
> Jest to również prawdą, jeśli używasz edytora lub zintegrowanego środowiska programistycznego (IDE) innych niż Visual Studio.

Zobacz [Mapowanie między project.json i csproj właściwości](../tools/project-json-to-csproj.md) dla porównania *formatów project.json* i *.csproj.*

Jeśli pojawi się błąd:

> Nie znaleziono pliku wykonywalnego pasującego do polecenia dotnet-migrate

Uruchom, `dotnet --version` aby zobaczyć, której wersji używasz. [`dotnet migrate`](../tools/dotnet-migrate.md)został wprowadzony w .NET Core SDK 1.0.0 i usunięty w wersji 3.0.100.
Ten błąd zostanie uisany, jeśli w bieżącym lub nadrzędnym katalogu `sdk` znajduje się plik *global.json,* a określona przez niego wersja znajduje się poza tym zakresem.

## <a name="migration-from-dnx-to-csproj"></a>Migracja z DNX do csproj

Jeśli nadal używasz DNX dla rozwoju .NET Core, proces migracji powinien odbywać się w dwóch etapach:

1. Użyj [istniejących wskazówek migracji DNX](from-dnx.md) do migracji z DNX do projektu json włączone CLI.
2. Wykonaj kroki z poprzedniej sekcji, aby przeprowadzić migrację z *programu project.json* do *pliku .csproj*.

> [!NOTE]
> DNX został oficjalnie przestarzały podczas wersji zapoznawczej 1.NET Core CLI.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Migracja z wcześniejszych formatów csproj csproj .NET Core do RTM csproj

Format csproj .NET Core zmienia ł się wraz z każdą nową wersją przedpremierową oprzyrządowania. Nie ma narzędzia, które będzie migrować plik projektu z wcześniejszych wersji csproj do najnowszych, więc trzeba ręcznie edytować plik projektu. Rzeczywiste kroki zależą od wersji pliku projektu, który jest migrowana. Poniżej przedstawiono kilka wskazówek, które należy wziąć pod uwagę na podstawie zmian, które miały miejsce między wersjami:

- Usuń właściwość version tools `<Project>` z elementu, jeśli istnieje.
- Usuń obszar nazw XML`xmlns`( `<Project>` ) z elementu.
- Jeśli nie istnieje, dodaj `Sdk` atrybut do `<Project>` elementu i `Microsoft.NET.Sdk` ustaw `Microsoft.NET.Sdk.Web`go na lub . Ten atrybut określa, że projekt używa sdk do użycia. `Microsoft.NET.Sdk.Web`jest używany w aplikacjach internetowych.
- Usuń `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` instrukcje `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` i z góry i u dołu projektu. Te instrukcje importu są implikowane przez zestaw SDK, więc nie ma potrzeby, aby znajdowały się w projekcie.
- Jeśli masz `Microsoft.NETCore.App` `NETStandard.Library` `<PackageReference>` lub elementy w projekcie, należy je usunąć. Te odwołania do pakietów są [implikowane przez zestaw SDK](https://aka.ms/sdkimplicitrefs).
- `Microsoft.NET.Sdk` `<PackageReference>` Usuń element, jeśli istnieje. Odwołanie sdk jest `Sdk` za pośrednictwem atrybutu na `<Project>` element.
- Usuń [globs,](https://en.wikipedia.org/wiki/Glob_(programming)) które są [implikowane przez zestaw SDK](../project-sdk/overview.md#default-compilation-includes). Pozostawienie tych globs w projekcie spowoduje błąd na kompilacji, ponieważ elementy kompilacji zostaną zduplikowane.

Po tych krokach projekt powinien być w pełni zgodny z formatem CSPROJ RTM .NET Core.

Przykłady przed i po migracji ze starego formatu csproj do nowego, zobacz [aktualizowanie visual studio 2017 RC — .NET Core Tooling ulepszenia](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) artykułu w blogu .NET.

## <a name="see-also"></a>Zobacz też

- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
