---
title: Rozwiązywanie problemów z korzystaniem z narzędzia .NET Core
description: Poznaj typowe problemy podczas uruchamiania narzędzi .NET Core i możliwych rozwiązań.
author: kdollard
ms.date: 02/14/2020
ms.openlocfilehash: ed6243f802c4d3ce56a742916a1a28676e3cd876
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146453"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a>Rozwiązywanie problemów z korzystaniem z narzędzia .NET Core

Możesz napotkać problemy podczas próby zainstalowania lub uruchomienia narzędzia .NET Core, które może być narzędziem globalnym lub lokalnym. W tym artykule opisano typowe przyczyny główne i niektóre możliwe rozwiązania.

## <a name="installed-net-core-tool-fails-to-run"></a>Nie można uruchomić narzędzia Installed .NET Core

Gdy narzędzie .NET Core nie działa, najprawdopodobniej napotkałeś jeden z następujących problemów:

* Nie znaleziono pliku wykonywalnego narzędzia.
* Nie znaleziono poprawnej wersji programu uruchomieniowego .NET Core.

### <a name="executable-file-not-found"></a>Nie znaleziono pliku wykonywalnego

Jeśli plik wykonywalny nie zostanie znaleziony, zostanie wyświetlony komunikat podobny do następującego:

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

Nazwa pliku wykonywalnego określa sposób wywoływania narzędzia. W poniższej tabeli opisano format:

| Format nazwy wykonywalnej  | Format wywołania   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* Narzędzia globalne

  Narzędzia globalne można instalować w katalogu domyślnym lub w określonej lokalizacji. Katalogi domyślne to:

  | System operacyjny          | Ścieżka                          |
  |-------------|-------------------------------|
  | Linux/macOS | `$HOME/.dotnet/tools`         |
  | Windows     | `%USERPROFILE%\.dotnet\tools` |

  Jeśli próbujesz uruchomić narzędzie globalne, sprawdź, czy zmienna `PATH` środowiskowa na komputerze zawiera ścieżkę, w której zainstalowano narzędzie globalne i czy plik wykonywalny znajduje się w tej ścieżce.

  Polecenie CLI programu .NET Core próbuje dodać domyślną lokalizację do zmiennej środowiskowej PATH przy pierwszym użyciu. Istnieją jednak pewne scenariusze, w których lokalizacja może nie zostać automatycznie dodana do PATH:

  * Jeśli używasz systemu Linux i zainstalowano sdk .NET Core przy użyciu plików *.tar.gz,* a nie apt-get lub rpm.
  * Jeśli używasz systemu macOS 10.15 "Catalina" lub nowsze wersje.
  * Jeśli używasz systemu macOS 10.14 "Mojave" lub wcześniejszych wersji, a pakiet SDK .NET Core został zainstalowany przy użyciu plików *.tar.gz,* a nie *.pkg*.
  * Jeśli zainstalowano zestaw SDK .NET Core 3.0 i `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` ustawiono zmienną środowiskową na `false`.
  * Jeśli zainstalowano zestaw SDK programu .NET Core 2.2 lub wcześniejsze `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` wersje, ustawiono zmienną środowiskową na `true`.

  W tych scenariuszach lub jeśli `--tool-path` określono `PATH` opcję, zmienna środowiskowa na komputerze nie zawiera automatycznie ścieżki, w której zainstalowano narzędzie globalne. W takim przypadku dołącz lokalizację narzędzia `$HOME/.dotnet/tools`(na `PATH` przykład) do zmiennej środowiskowej przy użyciu dowolnej metody, jaką zapewnia powłoka do aktualizowania zmiennych środowiskowych. Aby uzyskać więcej informacji, zobacz [narzędzia .NET Core](global-tools.md).

* Narzędzia lokalne

  Jeśli próbujesz uruchomić narzędzie lokalne, sprawdź, czy w bieżącym katalogu lub dowolnych katalogach nadrzędnych znajduje się plik manifestu o nazwie *dotnet-tools.json.* Ten plik może również działać w folderze o nazwie *.config* w dowolnym miejscu w hierarchii folderów projektu, a nie w folderze głównym. Jeśli *istnieje dotnet-tools.json,* otwórz go i sprawdź, czy narzędzie, które próbujesz uruchomić. Jeśli plik nie zawiera wpisu `"isRoot": true`dla , a następnie również sprawdzić dalej hierarchii plików dla dodatkowych plików manifestu narzędzia.

  Jeśli próbujesz uruchomić narzędzie .NET Core, które zostało zainstalowane z określoną ścieżką, musisz uwzględnić tę ścieżkę podczas korzystania z narzędzia. Przykładem użycia narzędzia zainstalowanego ścieżką narzędzia jest:

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a>Nie znaleziono czasu wykonywania

