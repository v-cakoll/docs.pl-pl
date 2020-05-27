---
title: Publikowanie aplikacji Hello world .NET Core przy użyciu programu Visual Studio
description: Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: e4ef8c12f3e52faa7cf09058a98abae65b0dcfce
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005116"
---
# <a name="tutorial-publish-a-net-core-console-application-with-visual-studio"></a>Samouczek: publikowanie aplikacji konsolowej .NET Core za pomocą programu Visual Studio

W tym samouczku pokazano, jak opublikować aplikację konsolową, tak aby inni użytkownicy mogli ją uruchomić. Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji. Aby wdrożyć pliki, skopiuj je na maszynę docelową.

## <a name="prerequisites"></a>Wymagania wstępne

- Ten samouczek współpracuje z aplikacją konsolową utworzoną w temacie [Tworzenie aplikacji konsolowej platformy .NET Core w programie Visual Studio 2019](with-visual-studio.md).

## <a name="publish-the-app"></a>Publikowanie aplikacji

1. Upewnij się, że program Visual Studio kompiluje wydaną wersję aplikacji. W razie potrzeby zmień ustawienie konfiguracji kompilacji na pasku narzędzi z **Debuguj** na **Release**.

   ![Program Visual Studio Toolbar z wybraną kompilacją wydania](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Kliknij prawym przyciskiem myszy projekt **HelloWorld** (nie rozwiązanie HelloWorld) i wybierz polecenie **Publikuj** z menu.

   ![Menu kontekstowe publikacji programu Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

1. Na karcie **Target** strony **Publikowanie** wybierz pozycję **folder**, a następnie wybierz pozycję **dalej**.

   ![Wybieranie elementu docelowego publikowania w programie Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)

1. Na karcie **Lokalizacja** strony **Publikowanie** wybierz pozycję **Zakończ**.

   ![Karta Lokalizacja strony publikacji programu Visual Studio](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. Na karcie **Publikowanie** okna **Publikowanie** wybierz pozycję **Publikuj**.

   ![Okno publikowania programu Visual Studio](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a>Inspekcja plików

Proces publikowania tworzy wdrożenie zależne od platformy, które jest typem wdrożenia, w którym jest uruchomiona opublikowana aplikacja na komputerze z zainstalowanym środowiskiem uruchomieniowym .NET Core. Użytkownicy mogą uruchamiać opublikowaną aplikację przez dwukrotne kliknięcie pliku wykonywalnego lub wydawanie `dotnet HelloWorld.dll` polecenia z wiersza polecenia.

W poniższych krokach zawarto Podgląd plików utworzonych przez proces publikowania.

1. W **Eksplorator rozwiązań**wybierz opcję **Pokaż wszystkie pliki**.

1. W folderze projektu rozwiń węzeł *bin/Release/netcoreapp 3.1/Publish*.

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="Eksplorator rozwiązań wyświetlania opublikowanych plików":::

   W miarę wyświetlania obrazu opublikowane dane wyjściowe zawierają następujące pliki:

      * *HelloWorld. deps. JSON*

         Jest to plik zależności środowiska uruchomieniowego aplikacji. Definiuje składniki programu .NET Core i biblioteki (w tym bibliotekę dołączaną dynamicznie, która zawiera aplikację) potrzebną do uruchomienia aplikacji. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

      * *HelloWorld. dll*

         Jest to [zależna od platformy wersja wdrożenia](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikacji. Aby wykonać tę bibliotekę dołączaną dynamicznie, wprowadź `dotnet HelloWorld.dll` w wierszu polecenia.

      * *HelloWorld. exe*

         Jest to [zależna od struktury wersja pliku wykonywalnego](../deploying/deploy-with-cli.md#framework-dependent-executable) aplikacji. Aby uruchomić tę opcję, wprowadź `HelloWorld.exe` w wierszu polecenia.

      * *HelloWorld. pdb* (opcjonalnie dla wdrożenia)

         Jest to plik symboli debugowania. Nie musisz wdrażać tego pliku wraz z aplikacją, chociaż należy je zapisać w zdarzeniu, które trzeba debugować opublikowaną wersję aplikacji.

      * *HelloWorld. runtimeconfig. JSON*

         To jest plik konfiguracji czasu wykonywania aplikacji. Identyfikuje wersję platformy .NET Core, w której aplikacja została skompilowana. Możesz również dodać do niej opcje konfiguracji. Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).

## <a name="run-the-published-app"></a>Uruchom opublikowaną aplikację

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy folder *Publikowanie* , a następnie wybierz polecenie **Kopiuj pełną ścieżkę**.

1. Otwórz wiersz polecenia i przejdź do folderu *Publikowanie* . Wprowadź `cd` i wklej pełną ścieżkę. Przykład:

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. Uruchom aplikację przy użyciu pliku wykonywalnego:

   1. Wprowadź `HelloWorld.exe` i naciśnij klawisz ENTER.

   1. Wprowadź nazwę w odpowiedzi na monit, a następnie naciśnij dowolny klawisz, aby wyjść.

1. Uruchom aplikację za pomocą `dotnet` polecenia:

   1. Wprowadź `dotnet HelloWorld.dll` i naciśnij klawisz ENTER.

   1. Wprowadź nazwę w odpowiedzi na monit, a następnie naciśnij dowolny klawisz, aby wyjść.

## <a name="additional-resources"></a>Zasoby dodatkowe

- [Wdrażanie aplikacji .NET Core](../deploying/index.md)

## <a name="next-steps"></a>Następne kroki

W tym samouczku opublikowano aplikację konsolową. W następnym samouczku utworzysz bibliotekę klas.

> [!div class="nextstepaction"]
> [Tworzenie biblioteki .NET Standard w programie Visual Studio](library-with-visual-studio.md)
