---
title: polecenie testu dotnet
description: Polecenie Test dotnet służy do wykonywania testów jednostkowych w danym projekcie.
ms.date: 05/29/2018
ms.openlocfilehash: c3115d546efb1f076ae9f9731f83a12183aa4154
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182518"
---
# <a name="dotnet-test"></a>dotnet test

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet test`— Sterownik testowy .NET używany do wykonywania testów jednostkowych.

## <a name="synopsis"></a>Streszczenie

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [--blame] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] 
    [-v|--verbosity] [-- <RunSettings arguments>]

dotnet test [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [--collect] [-d|--diag] [-f|--framework] [--filter]
    [-l|--logger] [--no-build] [--no-restore] [-o|--output] [-r|--results-directory] [-s|--settings] [-t|--list-tests] [-v|--verbosity]

dotnet test [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet test [<PROJECT>] [-a|--test-adapter-path] [-c|--configuration] [-d|--diag] [-f|--framework] [--filter] [-l|--logger] [--no-build] [-o|--output] [-s|--settings] [-t|--list-tests]  [-v|--verbosity]

dotnet test [-h|--help]
```

---

## <a name="description"></a>Opis

`dotnet test` Polecenie służy do wykonywania testów jednostkowych w danym projekcie. `dotnet test` Polecenie uruchamia aplikację konsolową Test Runner określoną dla projektu. Moduł uruchamiający testy wykonuje testy zdefiniowane dla struktury testów jednostkowych (na przykład MSTest, NUnit lub xUnit) i raportuje sukces lub niepowodzenie każdego testu. Jeśli wszystkie testy zakończą się pomyślnie, moduł uruchamiający testy zwraca 0 jako kod zakończenia; w przeciwnym razie, jeśli dowolny test zakończy się niepowodzeniem, zwraca 1. Moduł uruchamiający testy i Biblioteka testów jednostkowych są spakowane jako pakiety NuGet i są przywracane jako zwykłe zależności projektu.

Projekty testowe określają Test Runner przy użyciu zwykłego `<PackageReference>` elementu, jak pokazano w poniższym przykładowym pliku projektu:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

## <a name="arguments"></a>Argumenty

`PROJECT`

Ścieżka do projektu testowego. Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Użyj niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.

`--blame`

Uruchamia testy w trybie polecenia Blame. Ta opcja jest pomocna w odizolowaniu problematycznych testów powodujących awarię hosta testowego. Tworzy plik wyjściowy w bieżącym katalogu jako *Sequence. XML* , który przechwytuje kolejność testów przed awarią.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`, ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Włącza moduł zbierający dane dla przebiegu testu. Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku.

`-f|--framework <FRAMEWORK>`

Wyszukuje pliki binarne testów dla konkretnej [struktury](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia. Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) . Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`-l|--logger <LoggerUri/FriendlyName>`

Określa Rejestrator dla wyników testu.

`--no-build`

Nie kompiluje projektu testowego przed jego uruchomieniem. Również niejawne ustawia `--no-restore` flagę.

`--no-restore`

Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w którym można znaleźć pliki binarne do uruchomienia.

`-r|--results-directory <PATH>`

Katalog, w którym zostaną umieszczone wyniki testu. Jeśli określony katalog nie istnieje, zostanie utworzony.

`-s|--settings <SETTINGS_FILE>`

Plik `.runsettings` , który ma być używany do uruchamiania testów. [Skonfiguruj testy jednostkowe przy użyciu `.runsettings` pliku.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`

`RunSettings arguments`

Argumenty przekazane jako konfiguracje RunSettings dla testu. Argumenty są określane jako `[name]=[value]` pary po "--" (należy zwrócić uwagę na spację po--). Spacja jest używana do rozdzielania wielu `[name]=[value]` par.

Przykład: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