Narzędzia .NET Core są [aplikacjami zależnymi od struktury,](../deploying/index.md#publish-runtime-dependent)co oznacza, że opierają się na czasie uruchomieniowym .NET Core zainstalowanym na komputerze. Jeśli oczekiwany czas wykonywania nie zostanie znaleziony, są one zgodne z normalnymi regułami realizacji programu .NET Core, takimi jak:

* Aplikacja jest przerzucana do najwyższej wersji poprawki określonej wersji głównej i pomocniczej.
* Jeśli nie ma pasującego czasu uruchomieniowego z pasującym numerem wersji głównej i pomocniczej, używana jest następna wyższa wersja pomocnicza.
* Roll forward nie występuje między wersjami podglądu w czasie wykonywania lub między wersjami w wersji zapoznawczej i wersjami wersji. Tak, .NET Core narzędzia utworzone przy użyciu wersji podglądu muszą być przebudowane i ponownie opublikowane przez autora i ponownie zainstalować.

Roll-forward nie nastąpi domyślnie w dwóch typowych scenariuszach:

* Dostępne są tylko niższe wersje programu runtime. Roll-forward wybiera tylko nowsze wersje czasu wykonywania.
* Dostępne są tylko wyższe wersje główne programu runtime. Roll-forward nie przekracza granic głównych wersji.

Jeśli aplikacja nie może znaleźć odpowiedniego czasu uruchomienia, nie można uruchomić i zgłasza błąd.

Możesz dowiedzieć się, które programy uruchomieniowe programu .NET Core są zainstalowane na komputerze za pomocą jednego z następujących poleceń:

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

Jeśli uważasz, że narzędzie powinno obsługiwać aktualnie zainstalowaną wersję wykonywania, możesz skontaktować się z autorem narzędzia i sprawdzić, czy można zaktualizować numer wersji lub wiele celów. Po ponownym skompilowaniu i ponownym opublikowaniu pakietu narzędzi do NuGet ze zaktualizowanym numerem wersji można zaktualizować kopię. Chociaż tak się nie dzieje, najszybszym rozwiązaniem dla Ciebie jest zainstalowanie wersji czasu wykonywania, która będzie działać z narzędziem, które próbujesz uruchomić. Aby pobrać określoną wersję programu .NET Core, odwiedź [stronę pobierania .NET Core](https://dotnet.microsoft.com/download/dotnet-core).

Jeśli instalujesz zestaw SDK .NET Core w lokalizacji niedomyślnej, należy ustawić zmienną środowiskową `DOTNET_ROOT` na katalog zawierający `dotnet` plik wykonywalny.

## <a name="net-core-tool-installation-fails"></a>Instalacja narzędzia .NET Core nie powiodła się

Istnieje wiele przyczyn, dla których instalacja narzędzia globalnego lub lokalnego .NET Core może zakończyć się niepowodzeniem. Gdy instalacja narzędzia nie powiedzie się, zostanie wyświetlony komunikat podobny do następującego:

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

Aby ułatwić diagnozowanie tych błędów, komunikaty NuGet są wyświetlane bezpośrednio do użytkownika, wraz z poprzednim komunikatem. Komunikat NuGet może pomóc w zidentyfikowaniu problemu.

### <a name="package-naming-enforcement"></a>Wymuszanie nazewnictwa pakietów

Firma Microsoft zmieniła swoje wytyczne dotyczące identyfikatora pakietu dla narzędzi, co spowodowało, że wiele narzędzi nie zostało znalezionych z przewidywaną nazwą. Nowe wskazówki są takie, że wszystkie narzędzia firmy Microsoft są poprzedzone "Microsoft". Ten prefiks jest zarezerwowany i może być używany tylko dla pakietów podpisanych certyfikatem autoryzowanym przez firmę Microsoft.

Podczas przejścia niektóre narzędzia firmy Microsoft będą miały starą formę identyfikatora pakietu, podczas gdy inne będą miały nowy formularz:

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

W miarę aktualizowania identyfikatorów pakietów należy zmienić nowy identyfikator pakietu, aby otrzymywać najnowsze aktualizacje. Pakiety z uproszczoną nazwą narzędzia zostaną przestarzałe.

### <a name="preview-releases"></a>Wersje podglądu

* Próbujesz zainstalować wersję zawersji zapoznawczej `--version` i nie używasz opcji, aby określić wersję.

Narzędzia .NET Core, które są w wersji zapoznawczej, muszą być określone z częścią nazwy, aby wskazać, że są one w wersji zapoznawczej. Nie musisz dołączać całego podglądu. Zakładając, że numery wersji są w oczekiwanym formacie, można użyć czegoś takiego jak w poniższym przykładzie:

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a>Pakiet nie jest narzędziem .NET Core

* Znaleziono pakiet NuGet o tej nazwie, ale nie było to narzędzie .NET Core.

Jeśli spróbujesz zainstalować pakiet NuGet, który jest zwykłym pakietem NuGet, a nie narzędziem .NET Core, zobaczysz błąd podobny do następującego:

> NU1212: Nieprawidłowa kombinacja `<ToolName>`pakietu projektowego dla . Styl projektu DotnetToolReference może zawierać tylko odwołania do typu DotnetTool.

### <a name="nuget-feed-cant-be-accessed"></a>Nie można uzyskać dostępu do kanału NuGet

* Wymagany kanał nuget nie jest dostępny, być może z powodu problemu z połączeniem internetowym.

Instalacja narzędzia wymaga dostępu do źródła danych NuGet, który zawiera pakiet narzędzi. Nie powiedzie się, jeśli kanał nie jest dostępny. Można zmieniać kanały `nuget.config`informacyjne za `nuget.config` pomocą, żądać określonego `--add-source` pliku lub określać dodatkowe źródła danych za pomocą przełącznika. Domyślnie NuGet zgłasza błąd dla dowolnego źródła danych, który nie może się połączyć. Flaga `--ignore-failed-sources` może pominąć te nieosiągalne źródła.

### <a name="package-id-incorrect"></a>Identyfikator pakietu niepoprawny

* Nazwa narzędzia została błędnie wpisana.

Częstą przyczyną niepowodzenia jest to, że nazwa narzędzia nie jest poprawna. Może się to zdarzyć z powodu mistyping, lub dlatego, że narzędzie zostało przeniesione lub przestarzałe. W przypadku narzędzi na NuGet.org jednym ze sposobów upewnienia się, że nazwa jest poprawna, jest wyszukanie narzędzia w NuGet.org i skopiowanie polecenia instalacji.

## <a name="see-also"></a>Zobacz też

* [Narzędzia .NET Core](global-tools.md)
