---
title: Migracja platformy .NET core do formatu csproj
description: .NET core project.json do csproj migracji
author: blackdwarf
ms.author: mairaw
ms.date: 07/19/2017
ms.openlocfilehash: da1995ed3b77cb802d1f3d04e6d741809de20927
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44709428"
---
# <a name="migrating-net-core-projects-to-the-csproj-format"></a>Migrowanie projektów .NET Core do formatu csproj

W tym dokumencie opisano scenariusze migracji dla projektów .NET Core i przechodzą przez następujące scenariusze migracji trzy:

1. [Migracja z prawidłowym schematem najnowsze z *project.json* do *csproj*](#migration-from-projectjson-to-csproj)
2. [Migracja ze środowiska DNX do pliku csproj](#migration-from-dnx-to-csproj)
3. [Migracja z RC3 i poprzedniej projektów csproj programu .NET Core do końcowego formatu](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

## <a name="migration-from-projectjson-to-csproj"></a>Migracja z pliku project.json do csproj

Migracja z *project.json* do *.csproj* może odbywać się przy użyciu jednej z następujących metod:

- [Visual Studio 2017](#visual-studio-2017)
- [polecenia DotNet migracji narzędzie wiersza polecenia](#dotnet-migrate)

Obie metody umożliwiają migrację projektów, aby wyniki będą takie same dla obu tego samego silnika podstawowego. W większości przypadków przy użyciu jednej z tych metod, aby przeprowadzić migrację *project.json* do *csproj* jest jedynym elementem, który jest potrzebny i żadne dodatkowe ręczne edytowanie pliku projektu jest to konieczne. Wartość wynikowa *.csproj* pliku będzie miała taka sama jak nazwa katalogu zawierającego.

### <a name="visual-studio-2017"></a>Visual Studio 2017

Po otwarciu *xproj* plik lub rozwiązanie, która odwołuje się do pliku *xproj* pliki, **jednokierunkowe uaktualnienie** zostanie wyświetlone okno dialogowe. Okno dialogowe wyświetla projektów przeznaczonych do migracji.
Jeśli otworzysz plik rozwiązania, zostaną wyświetlone wszystkie projekty, które są określone w pliku rozwiązania. Przejrzyj listę projektów, które mają zostać poddane migracji, a następnie wybierz pozycję **OK**.

![Jednokierunkowego uaktualnienia okno dialogowe z wyświetloną listę projektów przeznaczonych do migracji](media/one-way-upgrade.jpg)

Program Visual Studio, zostaną zmigrowane projektów wybrana automatycznie. Podczas migrowania rozwiązaniem, jeśli nie wybierzesz, wszystkie projekty, ten sam dialog pojawi się monitem o uaktualnienie Pozostałe projekty z tego rozwiązania. Po przeprowadzeniu migracji projektu można wyświetlić i zmodyfikować jego zawartość, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** okna i wybierając polecenie **Edytuj \<Nazwa projektu > .csproj**.

Pliki, które zostały poddane migracji (*project.json*, *global.json*, *xproj* i plik rozwiązania) zostanie przeniesiony do *kopii zapasowej* folderu. Plik rozwiązania, który został poddany migracji, które zostaną uaktualnione do programu Visual Studio 2017 i nie będzie można otworzyć tego pliku rozwiązania w poprzednich wersjach programu Visual Studio.
Plik o nazwie *UpgradeLog.htm* jest także zapisywane i automatycznie otwierane zawiera raport z migracji.

> [!IMPORTANT]
> Nowe narzędzia nie jest dostępne w programie Visual Studio 2015, więc nie można dokonać migracji projektów za pomocą tej wersji programu Visual Studio.

### <a name="dotnet-migrate"></a>Migrowanie DotNet

W tym scenariuszu, wiersza polecenia, można użyć [ `dotnet migrate` ](../tools/dotnet-migrate.md) polecenia. Zmigruje projektu, to rozwiązanie lub zestaw folderów w takiej kolejności, w zależności od takich, które zostały odnalezione.
Podczas migracji projektu migracji projektu i wszystkich jego zależności.

Pliki, które zostały poddane migracji (*project.json*, *global.json* i *xproj*) zostanie przeniesiony do *kopii zapasowej* folderu.

> [!NOTE]
> Jeśli używasz programu Visual Studio Code, `dotnet migrate` polecenia takie jak nie zmodyfikuje pliki specyficznymi dla kodu programu Visual Studio `tasks.json`. Te pliki trzeba zmieniać ręcznie.
> Jest to również wartość true, jeśli używasz Ryder projektu lub dowolnego edytora lub tworzenia środowiska IDE (Integrated) niż Visual Studio.

Zobacz [mapowanie między formatami project.json i csproj właściwości](../tools/project-json-to-csproj.md) porównanie formatami project.json i csproj.

### <a name="common-issues"></a>Typowe problemy

- Jeśli zostanie wyświetlony komunikat o błędzie: "nie pliku wykonywalnego znaleziono pasującego polecenia dotnet-migracji":

Uruchom `dotnet --version` aby zobaczyć, której wersji używasz. [`dotnet migrate`](../tools/dotnet-migrate.md) wymaga platformy .NET Core interfejsu wiersza polecenia RC3 lub nowszej.
Jeśli istnieje, zostanie wyświetlony ten błąd *global.json* plik w bieżącym lub katalog nadrzędny i `sdk` wersja została ustawiona na starszą wersję.

## <a name="migration-from-dnx-to-csproj"></a>Migracja ze środowiska DNX do pliku csproj

Jeśli nadal używasz środowiska DNX programowania .NET Core, proces migracji ma się odbywać w dwóch etapach:

1. Użyj [wskazówki dotyczące migracji istniejącego środowiska DNX](from-dnx.md) migracji ze środowiska DNX włączone json projektu interfejsu wiersza polecenia.
2. Postępuj zgodnie z instrukcjami w poprzedniej sekcji, aby przeprowadzić migrację z *project.json* do *.csproj*.  

> [!NOTE]
> Środowiska DNX stają się oficjalnie przestarzałe w wersji 1 (wersja zapoznawcza), interfejsu wiersza polecenia platformy .NET Core.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Migracja z starszych formatach csproj platformy .NET Core do wersji RTM csproj

Zmiana formatu csproj platformy .NET Core i zmieniających się za pomocą każda nowa wersja wstępna narzędzi. Nie ma żadnych narzędzie, które będą migracji pliku projektu z wcześniejszych wersji pliku csproj do najnowszej wersji, więc trzeba ręcznie edytować plik projektu. Rzeczywiste kroki zależą od wersji pliku projektu, który jest przeprowadzana migracja. Poniżej przedstawiono pewne wskazówki do uwzględnienia na podstawie zmian, które miały miejsce między wersjami:

* Usuń właściwość wersji narzędzia `<Project>` elementu, jeśli taki istnieje.
* Usuń przestrzeń nazw XML (`xmlns`) z `<Project>` elementu.
* Jeśli nie istnieje, Dodaj `Sdk` atrybutu `<Project>` element i ustaw ją na `Microsoft.NET.Sdk` lub `Microsoft.NET.Sdk.Web`. Ten atrybut określa, że projekt korzysta z zestawu SDK do użycia. `Microsoft.NET.Sdk.Web` jest używana dla aplikacji sieci web.
* Usuń `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` i `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` instrukcji, górnej i dolnej części projektu. Import, te instrukcje są też dorozumianych przez zestaw SDK, dzięki czemu nie trzeba ich w projekcie.
* Jeśli masz `Microsoft.NETCore.App` lub `NETStandard.Library` `<PackageReference>` elementów w projekcie, należy usunąć je. Te odwołania do pakietu są [też dorozumianych przez zestaw SDK](https://aka.ms/sdkimplicitrefs).
* Usuń `Microsoft.NET.Sdk` `<PackageReference>` elementu, jeśli taki istnieje. Odwołanie do zestawu SDK, który jest dostarczany za pośrednictwem `Sdk` atrybutu na `<Project>` elementu.
* Usuń [elementy globalne](https://en.wikipedia.org/wiki/Glob_(programming)) , które są [też dorozumianych przez zestaw SDK](../tools/csproj.md#default-compilation-includes-in-net-core-projects). Pozostawienie te elementy globalne w projekcie spowoduje, że wystąpił błąd podczas kompilacji ponieważ zostaną zduplikowane elementy kompilacji.

Po wykonaniu tych kroków projektu powinien być w pełni zgodny z formatem pliku csproj RTM platformy .NET Core.

Aby uzyskać przykłady przed i po migracji ze starego formatu csproj do nowego, zobacz [aktualizacji Visual Studio 2017 RC — ulepszenia narzędzi programu .NET Core](https://blogs.msdn.microsoft.com/dotnet/2016/12/12/updating-visual-studio-2017-rc-net-core-tooling-improvements/) artykuł w blogu .NET.

## <a name="see-also"></a>Zobacz także

- [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
