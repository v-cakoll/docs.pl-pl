---
title: Jak zainstalować narzędzie ML.NET Command-Line Interface (CLI)
description: Dowiedz się, jak zainstalować, uaktualnić, obniżyć i odinstalować narzędzie ML.NET interfejsu wiersza polecenia (CLI).
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 9f678c7117d32bf817139951db7eef2c3d0f5eb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848642"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>Jak zainstalować narzędzie ML.NET Command-Line Interface (CLI)

Dowiedz się, jak zainstalować ML.NET interfejsu wiersza polecenia (interfejsu wiersza polecenia) w systemie Windows, Mac lub Linux.

ML.NET CLI generuje dobrej jakości modele ML.NET i kod źródłowy przy użyciu automatycznego uczenia maszynowego (AutoML) i zestawu danych szkoleniowych.

> [!NOTE]
> Ten temat odnosi się do ML.NET cli i ML.NET AutoML, które są obecnie w wersji zapoznawczej, a materiał może ulec zmianie.

## <a name="pre-requisites"></a>Wymagania wstępne

- [Zestaw SDK .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- (Opcjonalnie) [Visual Studio 2017 lub 2019](https://visualstudio.microsoft.com/vs/)

Wygenerowane projekty kodu C# można uruchomić za `F5` pomocą programu `dotnet run` Visual Studio, naciskając klawisz lub za pomocą (.NET Core CLI).

Uwaga: Jeśli po zainstalowaniu [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` polecenie nie działa, wyloguj się z systemu Windows i zaloguj się ponownie.

## <a name="install"></a>Instalowanie

ML.NET CLI jest zainstalowany jak każde inne narzędzie globalne dotnet. Używasz polecenia `dotnet tool install` .NET Core CLI.

W poniższym przykładzie pokazano, jak zainstalować ML.NET cli w domyślnej lokalizacji kanału danych NuGet:

```dotnetcli
dotnet tool install -g mlnet
```

Jeśli nie można zainstalować narzędzia (oznacza to, że nie jest dostępne w domyślnym kanale NuGet), wyświetlane są komunikaty o błędach. Sprawdź, czy oczekiwane kanały są sprawdzane.

Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat z poleceniem użytym do wywołania narzędzia i zainstalowaną wersją, podobnie jak w poniższym przykładzie:

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

Można potwierdzić, że instalacja zakończyła się pomyślnie, wpisując następujące polecenie:

```console
mlnet
```

Powinna zostać wyświetlona pomoc dotycząca dostępnych poleceń dla narzędzia mlnet, takiego jak polecenie "auto-train".

## <a name="install-a-specific-release-version"></a>Instalowanie określonej wersji

Jeśli próbujesz zainstalować wersję w wersji wstępnej lub określoną wersję narzędzia, możesz określić [strukturę](../../standard/frameworks.md) w następującym formacie:

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

Można również sprawdzić, czy pakiet jest poprawnie zainstalowany, wpisując następujące polecenie:

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>Odinstalowywanie pakietu CLI

Wpisz następujące polecenie, aby odinstalować pakiet z komputera lokalnego:

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>Aktualizowanie pakietu CLI

Wpisz następujące polecenie, aby zaktualizować pakiet z komputera lokalnego:

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>Konfigurowanie sugestii cli (automatyczne uzupełnianie oparte na karcie)

Ponieważ ML.NET CLI jest `System.CommandLine`oparty na , ma wbudowaną obsługę uzupełniania kart.

Przykład działania automatycznego uzupełniania kart jest wyświetlany w następującej animacji:

![image](./media/cli-tab-completion.gif)

"Automatyczne uzupełnianie oparte na kartach" (sugestie parametrów) działa na *windows PowerShell* i *macOS /Linux bash,* ale nie będzie działać na *Windows CMD*.

Aby go włączyć, w bieżącej wersji zapoznawczej użytkownik końcowy musi wykonać kilka kroków raz na powłokę, opisane poniżej. Gdy to zrobisz, zakończenia będą działać `System.CommandLine` dla wszystkich aplikacji napisanych przy użyciu takich jak ML.NET CLI.

Na komputerze, na którym chcesz włączyć ukończenie, musisz wykonać dwie czynności.

1. Zainstaluj `dotnet-suggest` narzędzie globalne, uruchamiając następujące polecenie:

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. Dodaj odpowiedni skrypt podkładki do profilu powłoki. Może być trzeba utworzyć plik profilu powłoki. Skrypt składki przekaże żądania ukończenia `dotnet-suggest` z powłoki do `System.CommandLine`narzędzia, które przekazuje do odpowiedniej aplikacji opartej.

    - Dla bash, dodaj zawartość [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) do `~/.bash_profile`.

    - W przypadku programu PowerShell dodaj zawartość pliku [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) do profilu programu PowerShell. Oczekiwaną ścieżkę do profilu programu PowerShell można znaleźć, uruchamiając w konsoli następujące polecenie:

    ```console
    echo $profile
    ```

(W przypadku innych pocisków [poszukaj](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) lub otwórz [problem).](https://github.com/dotnet/System.CommandLine/issues)

## <a name="installation-directory"></a>Katalog instalacji

ML.NET CLI można zainstalować w katalogu domyślnym lub w określonej lokalizacji. Katalogi domyślne to:

| System operacyjny          | Ścieżka                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Te lokalizacje są dodawane do ścieżki użytkownika po pierwszym uruchomieniu sdk, więc narzędzia globalne zainstalowane tam mogą być wywoływane bezpośrednio.

Uwaga: Narzędzia globalne są specyficzne dla użytkownika, a nie globalne maszyny. Bycie specyficznym dla użytkownika oznacza, że nie można zainstalować narzędzia globalnego, które jest dostępne dla wszystkich użytkowników urządzenia. Narzędzie jest dostępne tylko dla każdego profilu użytkownika, w którym narzędzie zostało zainstalowane.

Narzędzia globalne można również zainstalować w określonym katalogu. Po zainstalowaniu w określonym katalogu użytkownik musi upewnić się, że polecenie jest dostępne, dołączając ten katalog do ścieżki, wywołując polecenie z określonym katalogiem lub wywołując narzędzie z określonego katalogu.
W takim przypadku .NET Core CLI nie dodaje tej lokalizacji automatycznie do zmiennej środowiskowej PATH.

## <a name="see-also"></a>Zobacz też

- [ML.NET przegląd cli](../automate-training-with-cli.md)
- [Samouczek: Analizowanie nastrojów za pomocą ML.NET interfejsu i ujścia interfejsu i odpowiedzialności](../tutorials/sentiment-analysis-cli.md)
- [ML.NET przewodnik po polecenia automatycznego pociągu cli](../reference/ml-net-cli-reference.md)
- [Telemetria w ML.NET CLI](../resources/ml-net-cli-telemetry.md)
