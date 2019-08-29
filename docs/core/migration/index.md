---
title: Migracja platformy .NET Core z pliku Project. JSON
description: Dowiedz się, jak przeprowadzić migrację starszego projektu .NET Core przy użyciu pliku Project. JSON
ms.date: 07/19/2017
ms.custom: seodec18
ms.openlocfilehash: 6334f06a998054cfaf766654dda59d87f5d23ed8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105307"
---
# <a name="migrating-net-core-projects-from-projectjson"></a>Migrowanie projektów .NET Core z pliku Project. JSON

W tym dokumencie omówiono scenariusze migracji dla projektów .NET Core i przechodzą następujące trzy scenariusze migracji:

1. [Migracja z prawidłowego najnowszego schematu pliku *Project. JSON* do *csproj*](#migration-from-projectjson-to-csproj)
2. [Migracja z środowiska DNX do csproj](#migration-from-dnx-to-csproj)
3. [Migracja z RC3 i poprzednich projektów .NET Core csproj do końcowego formatu](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

Ten dokument ma zastosowanie tylko do starszych projektów programu .NET Core, które nadal używają pliku Project. JSON. Nie dotyczy migrowania z .NET Framework do programu .NET Core.

## <a name="migration-from-projectjson-to-csproj"></a>Migracja z pliku Project. JSON do csproj

Migracja z pliku *Project. JSON* do *. csproj* można wykonać przy użyciu jednej z następujących metod:

- [Visual Studio 2017](#visual-studio-2017)
- [Narzędzie wiersza polecenia migracji dotnet](#dotnet-migrate)

Obie metody używają tego samego aparatu podstawowego do migrowania projektów, dlatego wyniki będą takie same dla obu tych metod. W większości przypadków użycie jednego z tych dwóch metod migracji pliku *Project. JSON* do *csproj* jest jedyną potrzebną operacją i nie jest konieczne ręczne edytowanie plików projektu. Utworzony plik *csproj* będzie taki sam jak nazwa katalogu zawierającego.

### <a name="visual-studio-2017"></a>Visual Studio 2017

Po otwarciu pliku *. xproj* lub pliku rozwiązania, który odwołuje się do plików *. xproj* zostanie wyświetlone okno dialogowe **uaktualnianie jednokierunkowe** . W oknie dialogowym zostaną wyświetlone projekty do migracji.
Jeśli otworzysz plik rozwiązania, zostaną wyświetlone wszystkie projekty określone w pliku rozwiązania. Przejrzyj listę projektów do migracji i wybierz **przycisk OK**.

![Jednokierunkowe okno dialogowe uaktualniania zawierające listę projektów do migracji](media/one-way-upgrade.jpg)

Program Visual Studio automatycznie przeprowadzi migrację wybranych projektów. W przypadku migrowania rozwiązania, jeśli nie wybrano wszystkich projektów, zostanie wyświetlone okno dialogowe z prośbą o uaktualnienie pozostałych projektów z tego rozwiązania. Po migracji projektu można zobaczyć i zmodyfikować jego zawartość, klikając prawym przyciskiem myszy projekt w oknie **Eksplorator rozwiązań** i wybierając polecenie **Edytuj \<nazwę projektu >. csproj**.

Pliki migrowane (*Project. JSON*, *Global. JSON*, *. xproj* i plik rozwiązania) zostaną przeniesione do folderu *kopii zapasowej* . Migrowany plik rozwiązania zostanie uaktualniony do wersji Visual Studio 2017 i nie będzie można otworzyć tego pliku rozwiązania we wcześniejszych wersjach programu Visual Studio.
Plik o nazwie *UpgradeLog. htm* jest również zapisywany i automatycznie otwierany, który zawiera raport migracji.

> [!IMPORTANT]
> Nowe narzędzia nie są dostępne w programie Visual Studio 2015, dlatego nie można migrować projektów przy użyciu tej wersji programu Visual Studio.

### <a name="dotnet-migrate"></a>dotnet migrate

W scenariuszu wiersza polecenia można użyć [`dotnet migrate`](../tools/dotnet-migrate.md) polecenia. Przeprowadzi migrację projektu, rozwiązania lub zestawu folderów w tej kolejności, w zależności od tego, które zostały znalezione.
Podczas migrowania projektu, projekt i wszystkie jego zależności są migrowane.

Pliki migrowane (*Project. JSON*, *Global. JSON* i *. xproj*) zostaną przeniesione do folderu *kopii zapasowej* .

> [!NOTE]
> Jeśli używasz Visual Studio Code, `dotnet migrate` polecenie nie zmodyfikuje plików specyficznych dla Visual Studio Code, takich jak. `tasks.json` Te pliki należy zmienić ręcznie.
> Jest to również prawdziwe, jeśli używasz programu Project Ryder lub dowolnego edytora lub zintegrowanego środowiska programistycznego (IDE) innego niż program Visual Studio.

Zobacz [Mapowanie między właściwościami Project. JSON i csproj](../tools/project-json-to-csproj.md) , aby porównać formaty Project. JSON i csproj.

### <a name="common-issues"></a>Typowe problemy

- Jeśli wystąpi błąd: "Nie znaleziono pliku wykonywalnego zgodnego z poleceniem dotnet-Migrowanie":

Uruchom `dotnet --version` , aby zobaczyć, której wersji używasz. [`dotnet migrate`](../tools/dotnet-migrate.md)wymaga interfejs wiersza polecenia platformy .NET Core RC3 lub wyższego.
Ten błąd występuje, jeśli masz plik *Global. JSON* w bieżącym lub nadrzędnym katalogu, a `sdk` wersja jest ustawiona na starszą wersję.

## <a name="migration-from-dnx-to-csproj"></a>Migracja z środowiska DNX do csproj

Jeśli nadal używasz programu środowiska DNX do programowania w środowisku .NET Core, proces migracji powinien odbywać się w dwóch etapach:

1. Użyj [istniejących wskazówek dotyczących migracji środowiska DNX](from-dnx.md) , aby przeprowadzić migrację z środowiska DNX do interfejsu wiersza polecenia z włączonym kodem JSON.
2. Postępuj zgodnie z instrukcjami z poprzedniej sekcji, aby przeprowadzić migrację z pliku *Project. JSON* do pliku *. csproj*.  

> [!NOTE]
> ŚRODOWISKA DNX jest oficjalnie przestarzałe w wersji zapoznawczej 1 interfejs wiersza polecenia platformy .NET Core.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Migracja z wcześniejszych formatów programu .NET Core csproj do wersji RTM csproj

Format programu .NET Core csproj został zmieniony i rozwijający się za pomocą każdej nowej wersji wstępnej narzędzi. Nie ma narzędzia, które przeprowadzi migrację pliku projektu z wcześniejszych wersji csproj do najnowszej, więc musisz ręcznie edytować plik projektu. Rzeczywiste kroki zależą od wersji migrowanego pliku projektu. Poniżej znajdują się wskazówki, które należy wziąć pod uwagę w zależności od zmian, które wystąpiły między wersjami:

- Usuń właściwość wersja narzędzi z `<Project>` elementu, jeśli istnieje.
- Usuń przestrzeń nazw XML (`xmlns`) `<Project>` z elementu.
- Jeśli nie istnieje, `Sdk` Dodaj atrybut `<Project>` do elementu i ustaw go na `Microsoft.NET.Sdk` lub `Microsoft.NET.Sdk.Web`. Ten atrybut określa, że projekt używa zestawu SDK, który ma być używany. `Microsoft.NET.Sdk.Web`jest używany dla aplikacji sieci Web.
- Usuń instrukcje `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` i z góry i u dołu projektu. `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` Te instrukcje importu są implikowane przez zestaw SDK, więc nie ma potrzeby, aby były one w projekcie.
- Jeśli masz `Microsoft.NETCore.App` lub `NETStandard.Library` elementywprojekcie,należyjeusunąć`<PackageReference>` . Te odwołania do pakietów są [implikowane przez zestaw SDK](https://aka.ms/sdkimplicitrefs).
- `Microsoft.NET.Sdk` Usuń`<PackageReference>` element, jeśli istnieje. Odwołanie do zestawu SDK zawiera `Sdk` atrybut `<Project>` w elemencie.
- Usuń [elementy globalne](https://en.wikipedia.org/wiki/Glob_(programming)) , które są [implikowane przez zestaw SDK](../tools/csproj.md#default-compilation-includes-in-net-core-projects). Pozostawienie tych elementy globalne w projekcie spowoduje wystąpienie błędu podczas kompilacji, ponieważ elementy kompilacji zostaną zduplikowane.

Po wykonaniu tych kroków projekt powinien być w pełni zgodny z formatem CSPROJ RTM platformy .NET Core.

Aby zapoznać się z przykładami przed i po migracji ze starego formatu csproj do nowego, zobacz artykuł [Aktualizacja programu Visual Studio 2017 RC — udoskonalenia narzędzi dla programu .NET Core](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) w blogu platformy .NET.

## <a name="see-also"></a>Zobacz także

- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
