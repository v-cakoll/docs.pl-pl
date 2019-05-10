---
title: Jak zainstalować narzędzie strukturze ML.NET interfejsu wiersza polecenia (CLI)
description: Omówienie i instalacja narzędzia strukturze ML.NET interfejsu wiersza polecenia (CLI).
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 869c443d519557c9d3976676047e63a4a072d2d3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066236"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>Jak zainstalować narzędzie strukturze ML.NET interfejsu wiersza polecenia (CLI)

Strukturze ML.NET interfejsu wiersza polecenia (interfejsu wiersza polecenia) jest narzędziem, które można uruchomić na dowolnym wiersza polecenia (Windows, Mac lub Linux) generowania modeli strukturze ML.NET dobrej jakości i kodu źródłowego, w oparciu o zestawów danych szkoleniowych, których udzielasz.

> [!NOTE]
> W tym temacie odnosi się do interfejsu wiersza polecenia w strukturze ML.NET i strukturze ML.NET AutoML, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.

## <a name="pre-requisites"></a>Wymagania wstępne

- [.NET core SDK 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- (Opcjonalnie) [Visual Studio 2017 lub 2019 r](https://visualstudio.microsoft.com/vs/)

Aplikację możesz uruchomić wygenerowany C# projekty z Visual Studio F5 lub kodu `dotnet run` (.NET Core interfejsu wiersza polecenia).

Uwaga: Jeśli po zainstalowaniu [zestawu .NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` polecenie nie działa, wyloguj się z Windows i zalogować się ponownie.

## <a name="install"></a>Zainstaluj

Interfejs wiersza polecenia strukturze ML.NET zainstalowano podobnie jak wszystkie inne polecenia dotnet narzędzie globalne. Możesz użyć `dotnet tool install` polecenia interfejsu wiersza polecenia platformy .NET Core. 

Poniższy przykład pokazuje, jak do zainstalowania interfejsu wiersza polecenia strukturze ML.NET w domyślnym, który NuGet kanału informacyjnego lokalizacji:

```console
> dotnet tool install -g mlnet
```

Jeśli nie można zainstalować narzędzia, (to znaczy, jeśli nie jest dostępny na domyślne, które NuGet źródła danych), zostaną wyświetlone komunikaty o błędach. Sprawdź, że źródła danych, które miały są sprawdzane.

Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat przedstawiający polecenia używane do wywoływania narzędzia i wersją zainstalowaną, podobny do poniższego przykładu:

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

Można potwierdzić, że instalacja zakończyła się pomyślnie, wpisując następujące polecenie:

```console
> mlnet
```

Pomoc dla dostępnych poleceń dla narzędzia mlnet, takie jak polecenie "auto-train" powinien być widoczny.

## <a name="install-a-specific-release-version"></a>Instalowanie określonej wersji

Jeśli próbujesz zainstalować wersję wstępną lub określoną wersję narzędzia, można określić numeru wersji w następującym formacie:

```console
> dotnet tool install -g <package-name> --version <version-number>
```

Możesz również sprawdzić, jeśli pakiet jest prawidłowo zainstalowany, wpisując następujące polecenie:

```console
> dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>Odinstaluj pakiet interfejsu wiersza polecenia

Wpisz następujące polecenie, aby odinstalować pakiet z komputera lokalnego:

```console
> dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>Aktualizuj pakiet interfejsu wiersza polecenia

Wpisz następujące polecenie, aby zaktualizować pakiet z komputera lokalnego:

```console
> dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>Konfigurowanie interfejsu wiersza polecenia sugestie (oparte na karcie automatycznego uzupełniania)

Interfejs wiersza polecenia strukturze ML.NET jest tworzony na podstawie `System.CommandLine`, ma wbudowaną obsługę uzupełniania po naciśnięciu tabulatora.

Przykład sposobu działania uzupełniania po naciśnięciu tabulatora automatycznie jest pokazana w animacji następujące:

![obraz](./media/cli-tab-completion.gif)

"Oparte na karcie automatycznego uzupełniania" (parametr sugestie) działa na *programu Windows PowerShell* i *bash systemu macOS/Linux* , ale nie będzie działać na *Windows CMD*.

Aby ją włączyć, w bieżącej wersji zapoznawczej, użytkownik końcowy musi wykonać kilka czynności, raz na shell w opisany poniżej. Po zakończeniu tej operacji uzupełnienia będzie działać dla wszystkich aplikacji napisanych z użyciem `System.CommandLine` takich jak strukturze ML.NET interfejsu wiersza polecenia.

Na komputerze, na którym chcesz włączyć uzupełnianie należy wykonać dwie czynności.

1. Zainstaluj `dotnet-suggest` narzędzie globalne, uruchamiając następujące polecenie:

    ```console
    > dotnet tool install dotnet-suggest -g
    ```

2. Dodaj skrypt podkładki odpowiednie do swojego profilu powłoki. Użytkownik może być konieczne utworzenie pliku profilu powłoki. Skrypt podkładki przekaże żądania zakończenia z powłoki do `dotnet-suggest` narzędzia, który deleguje do odpowiedniego `System.CommandLine`— na podstawie aplikacji.

    * W przypadku powłoki bash, należy dodać zawartość [dotnet zasugerować shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) do `~/.bash_profile`.

    * W przypadku programu PowerShell, należy dodać zawartość [dotnet zasugerować shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) do Twojego profilu programu PowerShell. Oczekiwaną ścieżką do Twojego profilu programu PowerShell można znaleźć, uruchamiając następujące polecenie w konsoli:

    ```console
    > echo $profile
    ``` 

(Dla innych powłoki [poszukaj](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) lub Otwórz [problem](https://github.com/dotnet/System.CommandLine/issues).)

## <a name="installation-directory"></a>Katalog instalacyjny

Strukturze ML.NET interfejsu wiersza polecenia można zainstalować w domyślnym katalogu lub w określonej lokalizacji. Domyślne katalogi są następujące:

| System operacyjny          | Ścieżka                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Te lokalizacje są dodawane do ścieżki użytkownika podczas pierwszego uruchomienia zestaw SDK, więc globalnego narzędzia są zainstalowane, może być wywoływana bezpośrednio.

Uwaga: narzędzia globalne są specyficzne dla użytkownika, nie machine globalnego. Są specyficzne dla użytkownika oznacza, że nie można zainstalować narzędzie globalne, która jest dostępna dla wszystkich użytkowników komputera. Narzędzie jest dostępne tylko dla każdego profilu użytkownika którym zostało zainstalowane narzędzie.

Można również zainstalować narzędzia globalnej w określonym katalogu. Podczas instalowania w określonym katalogu, użytkownik musi upewnić się polecenie jest dostępne, umieszczając tego katalogu w ścieżce, wywołując polecenie z katalogu, który został określony, lub podczas wywoływania narzędzia z w określonym katalogu.
W tym przypadku interfejsu wiersza polecenia platformy .NET Core nie powoduje dodania tej lokalizacji automatycznie do zmiennej środowiskowej PATH.

## <a name="see-also"></a>Zobacz także

- [Samouczek dotyczący "Wprowadzenie za pomocą narzędzia interfejsu wiersza polecenia w strukturze ML.NET"](../tutorials/mlnet-cli.md)
- [Jak automatycznie uczenia modeli za pomocą narzędzia interfejsu wiersza polecenia w strukturze ML.NET](../automate-training-with-cli.md)
- [Podręcznik interfejsu wiersza polecenia w strukturze ML.NET train automatycznie poleceń](../reference/ml-net-cli-reference.md) 
- [Dane telemetryczne w interfejsie wiersza polecenia w strukturze ML.NET](../resources/ml-net-cli-telemetry.md)
