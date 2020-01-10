---
title: Publikowanie aplikacji Hello world .NET Core przy użyciu programu Visual Studio
description: Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 485d62ce67f284fe1bbe931dcaa00671be154f35
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715372"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a>Publikowanie aplikacji Hello world .NET Core przy użyciu programu Visual Studio

W obszarze [Tworzenie aplikacji Hello World przy użyciu platformy .NET Core w programie Visual Studio](with-visual-studio.md)utworzono aplikację konsolową Hello World. W [debugowaniu aplikacji Hello World za pomocą programu Visual Studio](debugging-with-visual-studio.md)przetestowano ją przy użyciu debugera programu Visual Studio. Teraz, gdy masz pewność, że działa zgodnie z oczekiwaniami, możesz ją opublikować, tak aby inni użytkownicy mogli ją uruchamiać. Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji. Aby wdrożyć pliki, skopiuj je na maszynę docelową.

## <a name="publish-the-app"></a>Publikowanie aplikacji

1. Upewnij się, że program Visual Studio kompiluje wydaną wersję aplikacji. W razie potrzeby zmień ustawienie konfiguracji kompilacji na pasku narzędzi z **Debuguj** na **Release**.

   ![Program Visual Studio Toolbar z wybraną kompilacją wydania](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Kliknij prawym przyciskiem myszy projekt **HelloWorld** (nie rozwiązanie HelloWorld) i wybierz polecenie **Publikuj** z menu. (Możesz również wybrać opcję **Publikuj HelloWorld** z głównego menu **kompilacji** ).

   ![Menu kontekstowe publikacji programu Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)
   
1. Na stronie **Wybierz miejsce docelowe publikowania** wybierz pozycję **folder**, a następnie wybierz pozycję **Utwórz profil**.

   ![Wybieranie elementu docelowego publikowania w programie Visual Studio](media/publishing-with-visual-studio/pick-publish-target.png)
   
1. Na stronie **Publikowanie** wybierz pozycję **Publikuj**.

   ![Okno publikowania programu Visual Studio](media/publishing-with-visual-studio/publish-page.png)
   
## <a name="inspect-the-files"></a>Inspekcja plików

Proces publikowania tworzy wdrożenie zależne od platformy, które jest typem wdrożenia, w którym opublikowana aplikacja działa na dowolnej platformie obsługiwanej przez platformę .NET Core z zainstalowanym systemem .NET Core. Użytkownicy mogą uruchamiać opublikowaną aplikację przez dwukrotne kliknięcie pliku wykonywalnego lub wydawanie `dotnet HelloWorld.dll` polecenia z wiersza polecenia.

W poniższych krokach zawarto Podgląd plików utworzonych przez proces publikowania.

1. Otwórz wiersz polecenia.

   Jednym ze sposobów, aby otworzyć wiersz polecenia, jest wprowadzenie **wiersza polecenia** (lub **cmd** for Short) w polu wyszukiwania na pasku zadań systemu Windows. Wybierz pozycję **wiersz polecenia** aplikacja klasyczna lub naciśnij klawisz **Enter** , jeśli jest już zaznaczona w wynikach wyszukiwania.

1. Przejdź do opublikowanej aplikacji w podkatalogu *bin\Release\netcoreapp3.1\publish* w katalogu projektu aplikacji.

   ![Okno konsoli przedstawiające pliki opublikowane](media/publishing-with-visual-studio/published-files-output.png)

   W miarę wyświetlania obrazu opublikowane dane wyjściowe zawierają następujące pliki:

      * *HelloWorld.deps.json*

         Jest to plik zależności środowiska uruchomieniowego aplikacji. Definiuje składniki programu .NET Core i biblioteki (w tym bibliotekę dołączaną dynamicznie, która zawiera aplikację) potrzebną do uruchomienia aplikacji. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

      * *HelloWorld.dll*

         Jest to [zależna od platformy wersja wdrożenia](../deploying/deploy-with-cli.md#framework-dependent-deployment) aplikacji. Aby wykonać tę bibliotekę dołączaną dynamicznie, wprowadź `dotnet HelloWorld.dll` w wierszu polecenia.

      * *HelloWorld. exe*
      
         Jest to [zależna od struktury wersja pliku wykonywalnego](../deploying/deploy-with-cli.md#framework-dependent-executable) aplikacji. Aby go uruchomić, wprowadź `HelloWorld.exe` w wierszu polecenia.

      * *HelloWorld. pdb* (opcjonalnie dla wdrożenia)

         Jest to plik symboli debugowania. Nie musisz wdrażać tego pliku wraz z aplikacją, chociaż należy je zapisać w zdarzeniu, które trzeba debugować opublikowaną wersję aplikacji.

      * *HelloWorld.runtimeconfig.json*

         Jest to plik konfiguracji środowiska uruchomieniowego aplikacji. Identyfikuje wersję platformy .NET Core, w której aplikacja została skompilowana. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).

## <a name="additional-resources"></a>Dodatkowe zasoby

- [Wdrażanie aplikacji .NET core](../deploying/index.md)
