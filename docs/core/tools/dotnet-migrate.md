---
title: polecenie - .NET Core interfejsu wiersza polecenia migracji DotNet
description: "Migrowanie dotnet polecenia migruje projekt i wszystkie jego zależności."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 7fad6bf67dfe7b0d6f70ce527a153080aa17d888
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-migrate"></a>Migrowanie DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet migrate`-Wykonuje migrację projektu Preview 2 .NET Core projekt .NET Core SDK 1.0.

## <a name="synopsis"></a>Streszczenie

`dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file] [-s|--skip-project-references] [-r|--report-file] [--format-report-file-json] [--skip-backup] [-h|--help]`

## <a name="description"></a>Opis

`dotnet migrate` Polecenia migruje prawidłowy Preview 2 *project.json*— na podstawie projektu prawidłowy 1.0 zestawu SDK .NET Core *csproj* projektu. 

Domyślnie polecenia migruje głównego projektu i odwołań do projektu, które zawiera główny projekt. To zachowanie zostało wyłączone za pomocą `--skip-project-references` opcji w czasie wykonywania. 

Migracja odbywa się na następujących czynności:

* Pojedynczego projektu za pośrednictwem *project.json* plik do migracji.
* Wszystkie katalogi określone w *global.json* pliku, przekazując ścieżkę do *global.json* pliku.
* A *solution.sln* pliku, w którym migracją projektów w rozwiązaniu.
* Na wszystkie podkatalogi rekursywnie podanym katalogu.

`dotnet migrate` Polecenia śledzi migrowanych *project.json* pliku wewnątrz `backup` katalogu, który tworzy Jeśli katalog nie istnieje. To zachowanie jest zastępowany przy użyciu `--skip-backup` opcji.

Domyślnie operacji migracji Wyświetla stan procesu migracji na wyjście standardowe (STDOUT). Jeśli używasz `--report-file <REPORT_FILE>` opcji dane wyjściowe są zapisywane do pliku określić. 

`dotnet migrate` Polecenia obsługuje tylko prawidłowe Preview 2 *project.json*— na podstawie projektów. Oznacza to, że nie można użyć go do migracji DNX lub Preview 1 *project.json*— na podstawie projektów bezpośrednio do projektów MSBuild/csproj. Najpierw należy ręcznie wykonać migrację projektu do Preview 2 *project.json*— na podstawie projektu, a następnie użycie `dotnet migrate` polecenie, aby wykonać migrację projektu.

## <a name="arguments"></a>Argumenty

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Ścieżka do jednej z następujących czynności:

* *project.json* plik do migracji.
* *global.json* pliku, zostanie poddana migracji folderów określone w *global.json*.
* *solution.sln* pliku, zostaną zmigrowane projektów w rozwiązaniu.
* katalog, aby przeprowadzić migrację, zostanie on rekursywnie Wyszukaj *project.json* pliki migracji.

Wartość domyślna to bieżącego katalogu, jeśli nie określono żadnej wartości.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-t|--template-file <TEMPLATE_FILE>`

Plik csproj szablon do użycia na potrzeby migracji. Domyślnie tego samego szablonu co porzuconych przez `dotnet new console` jest używany.

`-v|--sdk-package-version <VERSION>`

Wersja pakietu sdk, który odwołuje się do migrowanych aplikacji. Wartość domyślna to wersja zestawu SDK w `dotnet new`.

`-x|--xproj-file <FILE>`

Ścieżka do pliku xproj do użycia. Wymagana, gdy istnieje więcej niż jeden xproj w katalogu projektu.

`-s|--skip-project-references [Debug|Release]`

Odwołuje się do migracji projektu SKIP. Domyślnie odwołania projektu są migrowane rekursywnie.

`-r|--report-file <REPORT_FILE>`

Raport migracji dane wyjściowe do pliku oprócz konsoli.

`--format-report-file-json <REPORT_FILE>`

Plik raportu migracji dane wyjściowe jako komunikaty JSON zamiast użytkownika.

`--skip-backup`

Pomiń przenoszenie *project.json*, *global.json*, i  *\*xproj* do `backup` katalogu po pomyślnej migracji.

## <a name="examples"></a>Przykłady

Migracja projekt w bieżącym katalogu i wszystkich jego zależności projektu do projektu:

`dotnet migrate`

Migracja wszystkich projektów, które *global.json* plik zawiera:

`dotnet migrate path/to/global.json`

Przeprowadź migrację tylko dla bieżącego projektu i bez zależności projektu do projektu (P2P). Ponadto należy użyć określonej wersji zestawu SDK:

`dotnet migrate -s -v 1.0.0-preview4`
