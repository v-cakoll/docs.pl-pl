---
title: Oprogramowanie .NET core migracji do formatu csproj
description: Oprogramowanie .NET core project.json csproj migracji
author: blackdwarf
ms.author: mairaw
ms.date: 07/19/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 102b875072ed77a328bdb6a62ed6cc98612ff059
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="migrating-net-core-projects-to-the-csproj-format"></a>Migrowanie projektów .NET Core do formatu .csproj

Ten dokument opisano scenariusze migracji dla projektów .NET Core i będą przekazywane następujące scenariusze migracji trzy:

1. [Migracja z prawidłowym schematem najnowsze z *project.json* do *csproj*](#migration-from-projectjson-to-csproj)
2. [Migracja z DNX do csproj](#migration-from-dnx-to-csproj)
3. [Migracja z RC3 i poprzednich projektów csproj .NET Core na ostateczny format](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

## <a name="migration-from-projectjson-to-csproj"></a>Migracja z project.json do csproj
Migracja z *project.json* do *.csproj* może odbywać się przy użyciu jednej z następujących metod:

- [Visual Studio 2017](#visual-studio-2017)
- [Narzędzie wiersza polecenia migracji DotNet](#dotnet-migrate)
 
Obie metody umożliwia migrację projektów, więc wyniki będą takie same dla tego samego silnika podstawowej. W większości przypadków przy użyciu jednej z tych metod, aby przeprowadzić migrację *project.json* do *csproj* jest jedynym elementem, który jest wymagany i niezbędne jest dalsze ręcznej edycji pliku projektu. Powstałe w ten sposób *.csproj* pliku będzie miała nazwę taka sama jak nazwa katalogu zawierającego.

### <a name="visual-studio-2017"></a>Visual Studio 2017

Po otwarciu *xproj* pliku lub rozwiązanie, które odwołuje się do pliku *xproj* pliki, **jednokierunkowe uaktualnienia** zostanie wyświetlone okno dialogowe. Okno dialogowe wyświetla projekty do migracji. Po otwarciu pliku rozwiązania, zostaną wyświetlone wszystkie projekty, które są określone w pliku rozwiązania. Przejrzyj listę projektów, aby zmigrować, a następnie wybierz **OK**.

![Wyświetla listę projektów przeznaczonych do migracji jednokierunkowe uaktualnienia okno dialogowe](media/one-way-upgrade.jpg)

Visual Studio będą migrowane projektów wybrana automatycznie. Podczas migracji rozwiązanie, jeśli użytkownik nie należy wybierać wszystkie projekty, tym samym oknie dialogowym zostanie wyświetlony monitem o Uaktualnij Pozostałe projekty z tego rozwiązania. Po przeprowadzeniu migracji folderu projektu, możesz wyświetlić i zmodyfikować jego zawartość, klikając prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** okna i wybierając **Edytuj \<Nazwa projektu > .csproj**.

Pliki, które zostały poddane migracji (*project.json*, *global.json*, *xproj* i plik rozwiązania) zostanie przeniesiony do *kopii zapasowej* folderu. Plik rozwiązania, który jest migrowany zostanie uaktualniona do programu Visual Studio 2017 i nie będzie można otworzyć tego pliku rozwiązania w poprzednich wersjach programu Visual Studio. Plik o nazwie *UpgradeLog.htm* jest także zapisać i automatycznie otwierane zawierający raport migracji.

> [!IMPORTANT]
> Nowe narzędzia nie jest dostępne w programie Visual Studio 2015, dlatego nie można migrować projektów przy użyciu tej wersji programu Visual Studio.

### <a name="dotnet-migrate"></a>Migrowanie DotNet

W tym scenariuszu, wiersza polecenia, można użyć [ `dotnet migrate` ](../tools/dotnet-migrate.md) polecenia. Zmigruje projektu, rozwiązania lub zestawie folderów w tej kolejności, w zależności od takich, które zostały odnalezione. Podczas migracji projektu projektu i jego zależności są migrowane.

Pliki, które zostały poddane migracji (*project.json*, *global.json* i *xproj*) zostanie przeniesiony do *kopii zapasowej* folderu.

> [!NOTE]
> Jeśli używasz programu Visual Studio Code, `dotnet migrate` polecenia takie jak nie zmodyfikuje pliki specyficzne dla programu Visual Studio kod `tasks.json`. Te pliki muszą być zmieniony ręcznie. Jest to również wartość true, jeśli używasz Ryder projektu lub dowolnego edytora lub programowanie środowiska IDE (Integrated) inne niż Visual Studio. 

Zobacz [mapowania między właściwości pliku project.json i csproj](../tools/project-json-to-csproj.md) Porównanie formatów pliku project.json i csproj.

### <a name="common-issues"></a>Typowe problemy

- Jeśli wystąpi błąd: "nie pliku wykonywalnego odnaleźć pasującego dotnet polecenia-migracji":

Uruchom `dotnet --version` aby zobaczyć, której używasz wersji. [`dotnet migrate`](../tools/dotnet-migrate.md) wymaga programu .NET Core CLI RC3 lub nowszej.
Zostanie wyświetlony ten błąd, jeśli masz *global.json* pliku w bieżącej lub katalog nadrzędny i `sdk` ustawiono wersji na starszą wersję.

## <a name="migration-from-dnx-to-csproj"></a>Migracja z DNX do csproj
Jeśli nadal używasz środowiska DNX dla rozwoju platformy .NET Core, procesu migracji należy wykonywać w dwóch etapach:

1. Użyj [istniejących wskazówki dotyczące migracji DNX](from-dnx.md) do migracji z DNX do projektu json włączone interfejsu wiersza polecenia.
2. Wykonaj kroki opisane w poprzedniej sekcji, aby przeprowadzić migrację z *project.json* do *.csproj*.  

> [!NOTE]
> DNX jest oficjalnie używany w wersji Preview 1 programu .NET Core interfejsu wiersza polecenia. 

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Migracja z wcześniejszych formatów csproj .NET Core do RTM csproj
Zmiana format csproj .NET Core i rozwijającymi z każdego nowego wstępną wersję narzędzi. Nie ma narzędzia, które będą migrowane pliku projektu z wcześniejszych wersji csproj do najnowszej wersji, więc musisz ręcznie edytować plik projektu. Rzeczywiste kroki zależą od wersji pliku projektu, który jest przeprowadzana migracja. Oto niektóre wskazówki wziąć pod uwagę na podstawie zmian, które wystąpiły między wersjami:

* Usuń właściwość wersji narzędzi z `<Project>` elementu, jeśli istnieje. 
* Usuń obszar nazw XML (`xmlns`) z `<Project>` elementu.
* Jeśli nie istnieje, Dodaj `Sdk` atrybutu `<Project>` element i ustaw ją na `Microsoft.NET.Sdk` lub `Microsoft.NET.Sdk.Web`. Ten atrybut określa, że projekt korzysta z zestawu SDK do użycia. `Microsoft.NET.Sdk.Web` Służy do aplikacji sieci web.
* Usuń `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` i `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` instrukcje od góry i u dołu projektu. Import, te instrukcje są implikowana przez zestaw SDK, więc nie istnieje potrzeba do nich w projekcie. 
* Jeśli masz `Microsoft.NETCore.App` lub `NETStandard.Library` `<PackageReference>` elementów w projekcie, należy usunąć je. Te odwołania do pakietu są [niejawnego przez zestaw SDK](https://aka.ms/sdkimplicitrefs). 
* Usuń `Microsoft.NET.Sdk` `<PackageReference>` elementu, jeśli istnieje. Odwołanie do zestawu SDK jest dostarczany za pomocą `Sdk` atrybutu `<Project>` elementu. 
* Usuń [globs](https://en.wikipedia.org/wiki/Glob_(programming)) , które są [niejawnego przez zestaw SDK](../tools/csproj.md#default-compilation-includes-in-net-core-projects). Pozostawienie tych globs projektu spowoduje, że wystąpił błąd podczas kompilacji ponieważ zostaną zduplikowane elementy kompilacji. 

Po wykonaniu tych kroków projektu należy w pełni zgodny z formatem csproj RTM .NET Core. 

Przykłady przed i po migracji z formatu csproj starego do nowego, zobacz [aktualizacji programu Visual Studio 2017 RC — ulepszenia narzędzi programu .NET Core](https://blogs.msdn.microsoft.com/dotnet/2016/12/12/updating-visual-studio-2017-rc-net-core-tooling-improvements/) artykuł w blogu .NET.

## <a name="see-also"></a>Zobacz także
[Port, migrowanie i uaktualnianie projektów programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
