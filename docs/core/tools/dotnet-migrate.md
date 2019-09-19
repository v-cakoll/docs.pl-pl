---
title: polecenie migracji dotnet
description: Polecenie Migruj z programu dotnet migruje projekt i wszystkie jego zależności.
ms.date: 08/08/2019
ms.openlocfilehash: afc16161761d151e743e53a8572a6564add43517
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117692"
---
# <a name="dotnet-migrate"></a>dotnet migrate

**Ten artykuł dotyczy: ✓** .NET Core 1. x SDK **✓** .NET Core 2. x SDK

## <a name="name"></a>Nazwa

`dotnet migrate`— Migruje projekt programu .NET Core w wersji zapoznawczej 2 do projektu w stylu zestaw .NET Core SDK.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a>Opis

Polecenie migruje prawidłowy projekt w wersji zapoznawczej 2 projekt *. JSON*do zestaw .NET Core SDK prawidłowego projektu csproj w stylu. `dotnet migrate`

Domyślnie polecenie migruje projekt główny i wszystkie odwołania do projektu, które zawiera projekt główny. To zachowanie jest wyłączone przy użyciu `--skip-project-references` opcji w czasie wykonywania.

Można przeprowadzić migrację na następujących zasobach:

* Pojedynczy projekt, określając plik *Project. JSON* do migracji.
* Wszystkie katalogi określone w pliku *Global. JSON* przez przekazanie ścieżki do pliku *Global. JSON* .
* Plik *. sln rozwiązania* , w którym migruje projekty, do których odwołuje się rozwiązanie.
* Wszystkie podkatalogi danego katalogu cyklicznie.

Polecenie zachowuje zmigrowany plik *Project. JSON* w `backup` katalogu, który tworzy, jeśli katalog nie istnieje. `dotnet migrate` To zachowanie jest zastępowane przy `--skip-backup` użyciu opcji.

Domyślnie operacja migracji wyprowadza stan procesu migracji do wyjścia standardowego (STDOUT). Jeśli używasz `--report-file <REPORT_FILE>` opcji, dane wyjściowe są zapisywane w pliku Określ.

Polecenie obsługuje tylko prawidłowe projekty w wersji zapoznawczej 2 dla *projektu.* `dotnet migrate` Oznacza to, że nie można używać go do migrowania środowiska DNX lub podglądu 1 projektów opartych na formacie *JSON*bezpośrednio do projektów MSBuild/csproj. Najpierw należy ręcznie zmigrować projekt do projektu w wersji zapoznawczej 2 *projektu. JSON*, a następnie użyć `dotnet migrate` polecenia w celu przeprowadzenia migracji projektu.

`dotnet migrate` Polecenie nie jest już dostępne począwszy od zestawu SDK programu .NET Core 3,0.

## <a name="arguments"></a>Argumenty

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

Ścieżka do jednego z następujących elementów:

* plik *Project. JSON* do migracji.
* plik *Global. JSON* : foldery określone w pliku *Global. JSON* są migrowane.
* plik *. sln rozwiązania* : projekty, do których odwołuje się rozwiązanie, są migrowane.
* Katalog do migracji: rekursywnie wyszukuje pliki *Project. JSON* do migracji w określonym katalogu.

Jeśli nie określono niczego, domyślnie jest używany bieżący katalog.

## <a name="options"></a>Opcje

`--format-report-file-json <REPORT_FILE>`

Wyjściowy plik raportu migracji w formacie JSON zamiast komunikatów użytkownika.

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`-r|--report-file <REPORT_FILE>`

Raport z migracji danych wyjściowych do pliku poza konsolą programu.

`-s|--skip-project-references [Debug|Release]`

Pomiń Migrowanie odwołań do projektu. Domyślnie odwołania do projektu są migrowane cyklicznie.

`--skip-backup`

Pomiń przenoszenie pliku`backup` *Project. JSON*, *Global. JSON*i  *\*. xproj* do katalogu po pomyślnej migracji.

`-t|--template-file <TEMPLATE_FILE>`

Plik CSPROJ szablonu do użycia na potrzeby migracji. Domyślnie używany jest ten sam szablon, który został usunięty przez `dotnet new console` .

`-v|--sdk-package-version <VERSION>`

Wersja pakietu SDK, do którego odwołuje się migrowana aplikacja. Wartość domyślna to wersja zestawu SDK w programie `dotnet new`.

`-x|--xproj-file <FILE>`

Ścieżka do pliku xproj, który ma być używany. Wymagane, gdy w katalogu projektu znajduje się więcej niż jeden xproj.

## <a name="examples"></a>Przykłady

Migruj projekt w bieżącym katalogu i wszystkie jego zależności między projektami:

`dotnet migrate`

Migruj wszystkie projekty, które zawierają plik *Global. JSON* :

`dotnet migrate path/to/global.json`

Migruj tylko bieżący projekt i bez zależności projekt-projekt (P2P). Należy również użyć określonej wersji zestawu SDK:

`dotnet migrate -s -v 1.0.0-preview4`
