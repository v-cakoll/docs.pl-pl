---
title: Narzędzia .NET Core
description: Jak zainstalować, używać, aktualizować i usuwać narzędzia programu .NET Core. Obejmuje narzędzia globalne, narzędzia ścieżki narzędzii i narzędzia lokalne.
author: KathleenDollard
ms.date: 02/12/2020
ms.openlocfilehash: 2f0101c6385c41eda49bcb2458428c1f14552617
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847793"
---
# <a name="how-to-manage-net-core-tools"></a>Jak zarządzać narzędziami programu .NET Core

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

Narzędzie .NET Core to specjalny pakiet NuGet zawierający aplikację konsoli. Narzędzie można zainstalować na komputerze w następujący sposób:

* Jako narzędzie globalne.

  Pliki binarne narzędzi są instalowane w katalogu domyślnym dodanym do zmiennej środowiskowej PATH. Narzędzie można wywołać z dowolnego katalogu na komputerze bez określania jego lokalizacji. Jedna wersja narzędzia jest używana dla wszystkich katalogów na maszynie.

* Jako narzędzie globalne w lokalizacji niestandardowej (nazywane również narzędziem ścieżki narzędzia).

  Pliki binarne narzędzi są instalowane w określonej lokalizacji. Narzędzie można wywołać z katalogu instalacyjnego lub podając katalog z nazwą polecenia lub dodając katalog do zmiennej środowiskowej PATH. Jedna wersja narzędzia jest używana dla wszystkich katalogów na maszynie.

* Jako narzędzie lokalne (dotyczy zestawu .NET Core SDK 3.0 i nowszych).

  Pliki binarne narzędzi są instalowane w katalogu domyślnym. Narzędzie wywołujesz z katalogu instalacyjnego lub dowolnego z jego podkatalogów. Różne katalogi mogą używać różnych wersji tego samego narzędzia.
  
  Polecenie CLI programu .NET używa plików manifestu do śledzenia, które narzędzia są instalowane jako lokalne w katalogu. Gdy plik manifestu jest zapisywany w katalogu głównym repozytorium kodu źródłowego, współautor może sklonować repozytorium i wywołać pojedyncze polecenie CLI .NET Core, które instaluje wszystkie narzędzia wymienione w plikach manifestu.

> [!IMPORTANT]
> Narzędzia .NET Core działają w pełnym zaufaniu. Nie instaluj narzędzia .NET Core, chyba że ufasz autorowi.

## <a name="find-a-tool"></a>Znajdowanie narzędzia

Obecnie program .NET Core nie ma funkcji wyszukiwania narzędzi. Oto kilka sposobów znajdowania narzędzi:

