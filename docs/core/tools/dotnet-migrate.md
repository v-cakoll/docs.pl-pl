---
title: polecenie migracji dotnet
description: Polecenie Migruj z programu dotnet migruje projekt i wszystkie jego zależności.
ms.date: 01/07/2020
ms.openlocfilehash: d746069b897a7458e0262663e96cc8743a586aa9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740515"
---
# <a name="dotnet-migrate"></a>dotnet migrate

**Ten artykuł dotyczy: ✓** .NET Core 1. x SDK **✓** .NET Core 2. x SDK

## <a name="name"></a>Nazwa

`dotnet migrate` — migruje projekt programu .NET Core w wersji zapoznawczej 2 do projektu w stylu zestaw .NET Core SDK.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a>Opis

To polecenie jest przestarzałe. Polecenie `dotnet migrate` nie jest już dostępne począwszy od zestawu SDK programu .NET Core 3,0. Może jedynie migrować projekt .NET Core w wersji zapoznawczej 2 do projektu 1. x platformy .NET Core, który nie jest obsługiwany.

Domyślnie polecenie migruje projekt główny i wszystkie odwołania do projektu, które zawiera projekt główny. To zachowanie jest wyłączone przy użyciu opcji `--skip-project-references` w czasie wykonywania.

Można przeprowadzić migrację na następujących zasobach:

* Pojedynczy projekt, określając plik *Project. JSON* do migracji.
* Wszystkie katalogi określone w pliku *Global. JSON* przez przekazanie ścieżki do pliku *Global. JSON* .
* Plik *. sln rozwiązania* , w którym migruje projekty, do których odwołuje się rozwiązanie.
* Wszystkie podkatalogi danego katalogu cyklicznie.

`dotnet migrate` polecenie zachowuje zmigrowany plik *Project. JSON* w katalogu `backup`, który tworzy, jeśli katalog nie istnieje. To zachowanie jest zastępowane przy użyciu opcji `--skip-backup`.

Domyślnie operacja migracji wyprowadza stan procesu migracji do wyjścia standardowego (STDOUT). Jeśli używasz opcji `--report-file <REPORT_FILE>`, dane wyjściowe są zapisywane w pliku Określ.

Polecenie `dotnet migrate` obsługuje tylko prawidłowe projekty w formacie *JSON*(wersja zapoznawcza 2). Oznacza to, że nie można używać go do migrowania środowiska DNX lub podglądu 1 projektów opartych na formacie *JSON*bezpośrednio do projektów MSBuild/csproj. Najpierw należy ręcznie zmigrować projekt do projektu w wersji zapoznawczej 2 *projektu. JSON*, a następnie użyć polecenia `dotnet migrate`, aby przeprowadzić migrację projektu.

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

Pomiń przenoszenie pliku *Project. JSON*, *Global. JSON*i *\*. xproj* do katalogu `backup` po pomyślnej migracji.

`-t|--template-file <TEMPLATE_FILE>`

Plik CSPROJ szablonu do użycia na potrzeby migracji. Domyślnie używany jest ten sam szablon, który został porzucony przez `dotnet new console`.

`-v|--sdk-package-version <VERSION>`

Wersja pakietu SDK, do którego odwołuje się migrowana aplikacja. Wartość domyślna to wersja zestawu SDK w `dotnet new`.

`-x|--xproj-file <FILE>`

Ścieżka do pliku xproj, który ma być używany. Wymagane, gdy w katalogu projektu znajduje się więcej niż jeden xproj.

## <a name="examples"></a>Przykłady

Migruj projekt w bieżącym katalogu i wszystkie jego zależności między projektami:

`dotnet migrate`

Migruj wszystkie projekty, które zawierają plik *Global. JSON* :

`dotnet migrate path/to/global.json`

Migruj tylko bieżący projekt i bez zależności projekt-projekt (P2P). Należy również użyć określonej wersji zestawu SDK:

`dotnet migrate -s -v 1.0.0-preview4`
