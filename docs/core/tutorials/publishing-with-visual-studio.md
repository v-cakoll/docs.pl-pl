---
title: Publikowanie aplikacji Hello world .NET Core przy użyciu programu Visual Studio 2017
description: Publikowanie tworzy zestaw plików, które są konieczne do uruchomienia aplikacji .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f8c37f47cc8dfb999f2371773a50c2dd91e074a5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660472"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio-2017"></a>Publikowanie aplikacji Hello world .NET Core przy użyciu programu Visual Studio 2017

W obszarze [Kompilowanie aplikacji C# Hello World z platformą .NET Core w programie Visual Studio 2017](with-visual-studio.md) lub Kompilowanie [Visual Basic Hello World aplikacji przy użyciu platformy .net core w programie Visual Studio 2017](vb-with-visual-studio.md)skompilowano aplikację konsolową Hello World. W [debugowaniu C# aplikacji Hello World za pomocą programu Visual Studio 2017](debugging-with-visual-studio.md)przetestowano go za pomocą debugera programu Visual Studio. Teraz, gdy masz pewność, że działa zgodnie z oczekiwaniami, możesz ją opublikować, tak aby inni użytkownicy mogli ją uruchamiać. Publikowanie tworzy zestaw plików, które są potrzebne do uruchomienia aplikacji, i można wdrożyć pliki, kopiując je na maszynę docelową.

Aby opublikować i uruchomić aplikację: 

1. Upewnij się, że program Visual Studio kompiluje wydaną wersję aplikacji. W razie potrzeby zmień ustawienie konfiguracji kompilacji na pasku narzędzi z **Debuguj** na **Release**.

   ![Program Visual Studio Toolbar z wybraną kompilacją wydania](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Kliknij prawym przyciskiem myszy projekt **HelloWorld** (nie rozwiązanie HelloWorld) i wybierz polecenie **Publikuj** z menu. Możesz również wybrać pozycję **Publikuj HelloWorld** z głównego menu **kompilacji** programu Visual Studio.

   ![Menu kontekstowe publikacji programu Visual Studio](media/publishing-with-visual-studio/publish-context-menu.png)

   ![Okno publikowania programu Visual Studio](media/publishing-with-visual-studio/publish-settings-window.png)

1. Otwórz okno konsoli. Na przykład w polu tekstowym **Wpisz tutaj, aby** wyszukać na pasku zadań systemu `Command Prompt` Windows wpisz `cmd` (lub w skrócie), a następnie otwórz okno konsoli, wybierając **polecenie Wiersz polecenia** aplikacji klasycznej lub naciskając klawisz ENTER, jeśli jest ono zaznaczone w Wyniki wyszukiwania.

1. Przejdź do opublikowanej aplikacji w `bin\release\PublishOutput` podkatalogu katalogu projektu aplikacji. Jak widać na poniższej ilustracji, opublikowane dane wyjściowe obejmują następujące cztery pliki:

      * *HelloWorld.deps.json*

         Plik zależności środowiska uruchomieniowego aplikacji. Definiuje składniki programu .NET Core i biblioteki (w tym bibliotekę dołączaną dynamicznie, która zawiera aplikację) potrzebną do uruchomienia aplikacji. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).
 
      * *HelloWorld.dll*

         Plik, który zawiera aplikację. Jest to biblioteka dołączana dynamicznie, którą można wykonać, wprowadzając `dotnet HelloWorld.dll` polecenie w oknie konsoli. 

      * *HelloWorld. pdb* (opcjonalnie dla wdrożenia)

         Plik, który zawiera symbole debugowania. Nie musisz wdrażać tego pliku wraz z aplikacją, chociaż należy je zapisać w zdarzeniu, które trzeba debugować opublikowaną wersję aplikacji.

      * *HelloWorld.runtimeconfig.json*

         Plik konfiguracji środowiska uruchomieniowego aplikacji. Identyfikuje wersję platformy .NET Core, w której aplikacja została skompilowana. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).  

   ![Okno konsoli przedstawiające pliki opublikowane](media/publishing-with-visual-studio/published-files-output.png)

Proces publikowania tworzy wdrożenie zależne od platformy, które jest typem wdrożenia, w którym opublikowana aplikacja będzie działać na dowolnej platformie obsługiwanej przez platformę .NET Core z zainstalowanym systemem .NET Core. Użytkownicy mogą uruchamiać aplikację, wydając `dotnet HelloWorld.dll` polecenie z okna konsoli.

Aby uzyskać więcej informacji o publikowaniu i wdrażaniu aplikacji platformy .NET Core, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).