Aby uzyskać więcej informacji na temat runsettings [, zobacz VSTest. Console. exe: Przekazywanie argumentów](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)runsettings.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Użyj niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`, ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.

`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`

Włącza moduł zbierający dane dla przebiegu testu. Aby uzyskać więcej informacji, zobacz [monitorowanie i analizowanie przebiegu testowego](https://aka.ms/vstest-collect).

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku.

`-f|--framework <FRAMEWORK>`

Wyszukuje pliki binarne testów dla konkretnej [struktury](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia. Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) . Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`-l|--logger <LoggerUri/FriendlyName>`

Określa Rejestrator dla wyników testu.

`--no-build`

Nie kompiluje projektu testowego przed jego uruchomieniem. Również niejawne ustawia `--no-restore` flagę.

`--no-restore`

Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w którym można znaleźć pliki binarne do uruchomienia.

`-r|--results-directory <PATH>`

Katalog, w którym zostaną umieszczone wyniki testu. Jeśli określony katalog nie istnieje, zostanie utworzony.

`-s|--settings <SETTINGS_FILE>`

Plik `.runsettings` , który ma być używany do uruchamiania testów. [Skonfiguruj testy jednostkowe przy użyciu `.runsettings` pliku.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-a|--test-adapter-path <PATH_TO_ADAPTER>`

Użyj niestandardowych adapterów testowych z określonej ścieżki w przebiegu testu.

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`, ale Konfiguracja projektu może zastąpić to domyślne ustawienie zestawu SDK.

`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`

Włącza tryb diagnostyczny dla platformy testowej i zapisuje komunikaty diagnostyczne do określonego pliku.

`-f|--framework <FRAMEWORK>`

Wyszukuje pliki binarne testów dla konkretnej [struktury](../../standard/frameworks.md).

`--filter <EXPRESSION>`

Filtruje testy w bieżącym projekcie przy użyciu danego wyrażenia. Aby uzyskać więcej informacji, zobacz sekcję [szczegóły opcji filtrowania](#filter-option-details) . Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`-l|--logger <LoggerUri/FriendlyName>`

Określa Rejestrator dla wyników testu.

`--no-build`

Nie kompiluje projektu testowego przed jego uruchomieniem.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w którym można znaleźć pliki binarne do uruchomienia.

`-s|--settings <SETTINGS_FILE>`

Plik `.runsettings` , który ma być używany do uruchamiania testów. [Skonfiguruj testy jednostkowe przy użyciu `.runsettings` pliku.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)

`-t|--list-tests`

Wyświetl listę wszystkich odnalezionych testów w bieżącym projekcie.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`

---

## <a name="examples"></a>Przykłady

Uruchom testy w projekcie w bieżącym katalogu:

`dotnet test`

Uruchom testy w `test1` projekcie:

`dotnet test ~/projects/test1/test1.csproj`

Uruchom testy w projekcie w bieżącym katalogu i wygeneruj plik wyników testu w formacie TRX:

`dotnet test --logger trx`

## <a name="filter-option-details"></a>Szczegóły opcji filtrowania

`--filter <EXPRESSION>`

`<Expression>`ma format `<property><operator><value>[|&<Expression>]`.

`<property>`jest atrybutem `Test Case`klasy. Poniżej przedstawiono właściwości obsługiwane przez popularne struktury testów jednostkowych:

| Struktury testowej | Obsługiwane właściwości                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Nazwa</li><li>Nazwą</li><li>Priorytet</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>Cech</li></ul>                                   |

`<operator>` Opisuje relację między właściwością a wartością:

| Operator | Funkcja        |
| :------: | --------------- |
| `=`      | Dokładne dopasowanie     |
| `!=`     | Niedokładne dopasowanie |
| `~`      | Zawiera        |

`<value>`jest ciągiem. Wszystkie wyszukiwania są rozróżniane wielkości liter.

`<operator>` Wyrażenie bez elementu jest automatycznie uznawane `dotnet test --filter xyz` `contains` za Właściwość on `FullyQualifiedName` (na przykład jest takie samo jak `dotnet test --filter FullyQualifiedName~xyz`).

Wyrażenia mogą być dołączane za pomocą operatorów warunkowych:

| Operator            | Funkcja |
| ------------------- | -------- |
| <code>&#124;</code> | LUB       |
| `&`                 | AND      |

Wyrażenia można ująć w nawiasy, gdy są używane operatory warunkowe (na przykład `(Name~TestMethod1) | (Name~TestMethod2)`).

Aby uzyskać więcej informacji i zapoznać się z przykładami dotyczącymi używania selektywnego filtrowania testów jednostkowych, zobacz [Uruchamianie selektywnych testów jednostkowych](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Zobacz także

- [Struktury i elementy docelowe](../../standard/frameworks.md)
- [Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)](../rid-catalog.md)
