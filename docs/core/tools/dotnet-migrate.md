---
title: polecenie migracji dotnet
description: Polecenie migracji dotnetu migruje projekt i wszystkie jego zależności.
ms.date: 02/14/2020
ms.openlocfilehash: 6148048c469c43320cc4459352fd2fb62f101740
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503699"
---
# <a name="dotnet-migrate"></a>dotnet migrate

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK

## <a name="name"></a>Nazwa

`dotnet migrate`- Migruje projekt Preview 2 .NET Core do projektu w stylu .NET Core SDK.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a>Opis

To polecenie jest przestarzałe. Polecenie `dotnet migrate` nie jest już dostępne, począwszy od sdk .NET Core 3.0. Można migrować tylko podgląd 2 .NET Core projektu do 1.x .NET Core projektu, który jest bez obsługi.

Domyślnie polecenie migruje projekt główny i wszelkie odwołania do projektu, które zawiera projekt główny. To zachowanie jest wyłączone `--skip-project-references` przy użyciu opcji w czasie wykonywania.

Migracja może być wykonywana na następujących zasobach:

* Pojedynczy projekt, określając plik *project.json* do migracji.
* Wszystkie katalogi określone w pliku *global.json* przez przekazywanie w ścieżce do pliku *global.json.*
* Plik *solution.sln,* w którym przeprowadza migrację projektów, do których odwołuje się rozwiązanie.
* We wszystkich podkatalogach danego katalogu rekurencyjne.

Polecenie `dotnet migrate` przechowuje zmigrowany plik *project.json* wewnątrz `backup` katalogu, który tworzy, jeśli katalog nie istnieje. To zachowanie jest zastępowane `--skip-backup` przy użyciu tej opcji.

Domyślnie operacja migracji wyprowadza stan procesu migracji do standardowego wyjścia (STDOUT). Jeśli użyjesz `--report-file <REPORT_FILE>` tej opcji, dane wyjściowe zostaną zapisane w pliku określ.

Polecenie `dotnet migrate` obsługuje tylko prawidłowe projekty oparte na *programie Project.json*w wersji Preview 2. Oznacza to, że nie można go używać do migracji projektów opartych na programie DNX lub Preview 1 *project.json*bezpośrednio do projektów MSBuild/csproj. Najpierw należy ręcznie przeprowadzić migrację projektu do projektu opartego na projekcie Preview `dotnet migrate` *2,json,* a następnie użyć polecenia do migracji projektu.

## <a name="arguments"></a>Argumenty

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Ścieżka do jednej z następujących czynności:

* pliku *project.json* do migracji.
* plik *global.json:* foldery określone w *global.json* są migrowane.
* plik *solution.sln:* projekty, do których odwołuje się rozwiązanie, są migrowane.
* katalog do migracji: rekurencyjne wyszukiwanie plików *project.json* do migracji wewnątrz określonego katalogu.

Domyślnie do bieżącego katalogu, jeśli nic nie jest określone.

## <a name="options"></a>Opcje

`--format-report-file-json <REPORT_FILE>`

Plik raportu migracji wyjściowej jako JSON, a nie komunikaty użytkownika.

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`-r|--report-file <REPORT_FILE>`

Raport migracji wyjściowej do pliku oprócz konsoli.

`-s|--skip-project-references [Debug|Release]`

Pomiń migracji odwołań do projektu. Domyślnie odwołania do projektu są migrowane cyklicznie.

`--skip-backup`

Po zakończeniu migracji pomiń *przenoszenie project.json*, `backup` *global.json*i * \*.xproj* do katalogu.

`-t|--template-file <TEMPLATE_FILE>`

Szablon pliku csproj do użycia do migracji. Domyślnie używany jest ten sam szablon, który został usunięty. `dotnet new console`

`-v|--sdk-package-version <VERSION>`

Wersja pakietu sdk, do której odwołuje się zmigrowana aplikacja. Wartością domyślną jest wersja sdk w `dotnet new`.

`-x|--xproj-file <FILE>`

Ścieżka do pliku xproj do użycia. Wymagane, gdy w katalogu projektu znajduje się więcej niż jeden xproj.

## <a name="examples"></a>Przykłady

Migracja projektu w bieżącym katalogu i wszystkich jego zależności projektu do projektu:

`dotnet migrate`

Migracja wszystkich projektów, które zawiera plik *global.json:*

`dotnet migrate path/to/global.json`

Migracja tylko bieżącego projektu i żadnych zależności projektu do projektu (P2P). Należy również użyć określonej wersji sdk:

`dotnet migrate -s -v 1.0.0-preview4`
