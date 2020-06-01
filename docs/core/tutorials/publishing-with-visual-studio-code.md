---
title: Publikowanie aplikacji Hello world .NET Core przy użyciu Visual Studio Code
description: Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji .NET Core.
ms.date: 05/28/2020
ms.openlocfilehash: b49b12bf41e3ea7be8dbc459eb7d9b1fbef25790
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84246683"
---
# <a name="tutorial-publish-a-net-core-console-application-with-visual-studio-code"></a>Samouczek: publikowanie aplikacji konsolowej .NET Core za pomocą Visual Studio Code

W tym samouczku pokazano, jak opublikować aplikację konsolową, tak aby inni użytkownicy mogli ją uruchomić. Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji. Aby wdrożyć pliki, skopiuj je na maszynę docelową.

Interfejs wiersza polecenia platformy .NET Core jest używany do publikowania aplikacji, więc możesz wykonać czynności opisane w tym samouczku z edytorem kodu innym niż Visual Studio Code, jeśli wolisz.

## <a name="prerequisites"></a>Wymagania wstępne

- Ten samouczek współpracuje z aplikacją konsolową utworzoną w temacie [Tworzenie aplikacji konsolowej platformy .NET Core w Visual Studio Code](with-visual-studio-code.md).

## <a name="publish-the-app"></a>Publikowanie aplikacji

1. Otwórz program Visual Studio Code.

1. Otwórz folder projektu *HelloWorld* , który został utworzony w temacie [Tworzenie aplikacji konsolowej platformy .net Core w Visual Studio Code](with-visual-studio-code.md).

1. Wybierz pozycję **Wyświetl**  >  **Terminal** z menu głównego.

   Terminal zostanie otwarty w folderze *HelloWorld* .

1. Uruchom następujące polecenie:

   ```dotnetcli
   dotnet publish --configuration Release
   ```

   Domyślną konfiguracją kompilacji jest *debugowanie*, dlatego to polecenie określa konfigurację kompilacji *wydania* . Dane wyjściowe z konfiguracji kompilacji wydania zawierają minimalne informacje dotyczące debugowania symbolicznego i są w pełni zoptymalizowane.

   Dane wyjściowe polecenia są podobne do poniższego przykładu:

   ```
   Microsoft (R) Build Engine version 16.6.0+5ff7b0c9e for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.

   Determining projects to restore...
   All projects are up-to-date for restore.
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\HelloWorld.dll
   HelloWorld -> C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

## <a name="inspect-the-files"></a>Inspekcja plików

Domyślnie proces publikowania tworzy wdrożenie zależne od platformy, które jest typem wdrożenia, w którym jest uruchomiona opublikowana aplikacja na komputerze z zainstalowanym środowiskiem uruchomieniowym .NET Core. Aby uruchomić opublikowaną aplikację, można użyć pliku wykonywalnego lub uruchomić `dotnet HelloWorld.dll` polecenie z wiersza polecenia.

W poniższych krokach zawarto Podgląd plików utworzonych przez proces publikowania.

1. Wybierz **Eksploratora** na lewym pasku nawigacyjnym.

1. Rozwiń gałąź *bin/Release/netcoreapp 3.1/Publish*.

   :::image type="content" source="media/publishing-with-visual-studio-code/published-files-output.png" alt-text="Eksplorator przedstawiający opublikowane pliki":::

   W miarę wyświetlania obrazu opublikowane dane wyjściowe zawierają następujące pliki:

   * *HelloWorld. deps. JSON*

      Jest to plik zależności środowiska uruchomieniowego aplikacji. Definiuje składniki programu .NET Core i biblioteki (w tym bibliotekę dołączaną dynamicznie, która zawiera aplikację) potrzebną do uruchomienia aplikacji. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

   * *HelloWorld. dll*

      Jest to [zależna od platformy wersja wdrożenia](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikacji. Aby wykonać tę bibliotekę dołączaną dynamicznie, wprowadź `dotnet HelloWorld.dll` w wierszu polecenia. Ta metoda uruchamiania aplikacji działa na dowolnej platformie, na której zainstalowano środowisko uruchomieniowe platformy .NET Core.

   * *HelloWorld. exe* (*HelloWorld* w systemie Linux, nie utworzono w witrynie macOS).

      Jest to [zależna od struktury wersja pliku wykonywalnego](../deploying/deploy-with-cli.md#framework-dependent-executable) aplikacji. Plik działa w systemie operacyjnym.

   * *HelloWorld. pdb* (opcjonalnie dla wdrożenia)

      Jest to plik symboli debugowania. Nie musisz wdrażać tego pliku wraz z aplikacją, chociaż należy je zapisać w zdarzeniu, które trzeba debugować opublikowaną wersję aplikacji.

   * *HelloWorld. runtimeconfig. JSON*

      To jest plik konfiguracji czasu wykonywania aplikacji. Identyfikuje wersję platformy .NET Core, w której aplikacja została skompilowana. Możesz również dodać do niej opcje konfiguracji. Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).

## <a name="run-the-published-app"></a>Uruchom opublikowaną aplikację

1. W **Eksploratorze**kliknij prawym przyciskiem myszy folder *Publikowanie* (lub <kbd>naciśnij klawisz Ctrl</kbd>i kliknij pozycję macOS), a następnie wybierz pozycję **Otwórz w terminalu**.

   :::image type="content" source="media/publishing-with-visual-studio-code/open-in-terminal.png" alt-text="Menu kontekstowe pokazujące otwarty w terminalu":::

1. W systemie Windows lub Linux Uruchom aplikację przy użyciu pliku wykonywalnego.

   1. W systemie Windows wpisz `.\HelloWorld.exe` i naciśnij klawisz <kbd>Enter</kbd>.

   1. W systemie Linux wpisz `./HelloWorld` i naciśnij klawisz <kbd>Enter</kbd>.

   1. Wprowadź nazwę w odpowiedzi na monit, a następnie naciśnij dowolny klawisz, aby wyjść.

1. Na dowolnej platformie Uruchom aplikację za pomocą [`dotnet`](../tools/dotnet.md) polecenia:

   1. Wprowadź `dotnet HelloWorld.dll` i naciśnij klawisz <kbd>Enter</kbd>.

   1. Wprowadź nazwę w odpowiedzi na monit, a następnie naciśnij dowolny klawisz, aby wyjść.

## <a name="additional-resources"></a>Dodatkowe zasoby

- [Wdrażanie aplikacji .NET Core](../deploying/index.md)

## <a name="next-steps"></a>Następne kroki

W tym samouczku opublikowano aplikację konsolową. Aby dowiedzieć się, jak tworzyć biblioteki, zobacz [tworzenie bibliotek przy użyciu interfejs wiersza polecenia platformy .NET Core](libraries.md).

<!--In the next tutorial, you create a class library.

> [!div class="nextstepaction"]
> [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md)
-->