* Zobacz listę narzędzi w repozytorium GitHub [natemcmaster/dotnet-tools.](https://github.com/natemcmaster/dotnet-tools)
* Użyj [NarzędziaPobierz](https://www.toolget.net/) do wyszukiwania narzędzi .NET.
* Zobacz kod źródłowy narzędzi utworzonych przez zespół ASP.NET Core w [katalogu Narzędzia repozytorium GitHub dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).
* Dowiedz się więcej o narzędziach diagnostycznych w [narzędziach diagnostycznych .NET Core dotnet](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).
* Przeszukaj witrynę [NuGet.](https://www.nuget.org) Jednak nuget witryny nie ma jeszcze funkcji, która pozwala wyszukiwać tylko pakiety narzędzi.

## <a name="check-the-author-and-statistics"></a>Sprawdź autora i statystyki

Ponieważ narzędzia .NET Core działają w pełnym zaufaniu, a narzędzia globalne są dodawane do zmiennej środowiskowej PATH, mogą być bardzo wydajne. Nie pobieraj narzędzi od osób, którym nie ufasz.

Jeśli narzędzie jest hostowane na NuGet, można sprawdzić autora i statystyki, wyszukując narzędzie.

## <a name="install-a-global-tool"></a>Instalowanie narzędzia globalnego

Aby zainstalować narzędzie jako narzędzie `-g` globalne, należy użyć lub `--global` opcji [instalacji narzędzia dotnet](dotnet-tool-install.md), jak pokazano w poniższym przykładzie:

```dotnetcli
dotnet tool install -g dotnetsay
```

Dane wyjściowe pokazuje polecenie używane do wywołania narzędzia i zainstalowanej wersji, podobne do następującego przykładu:

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

Domyślna lokalizacja plików binarnych narzędzia zależy od systemu operacyjnego:

| System operacyjny          | Ścieżka                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Ta lokalizacja jest dodawana do ścieżki użytkownika po pierwszym uruchomieniu zestawu SDK, dzięki czemu można wywołać narzędzia globalne z dowolnego katalogu bez określania lokalizacji narzędzia.

Dostęp do narzędzi jest specyficzny dla użytkownika, a nie globalny. Narzędzie globalne jest dostępne tylko dla użytkownika, który zainstalował narzędzie.

### <a name="install-a-global-tool-in-a-custom-location"></a>Instalowanie narzędzia globalnego w lokalizacji niestandardowej

Aby zainstalować narzędzie jako narzędzie globalne w `--tool-path` lokalizacji niestandardowej, należy użyć opcji [instalacji narzędzia dotnet](dotnet-tool-install.md), jak pokazano w poniższych przykładach.

W systemie Windows:

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

W systemie Linux lub macOS:

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

Zestaw SDK .NET Core nie powoduje automatycznego dodania tej lokalizacji do zmiennej środowiskowej PATH. Aby [wywołać narzędzie ścieżki narzędzia,](#invoke-a-tool-path-tool)należy upewnić się, że polecenie jest dostępne przy użyciu jednej z następujących metod:

* Dodaj katalog instalacyjny do zmiennej środowiskowej PATH.
* Określ pełną ścieżkę do narzędzia podczas wywoływania go.
* Wywołaj narzędzie z poziomu katalogu instalacyjnego.

## <a name="install-a-local-tool"></a>Instalowanie narzędzia lokalnego

**Dotyczy sdk .NET Core 3.0 i nowszych.**

Aby zainstalować narzędzie tylko dla dostępu lokalnego (dla bieżącego katalogu i podkatalogów), należy je dodać do pliku manifestu narzędzia. Aby utworzyć plik manifestu `dotnet new tool-manifest` narzędzia, uruchom polecenie:

```dotnetcli
dotnet new tool-manifest
```

To polecenie tworzy plik manifestu o nazwie *dotnet-tools.json* w katalogu *.config.* Aby dodać narzędzie lokalne do pliku manifestu, użyj polecenia install `--global` tool `--tool-path` [dotnet](dotnet-tool-install.md) i **pomiń** opcje i opcje, jak pokazano w poniższym przykładzie:

```dotnetcli
dotnet tool install dotnetsay
```

Dane wyjściowe polecenia pokazuje, w którym pliku manifestu znajduje się nowo zainstalowane narzędzie, podobnie jak w poniższym przykładzie:

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

W poniższym przykładzie przedstawiono plik manifestu z zainstalowanymi dwoma narzędziami lokalnymi:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    },
    "dotnetsay": {
      "version": "2.1.3",
      "commands": [
        "dotnetsay"
      ]
    }
  }
}
```

Zazwyczaj dodaje się narzędzie lokalne do katalogu głównego repozytorium. Po zaewidencjonowanie w pliku manifestu do repozytorium deweloperzy, którzy wyewidencjonują kod z repozytorium, otrzymują najnowszy plik manifestu. Aby zainstalować wszystkie narzędzia wymienione w pliku manifestu, uruchomią `dotnet tool restore` polecenie:

```dotnetcli
dotnet tool restore
```

Dane wyjściowe wskazują, które narzędzia zostały przywrócone:

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a>Instalowanie określonej wersji narzędzia

Aby zainstalować wersję wstępną lub określoną wersję narzędzia, określ `--version` numer wersji przy użyciu tej opcji, jak pokazano w poniższym przykładzie:

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a>Korzystanie z narzędzia

Polecenie, którego używasz do wywoływania narzędzia, może się różnić od nazwy instalowany pakiet. Aby wyświetlić wszystkie narzędzia aktualnie zainstalowane na komputerze dla bieżącego użytkownika, użyj polecenia [listy narzędzi dotnet:](dotnet-tool-list.md)

```dotnetcli
dotnet tool list
```

Dane wyjściowe pokazują wersję i polecenie każdego narzędzia, podobne do następującego przykładu:

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

Jak pokazano w tym przykładzie, na liście są wyświetlane narzędzia lokalne. Aby wyświetlić narzędzia globalne, użyj `--global` tej opcji i zobacz `--tool-path` narzędzia ścieżki narzędzia, użyj tej opcji.

### <a name="invoke-a-global-tool"></a>Wywoływanie narzędzia globalnego

W przypadku narzędzi globalnych użyj polecenia narzędzia samodzielnie. Na przykład, jeśli `dotnetsay` polecenie `dotnet-doc`jest lub , to jest to, co można użyć do wywołania polecenia:

```console
dotnetsay
dotnet-doc
```

Jeśli polecenie zaczyna się `dotnet-`od prefiksu, alternatywnym sposobem `dotnet` wywołania narzędzia jest użycie polecenia i pominięcie prefiksu polecenia narzędzia. Na przykład, jeśli `dotnet-doc`polecenie jest , następujące polecenie wywołuje narzędzie:

```dotnetcli
dotnet doc
```

Jednak w poniższym scenariuszu `dotnet` nie można użyć polecenia do wywołania narzędzia globalnego:

* Narzędzie globalne i narzędzie lokalne mają to `dotnet-`samo polecenie poprzedzone .
* Chcesz wywołać narzędzie globalne z katalogu, który jest w zakresie narzędzia lokalnego.

W tym `dotnet doc` scenariuszu i `dotnet dotnet-doc` wywołać narzędzie lokalne. Aby wywołać narzędzie globalne, użyj polecenia samodzielnie:

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a>Wywoływanie narzędzia ścieżki narzędzia

Aby wywołać narzędzie globalne, które `tool-path` jest zainstalowane przy użyciu tej opcji, upewnij się, że polecenie jest dostępne, jak wyjaśniono [wcześniej w tym artykule](#install-a-global-tool-in-a-custom-location).

### <a name="invoke-a-local-tool"></a>Wywoływanie narzędzia lokalnego

Aby wywołać narzędzie lokalne, należy `dotnet` użyć polecenia z poziomu katalogu instalacyjnego. Można użyć formularza długiego (`dotnet tool run <COMMAND_NAME>`)`dotnet <COMMAND_NAME>`lub krótkiego formularza ( ), jak pokazano w poniższych przykładach:

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

Jeśli polecenie jest poprzedzone przez `dotnet-`, można dołączyć lub pominąć prefiks podczas wywoływania narzędzia. Na przykład jeśli polecenie `dotnet-doc`jest , każdy z poniższych przykładów wywołuje narzędzie lokalne:

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a>Aktualizowanie narzędzia

Aktualizacja narzędzia polega na odinstalowaniu i ponownym zainstalowaniu go za pomocą najnowszej stabilnej wersji. Aby zaktualizować narzędzie, użyj polecenia [aktualizacji narzędzia dotnet](dotnet-tool-update.md) z tą samą opcją, która została użyta do zainstalowania narzędzia:

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

W przypadku narzędzia lokalnego zestaw SDK znajduje pierwszy plik manifestu zawierający identyfikator pakietu, patrząc w bieżącym katalogu i katalogach nadrzędnych. Jeśli w żadnym pliku manifestu nie ma takiego identyfikatora pakietu, zestaw SDK dodaje nowy wpis do najbliższego pliku manifestu.

## <a name="uninstall-a-tool"></a>Odinstalowywanie narzędzia

Usuń narzędzie za pomocą polecenia [odinstalowywania narzędzia dotnet](dotnet-tool-uninstall.md) z tą samą opcją, która została użyta do zainstalowania narzędzia:

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path<packagename>
dotnet tool uninstall <packagename>
```

W przypadku narzędzia lokalnego zestaw SDK znajduje pierwszy plik manifestu zawierający identyfikator pakietu, patrząc w bieżącym katalogu i katalogach nadrzędnych.

## <a name="get-help-and-troubleshoot"></a>Uzyskiwanie pomocy i rozwiązywanie problemów

Aby uzyskać listę `dotnet tool` dostępnych poleceń, wprowadź następujące polecenie:

```dotnetcli
dotnet tool --help
```

Aby uzyskać instrukcje użycia narzędzia, wprowadź jedno z następujących poleceń lub zobacz witrynę sieci Web narzędzia:

```dotnetcli
<command> --help
dotnet <command> --help
```

Jeśli narzędzie nie może zostać zainstalowane lub uruchomione, zobacz [Rozwiązywanie problemów z używaniem narzędzia .NET Core](troubleshoot-usage-issues.md).

## <a name="see-also"></a>Zobacz też

- [Samouczek: Tworzenie narzędzia .NET Core przy użyciu procesora CLI programu .NET Core](global-tools-how-to-create.md)
- [Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core](global-tools-how-to-use.md)
- [Samouczek: Instalowanie i używanie lokalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core](local-tools-how-to-use.md)
