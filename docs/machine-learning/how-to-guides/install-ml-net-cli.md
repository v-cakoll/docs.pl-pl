---
title: Jak zainstalować narzędzie ML.NET interfejsu wiersza polecenia (CLI)
description: Omówienie i instalacja narzędzia ML.NET interfejsu wiersza polecenia (CLI).
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 8b6de466a6cf72b44a16c80fc024671bc4e975e8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106901"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>Jak zainstalować narzędzie ML.NET interfejsu wiersza polecenia (CLI)

Interfejs wiersza polecenia ML.NET — narzędzie, które można uruchomić w dowolnym wierszu polecenia (Windows, Mac lub Linux) w celu wygenerowania dobrej jakości modeli ML.NET i kodu źródłowego na podstawie podanych szkoleń.

> [!NOTE]
> Ten temat dotyczy ML.NET interfejsu wiersza polecenia i ML.NET AutoML, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.

## <a name="pre-requisites"></a>Wymagania wstępne

- [Zestaw SDK platformy .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- Obowiązkowe [Visual Studio 2017 lub 2019](https://visualstudio.microsoft.com/vs/)

Można uruchomić wygenerowane C# projekty kodu za pomocą programu Visual Studio F5 lub z `dotnet run` (interfejs wiersza polecenia platformy .NET Core).

Uwaga: Jeśli po zainstalowaniu [zestawu .NET Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` polecenie nie działa, Wyloguj się z systemu Windows i zaloguj się ponownie.

## <a name="install"></a>Zainstaluj

Interfejs wiersza polecenia ML.NET jest instalowany jak każdy inny narzędzie globalne dotnet. Używasz polecenia interfejs wiersza polecenia platformy .NET Core `dotnet tool install` . 

Poniższy przykład pokazuje, jak zainstalować interfejs wiersza polecenia ML.NET w domyślnej lokalizacji źródła danych NuGet:

```console
dotnet tool install -g mlnet
```

Jeśli nie można zainstalować narzędzia (czyli jeśli nie jest ono dostępne w domyślnym źródle danych NuGet), wyświetlane są komunikaty o błędach. Sprawdź, czy wybrane źródła danych są sprawdzane.

Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat z poleceniem, które służy do wywoływania narzędzia i zainstalowanej wersji, podobnie jak w poniższym przykładzie:

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

Można potwierdzić, że instalacja zakończyła się pomyślnie, wpisując następujące polecenie:

```console
mlnet
```

Powinna zostać wyświetlona Pomoc dotycząca dostępnych poleceń dla narzędzia mlnet, takiego jak polecenie "autouczenie".

## <a name="install-a-specific-release-version"></a>Zainstaluj określoną wersję wydania

Jeśli próbujesz zainstalować wersję wstępną lub określoną wersję narzędzia, możesz określić [strukturę](../../standard/frameworks.md) przy użyciu następującego formatu:

```console
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

Możesz również sprawdzić, czy pakiet jest prawidłowo zainstalowany, wpisując następujące polecenie:

```console
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>Odinstalowywanie pakietu interfejsu wiersza polecenia

Wpisz następujące polecenie, aby odinstalować pakiet z komputera lokalnego:

```console
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>Aktualizowanie pakietu interfejsu wiersza polecenia

Wpisz następujące polecenie, aby zaktualizować pakiet z komputera lokalnego:

```console
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>Konfigurowanie sugestii interfejsu wiersza polecenia (funkcja automatycznego uzupełniania oparta na kartach)

Ponieważ interfejs wiersza polecenia ml.NET jest oparty `System.CommandLine`na systemie, ma wbudowaną obsługę uzupełniania kart.

Przykład sposobu, w jaki działa funkcja automatycznego uzupełniania kart, jest pokazana w następującej animacji:

![obraz](./media/cli-tab-completion.gif)

"Autouzupełnianie oparte na kartach" (sugestie dotyczące parametrów) działają w programie *Windows PowerShell* i *macOS/Linux bash* , ale nie będzie działać w programie *Windows cmd*.

Aby włączyć tę funkcję, w bieżącej wersji zapoznawczej użytkownik końcowy musi wykonać kilka kroków raz na powłokę poniżej. Po wykonaniu tych czynności uzupełnianie będzie działało dla wszystkich aplikacji, które `System.CommandLine` zostały utworzone przy użyciu takiego interfejsu wiersza polecenia ml.NET.

Na komputerze, na którym chcesz włączyć uzupełnianie, musisz wykonać dwie czynności.

1. Zainstaluj narzędzie `dotnet-suggest` globalne, uruchamiając następujące polecenie:

    ```console
    dotnet tool install dotnet-suggest -g
    ```

2. Dodaj odpowiedni skrypt podkładki do profilu powłoki. Może być konieczne utworzenie pliku profilu powłoki. Skrypt podkładki przekaże żądania ukończenia z powłoki do `dotnet-suggest` narzędzia, które deleguje do odpowiedniej `System.CommandLine`aplikacji opartej na usłudze.

    - W przypadku bash Dodaj zawartość elementu [dotnet-sugerował-podkładkę. bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) do `~/.bash_profile`.

    - W przypadku programu PowerShell Dodaj zawartość [dotnet-Suggest-Shim. ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) do profilu programu PowerShell. Oczekiwaną ścieżkę do profilu programu PowerShell można znaleźć, uruchamiając następujące polecenie w konsoli programu:

    ```console
    echo $profile
    ``` 

(W przypadku innych powłok należy [](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) poszukać lub otworzyć [problem](https://github.com/dotnet/System.CommandLine/issues)).

## <a name="installation-directory"></a>Katalog instalacji

Interfejs wiersza polecenia ML.NET można zainstalować w katalogu domyślnym lub w określonej lokalizacji. Domyślne katalogi są następujące:

| OS          | Ścieżka                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Te lokalizacje są dodawane do ścieżki użytkownika podczas pierwszego uruchomienia zestawu SDK, dzięki czemu globalne narzędzia mogą być wywoływane bezpośrednio.

Uwaga: globalne narzędzia to specyficzne dla użytkownika, a nie globalne maszyny. Specyficzne dla użytkownika oznacza, że nie można zainstalować narzędzia globalnego, które jest dostępne dla wszystkich użytkowników komputera. Narzędzie jest dostępne tylko dla każdego profilu użytkownika, w którym zainstalowano narzędzie.

Narzędzia globalne można także zainstalować w określonym katalogu. Po zainstalowaniu w określonym katalogu użytkownik musi upewnić się, że polecenie jest dostępne, dołączając ten katalog w ścieżce, wywołując polecenie z określonym katalogiem lub wywołując narzędzie z w określonym katalogu.
W takim przypadku interfejs wiersza polecenia platformy .NET Core nie dodaje automatycznie tej lokalizacji do zmiennej środowiskowej PATH.

## <a name="see-also"></a>Zobacz także

- [Samouczek dotyczący "Wprowadzenie za pomocą narzędzia interfejsu wiersza polecenia ML.NET"](../tutorials/mlnet-cli.md)
- [Jak automatycznie uczenie modeli za pomocą narzędzia interfejsu wiersza polecenia ML.NET](../automate-training-with-cli.md)
- [Przewodnik dotyczący poleceń autouczenia interfejsu wiersza polecenia ML.NET](../reference/ml-net-cli-reference.md) 
- [Dane telemetryczne w interfejsie wiersza polecenia ML.NET](../resources/ml-net-cli-telemetry.md)
