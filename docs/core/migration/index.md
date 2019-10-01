---
title: Migracja platformy .NET Core z pliku Project. JSON
description: Dowiedz się, jak przeprowadzić migrację starszego projektu .NET Core przy użyciu pliku Project. JSON
ms.date: 07/19/2017
ms.custom: seodec18
ms.openlocfilehash: 167f0707bbaf34ce12a1c56ee2320e7cc4f48bd3
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698918"
---
# <a name="migrating-net-core-projects-from-projectjson"></a>Migrowanie projektów .NET Core z pliku Project. JSON

W tym dokumencie opisano następujące trzy scenariusze migracji dla projektów programu .NET Core:

1. [Migracja z prawidłowego najnowszego schematu pliku *Project. JSON* do *csproj*](#migration-from-projectjson-to-csproj)
2. [Migracja z środowiska DNX do csproj](#migration-from-dnx-to-csproj)
3. [Migracja z RC3 i poprzednich projektów .NET Core csproj do końcowego formatu](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

Ten dokument ma zastosowanie tylko do starszych projektów programu .NET Core, które używają pliku Project. JSON. Nie dotyczy migrowania z .NET Framework do programu .NET Core.

## <a name="migration-from-projectjson-to-csproj"></a>Migracja z pliku Project. JSON do csproj

Migracja z pliku *Project. JSON* do *. csproj* można wykonać przy użyciu jednej z następujących metod:

- [Visual Studio](#visual-studio)
- [Narzędzie wiersza polecenia migracji dotnet](#dotnet-migrate)

Obie metody używają tego samego aparatu podstawowego do migrowania projektów, dlatego wyniki będą takie same dla obu tych metod. W większości przypadków użycie jednego z tych dwóch metod migracji pliku *Project. JSON* do *csproj* jest jedyną potrzebną operacją i nie jest konieczne dalsze ręczne edytowanie plików projektu. Utworzony plik *csproj* będzie taki sam jak nazwa katalogu zawierającego.

### <a name="visual-studio"></a>Visual Studio

Po otwarciu pliku *. xproj* lub pliku rozwiązania, który odwołuje się do plików *. Xproj* w programie Visual Studio 2017 lub Visual studio 2019 w wersji 16,2 i starszej, zostanie wyświetlone okno dialogowe **uaktualnianie jednokierunkowe** . W oknie dialogowym zostaną wyświetlone projekty do migracji. Jeśli otworzysz plik rozwiązania, zostaną wyświetlone wszystkie projekty określone w pliku rozwiązania. Przejrzyj listę projektów do migracji i wybierz **przycisk OK**.

![Jednokierunkowe okno dialogowe uaktualniania zawierające listę projektów do migracji](media/one-way-upgrade.jpg)

Program Visual Studio automatycznie migruje wybrane projekty. W przypadku migrowania rozwiązania, jeśli nie wybrano wszystkich projektów, zostanie wyświetlone okno dialogowe z prośbą o uaktualnienie pozostałych projektów z tego rozwiązania. Po przeprowadzeniu migracji projektu można zobaczyć i zmodyfikować jego zawartość, klikając prawym przyciskiem myszy projekt w oknie **Eksplorator rozwiązań** i wybierając polecenie **Edytuj \<project nazwę >. csproj**.

Pliki migrowane (*Project. JSON*, *Global. JSON*, *. xproj*i plik rozwiązania) są przenoszone do folderu *kopii zapasowej* . Migrowany plik rozwiązania jest uaktualniany do programu Visual Studio 2017 lub Visual Studio 2019 i nie będzie można otworzyć tego pliku rozwiązania w programie Visual Studio 2015 lub jego wcześniejszych wersjach. Plik o nazwie *UpgradeLog. htm* zawierający raport migracji również jest automatycznie zapisywany i otwierany.

> [!IMPORTANT]
> Nie można migrować projektów przy użyciu programu Visual Studio 2015.

### <a name="dotnet-migrate"></a>dotnet migrate

W scenariuszu wiersza polecenia można użyć [`dotnet migrate`](../tools/dotnet-migrate.md) polecenia. Migruje projekt, rozwiązanie lub zestaw folderów w tej kolejności, w zależności od tego, które zostały znalezione. Podczas migrowania projektu, projekt i wszystkie jego zależności są migrowane.

Pliki migrowane (*Project. JSON*, *Global. JSON*i *. xproj*) są przenoszone do folderu *kopii zapasowej* .

> [!NOTE]
> Jeśli używasz Visual Studio Code, polecenie `dotnet migrate` nie modyfikuje Visual Studio Code plików specyficznych dla programu, takich jak `tasks.json`. Te pliki należy zmienić ręcznie.
> Jest to również prawdziwe, jeśli używasz programu Project Ryder lub dowolnego edytora lub zintegrowanego środowiska programistycznego (IDE) innego niż program Visual Studio.

Zobacz [Mapowanie między właściwościami Project. JSON i csproj](../tools/project-json-to-csproj.md) , aby porównać formaty Project. JSON i csproj.

### <a name="common-issues"></a>Typowe problemy

- Jeśli zostanie wyświetlony komunikat o błędzie: "nie znaleziono pliku wykonywalnego zgodnego z poleceniem dotnet-Migrowanie":

Uruchom `dotnet --version`, aby sprawdzić, która wersja jest używana. [`dotnet migrate`](../tools/dotnet-migrate.md) wymaga interfejs wiersza polecenia platformy .NET Core RC3 lub wyższy.
Ten błąd występuje, jeśli masz plik *Global. JSON* w bieżącym lub nadrzędnym katalogu, a wersja `sdk` jest ustawiona na starszą wersję.

## <a name="migration-from-dnx-to-csproj"></a>Migracja z środowiska DNX do csproj

Jeśli nadal używasz programu środowiska DNX do programowania w środowisku .NET Core, proces migracji powinien odbywać się w dwóch etapach:

1. Użyj [istniejących wskazówek dotyczących migracji środowiska DNX](from-dnx.md) , aby przeprowadzić migrację z środowiska DNX do interfejsu wiersza polecenia z włączonym kodem JSON.
2. Postępuj zgodnie z instrukcjami z poprzedniej sekcji, aby przeprowadzić migrację z pliku *Project. JSON* do pliku *. csproj*.  

> [!NOTE]
> ŚRODOWISKA DNX jest oficjalnie przestarzałe w wersji zapoznawczej 1 interfejs wiersza polecenia platformy .NET Core.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Migracja z wcześniejszych formatów programu .NET Core csproj do wersji RTM csproj

Format programu .NET Core csproj został zmieniony i rozwijający się za pomocą każdej nowej wersji wstępnej narzędzi. Nie ma narzędzia, które przeprowadzi migrację pliku projektu z wcześniejszych wersji csproj do najnowszej, więc musisz ręcznie edytować plik projektu. Rzeczywiste kroki zależą od wersji migrowanego pliku projektu. Poniżej znajdują się wskazówki, które należy wziąć pod uwagę w zależności od zmian, które wystąpiły między wersjami:

- Usuń właściwość wersja narzędzi z elementu `<Project>` (jeśli istnieje).
- Usuń przestrzeń nazw XML (`xmlns`) z elementu `<Project>`.
- Jeśli nie istnieje, Dodaj atrybut `Sdk` do elementu `<Project>` i ustaw go na `Microsoft.NET.Sdk` lub `Microsoft.NET.Sdk.Web`. Ten atrybut określa, że projekt używa zestawu SDK, który ma być używany. `Microsoft.NET.Sdk.Web` jest używany na potrzeby aplikacji sieci Web.
- Usuń instrukcje `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` i `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` z góry i u dołu projektu. Te instrukcje importu są implikowane przez zestaw SDK, więc nie ma potrzeby, aby były one w projekcie.
- Jeśli masz `Microsoft.NETCore.App` lub `NETStandard.Library` `<PackageReference>` elementów w projekcie, należy je usunąć. Te odwołania do pakietów są [implikowane przez zestaw SDK](https://aka.ms/sdkimplicitrefs).
- Usuń element `Microsoft.NET.Sdk` `<PackageReference>`, jeśli istnieje. Odwołanie do zestawu SDK znajduje się w atrybucie `Sdk` elementu `<Project>`.
- Usuń [elementy globalne](https://en.wikipedia.org/wiki/Glob_(programming)) , które są [implikowane przez zestaw SDK](../tools/csproj.md#default-compilation-includes-in-net-core-projects). Pozostawienie tych elementy globalne w projekcie spowoduje wystąpienie błędu podczas kompilacji, ponieważ elementy kompilacji zostaną zduplikowane.

Po wykonaniu tych kroków projekt powinien być w pełni zgodny z formatem CSPROJ RTM platformy .NET Core.

Aby zapoznać się z przykładami przed i po migracji ze starego formatu csproj do nowego, zobacz artykuł [Aktualizacja programu Visual Studio 2017 RC — udoskonalenia narzędzi dla programu .NET Core](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) w blogu platformy .NET.

## <a name="see-also"></a>Zobacz także

- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
