---
title: 'Samouczek: Instalowanie i używanie narzędzia globalnego .NET Core'
description: Dowiedz się, jak zainstalować narzędzie .NET i używać go jako narzędzia globalnego.
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156741"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a>Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

W tym samouczku nauczycię, jak zainstalować i używać globalnego narzędzia. Używasz narzędzia, które tworzysz w [pierwszym samouczku tej serii](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Wymagania wstępne

* Ukończ [pierwszy samouczek z tej serii](global-tools-how-to-create.md).

## <a name="use-the-tool-as-a-global-tool"></a>Używanie narzędzia jako narzędzia globalnego

1. Zainstaluj narzędzie z pakietu, uruchamiając polecenie [instalacji narzędzia dotnet](dotnet-tool-install.md) w folderze projektu *microsoft.botsay:*

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   Parametr `--global` informuje polecenie .NET Core CLI o zainstalowaniu plików binarnych narzędzi w lokalizacji domyślnej, która jest automatycznie dodawana do zmiennej środowiskowej PATH.

   Parametr `--add-source` informuje kontrolera CLI .NET Core o tymczasowym użyciu katalogu *./nupkg* jako dodatkowego źródła źródła dla pakietów NuGet. Nadasz pakietunikalną nazwę, aby upewnić się, że będzie ona dostępna tylko w katalogu *./nupkg,* a nie w Nuget.org witryny.

   Dane wyjściowe pokazuje polecenie używane do wywołania narzędzia i zainstalowana wersja:

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. Wywołaj narzędzie:

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > Jeśli to polecenie nie powiedzie się, może być konieczne otwarcie nowego terminalu w celu odświeżenia ŚCIEŻKI.

1. Usuń narzędzie, uruchamiając polecenie [odinstalowywania narzędzia dotnet:](dotnet-tool-uninstall.md)

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a>Używanie narzędzia jako narzędzia globalnego zainstalowanego w lokalizacji niestandardowej

1. Zainstaluj narzędzie z opakowania.

   W systemie Windows:

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   W systemie Linux lub macOS:

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   Parametr `--tool-path` informuje cli .NET Core o zainstalowaniu plików binarnych narzędzi w określonej lokalizacji. Jeśli katalog nie istnieje, jest tworzony. Ten katalog nie jest automatycznie dodawany do zmiennej środowiskowej PATH.

   Dane wyjściowe pokazuje polecenie używane do wywołania narzędzia i zainstalowana wersja:

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. Wywołaj narzędzie:

   W systemie Windows:

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   W systemie Linux lub macOS:

   ```console
   ~/bin/botsay hello from the bot
   ```

1. Usuń narzędzie, uruchamiając polecenie [odinstalowywania narzędzia dotnet:](dotnet-tool-uninstall.md)

   W systemie Windows:

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   W systemie Linux lub macOS:

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli podczas korzystania z samouczka zostanie wyświetlony komunikat o błędzie, zobacz [Rozwiązywanie problemów z używaniem narzędzia .NET Core](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Następne kroki

W tym samouczku zainstalowano i użyto narzędzia jako narzędzia globalnego. Aby zainstalować i używać tego samego narzędzia co narzędzie lokalne, przejdź do następnego samouczka.

> [!div class="nextstepaction"]
> [Instalowanie i używanie narzędzi lokalnych](local-tools-how-to-use.md)
