---
title: polecenie migracji dotnetu
description: Polecenie migracji dotnet migruje projekt i wszystkie jego zależności.
ms.date: 02/14/2020
ms.openlocfilehash: 71f587c1bfadd445aca818448bdd5f136f009fe0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463636"
---
# <a name="dotnet-migrate"></a>dotnet migrate

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK

## <a name="name"></a>Nazwa

`dotnet migrate`- Migruje projekt w wersji zapoznawczej 2 .NET Core do projektu w stylu sdk .NET Core.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json <REPORT_FILE>]
    [-r|--report-file <REPORT_FILE>] [-s|--skip-project-references [Debug|Release]]
    [--skip-backup] [-t|--template-file <TEMPLATE_FILE>] [-v|--sdk-package-version]
    [-x|--xproj-file]

dotnet migrate -h|--help
```

## <a name="description"></a>Opis

To polecenie jest przestarzałe. Polecenie `dotnet migrate` nie jest już dostępne począwszy od pliku .NET Core 3.0 SDK. Można przeprowadzić migrację tylko projektu programu Preview 2 .NET Core do projektu core 1.x .NET, który jest niew pomocy technicznej.

Domyślnie polecenie migruje projekt główny i wszelkie odwołania do projektu, które zawiera projekt główny. To zachowanie jest `--skip-project-references` wyłączone przy użyciu opcji w czasie wykonywania.

Migrację można przeprowadzić na następujących zasobach:

* Pojedynczy projekt, określając plik *project.json* do migracji.
* Wszystkie katalogi określone w pliku *global.json,* przechodząc w ścieżce do pliku *global.json.*
* Plik *solution.sln,* w którym migruje projekty, do których odwołuje się rozwiązanie.
* We wszystkich podkatalogach danego katalogu rekursywnie.

Polecenie `dotnet migrate` przechowuje zmigrowany plik *project.json* wewnątrz `backup` katalogu, który tworzy, jeśli katalog nie istnieje. To zachowanie jest zastępowane `--skip-backup` przy użyciu opcji.

Domyślnie operacja migracji wyprowadza stan procesu migracji do danych wyjściowych standardowych (STDOUT). Jeśli użyjesz `--report-file <REPORT_FILE>` tej opcji, dane wyjściowe są zapisywane w pliku określić.

Polecenie `dotnet migrate` obsługuje tylko prawidłowe projekty oparte na *programie Project.json*w wersji Preview 2. Oznacza to, że nie można go używać do migracji projektów opartych na programie DNX lub Preview 1 *project.json*bezpośrednio do projektów MSBuild/csproj. Najpierw należy ręcznie przeprowadzić migrację projektu do projektu opartego na programie Preview `dotnet migrate` 2 *project.json,* a następnie użyć polecenia do migracji projektu.

## <a name="arguments"></a>Argumenty

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Ścieżka do jednej z następujących czynności:

* pliku *project.json* do migracji.
* plik *global.json:* foldery określone w *pliku global.json* są migrowane.
* plik *solution.sln:* projekty, do których odwołuje się rozwiązanie, są migrowane.
* katalog do migracji: rekursywnie wyszukuje pliki *project.json* do migracji wewnątrz określonego katalogu.

Domyślnie bieżący katalog, jeśli nic nie jest określone.

## <a name="options"></a>Opcje

`--format-report-file-json <REPORT_FILE>`

Plik raportu migracji danych wyjściowych jako JSON, a nie wiadomości użytkownika.

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`-r|--report-file <REPORT_FILE>`

Raport migracji danych wyjściowych do pliku oprócz konsoli.

`-s|--skip-project-references [Debug|Release]`

Pomiń migrację odwołań do projektu. Domyślnie odwołania do projektu są migrowane rekursywnie.

`--skip-backup`

Po przemień przenoszenie *pliku project.json*, *global.json*i * \*.xproj* do katalogu po pomyślnej `backup` migracji.

`-t|--template-file <TEMPLATE_FILE>`

Szablon pliku csproj do użycia do migracji. Domyślnie używany jest ten sam `dotnet new console` szablon, który został usunięty przez.

`-v|--sdk-package-version <VERSION>`

Wersja pakietu sdk, do którego odwołuje się w zmigrowanym aplikacji. Domyślna jest wersja SDK `dotnet new`w pliku .

`-x|--xproj-file <FILE>`

Ścieżka do pliku xproj do użycia. Wymagane, gdy w katalogu projektu znajduje się więcej niż jeden xproj.

## <a name="examples"></a>Przykłady

Migrowanie projektu w bieżącym katalogu i wszystkich jego zależnościach między projektami:

`dotnet migrate`

Migrowanie wszystkich projektów, które zawiera plik *global.json:*

`dotnet migrate path/to/global.json`

Migrowanie tylko bieżącego projektu i bez zależności między projektem (P2P). Należy również użyć określonej wersji SDK:

`dotnet migrate -s -v 1.0.0-preview4`
