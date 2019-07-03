---
title: polecenia DotNet migracji polecenia
description: Migrowanie dotnet polecenia migrowana projekt i wszystkie jego zależności.
ms.date: 06/26/2019
ms.openlocfilehash: 3304f666d15d9188cdae76a401747d91791f817f
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539398"
---
# <a name="dotnet-migrate"></a>dotnet migrate

**Ten temat dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet migrate` -Wykonuje migrację projektów w wersji zapoznawczej 2 platformy .NET Core do projektu .NET Core SDK stylu.

> [!NOTE]
> `dotnet migrate` zostaną usunięte z zestawu .NET Core 3.0 SDK w następnej wersji (wersja zapoznawcza).

## <a name="synopsis"></a>Streszczenie

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a>Opis

`dotnet migrate` Polecenia migrowana prawidłowe 2 (wersja zapoznawcza) *project.json*— na podstawie projektu prawidłowy zestaw SDK platformy .NET Core — styl *csproj* projektu.

Domyślnie polecenie jest migrowana projektu głównego i odwołania do projektu, które zawiera projekt główny. To zachowanie jest wyłączone, za pomocą `--skip-project-references` opcji w czasie wykonywania.

Można wykonać migracji następujących zasobów:

* Pojedynczego projektu, określając *project.json* pliku migracji.
* Wszystkie katalogi określone w *global.json* pliku, przekazując ścieżkę do *global.json* pliku.
* A *przy* pliku, w którym przeprowadza migrację projektów, do którego odwołuje się rozwiązania.
* W podkatalogach cyklicznie danego katalogu.

`dotnet migrate` Polecenia utrzymuje zmigrowanych *project.json* pliku wewnątrz `backup` katalogu, który tworzy, jeśli katalog nie istnieje. To zachowanie jest zastępowany przy użyciu `--skip-backup` opcji.

Domyślnie operacji migracji Wyświetla stan procesu migracji do wyjścia standardowego (STDOUT). Jeśli używasz `--report-file <REPORT_FILE>` opcji dane wyjściowe są zapisywane do pliku określić.

`dotnet migrate` Prawidłowe 2 (wersja zapoznawcza) obsługuje tylko polecenia *project.json*— na projektach. Oznacza to, że nie można użyć go do migracji środowiska DNX lub 1 (wersja zapoznawcza) *project.json*— na projektach bezpośrednio do projektów MSBuild/csproj. Najpierw musisz ręcznie migrować projekt do wersji zapoznawczej 2 *project.json*— na podstawie projektu, a następnie użycie `dotnet migrate` polecenie, aby migrować projekt.

## <a name="arguments"></a>Argumenty

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Ścieżka do jednej z następujących czynności:

* *project.json* pliku migracji.
* *global.json* pliku: foldery określone w *global.json* są migrowane.
* *przy* pliku: projekty, do którego odwołuje się rozwiązania są migrowane.
* katalog do migracji: rekursywnie wyszukuje *project.json* plików, aby przeprowadzić migrację w określonym katalogu.

Wartość domyślna to bieżącego katalogu, jeśli nie określono żadnej wartości.

## <a name="options"></a>Opcje

`--format-report-file-json <REPORT_FILE>`

Dane wyjściowe pliku raportu migracji jako komunikaty JSON, a nie użytkownika.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-r|--report-file <REPORT_FILE>`

Raport migracji dane wyjściowe do pliku, oprócz konsoli.

`-s|--skip-project-references [Debug|Release]`

Odwołuje się do pomijania migracji projektu. Domyślnie odwołania do projektu są migrowane cyklicznie.

`--skip-backup`

Pomiń przenoszenie *project.json*, *global.json*, i  *\*xproj* do `backup` katalogu po pomyślnej migracji.

`-t|--template-file <TEMPLATE_FILE>`

Plik csproj szablonu do użycia podczas migracji. Domyślnie, tego samego szablonu co porzuconych przez `dotnet new console` jest używany.

`-v|--sdk-package-version <VERSION>`

Wersja pakietu sdk, w której podano odwołanie w migrowanych aplikacji. Wartość domyślna to wersja zestawu SDK w `dotnet new`.

`-x|--xproj-file <FILE>`

Ścieżka do pliku xproj do użycia. Wymagana, gdy istnieje więcej niż jeden xproj w katalogu projektu.

## <a name="examples"></a>Przykłady

Migracja projektu w bieżącym katalogu i wszystkich jego zależności projektu do projektu:

`dotnet migrate`

Migrowanie wszystkich projektów, które *global.json* plik zawiera:

`dotnet migrate path/to/global.json`

Przeprowadź migrację tylko bieżącego projektu i żadne zależności projektu do projektu (P2P). Ponadto należy użyć określonej wersji zestawu SDK:

`dotnet migrate -s -v 1.0.0-preview4`
