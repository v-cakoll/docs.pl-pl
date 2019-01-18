---
title: Publikowanie aplikacji platformy .NET Core Witaj, świecie przy użyciu programu Visual Studio 2017
description: Publikowanie tworzy zbiór plików, które są wymagane do uruchomienia aplikacji środowiska .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: ae202d8102d470e4260394f427e861750d4f0ee6
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362473"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio-2017"></a>Publikowanie aplikacji platformy .NET Core Witaj, świecie przy użyciu programu Visual Studio 2017

W [kompilacji C# aplikacji Hello World z platformą .NET Core w programie Visual Studio 2017](with-visual-studio.md) lub [tworzenie aplikacji Visual Basic Hello World z platformą .NET Core w programie Visual Studio 2017](vb-with-visual-studio.md), utworzoną aplikację konsolową w języku Hello World . W [debugowania języka C# aplikacji Hello World w programie Visual Studio 2017](debugging-with-visual-studio.md), przetestowane za pomocą debugera programu Visual Studio. Teraz, gdy masz pewność, że działa zgodnie z oczekiwaniami, możesz ją opublikować tak, aby uruchomić ją innym użytkownikom. Publikowanie tworzy zbiór plików, które są wymagane do uruchamiania aplikacji i plików można wdrożyć, kopiując je na komputerze docelowym.

Aby opublikować, a następnie uruchom aplikację: 

1. Upewnij się, że Visual Studio jest tworzenie wersji aplikacji. W razie potrzeby zmień ustawienie konfiguracji kompilacji, na pasku narzędzi z **debugowania** do **wersji**.

   ![Visual Studio pasek narzędzi z wybraną kompilacją wersji](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Kliknij prawym przyciskiem myszy **HelloWorld** projektu (nie rozwiązanie HelloWorld), a następnie wybierz **Publikuj** z menu. Możesz również wybrać **publikowania HelloWorld** z głównym programu Visual Studio **kompilacji** menu.

   ![Menu kontekstowe programu Visual Studio publikowania](media/publishing-with-visual-studio/publish-context-menu.png)


   ![Visual Studio publikowania okna](media/publishing-with-visual-studio/publish-settings-window.png)

1. Otwórz okno konsoli. Na przykład w **wpisz tutaj, aby wyszukać** tekstu pola na pasku zadań Windows, należy wprowadzić `Command Prompt` (lub `cmd` w skrócie) i Otwórz okno konsoli, wybierając **polecenia** pulpitu Aplikacja lub naciskając klawisz Enter, jeśli została wybrana w wynikach wyszukiwania.

1. Przejdź do aplikacji opublikowanych w `bin\release\PublishOutput` podkatalogu katalogu projektu aplikacji. Jak pokazano na poniższej ilustracji, opublikowane dane wyjściowe zawiera następujące cztery pliki:

      * *HelloWorld.deps.json*

         Plik zależności środowiska uruchomieniowego aplikacji. Definiuje składniki platformy .NET Core i bibliotek (w tym biblioteki dołączanej dynamicznie, która zawiera aplikację) potrzebnych do uruchomienia aplikacji. Aby uzyskać więcej informacji, zobacz [plików konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).
 
      * *HelloWorld.dll*

         Plik, który zawiera aplikację. Jest biblioteka dołączana dynamicznie, który może zostać wykonany, wprowadzając `dotnet HelloWorld.dll` polecenia w oknie konsoli. 

      * *HelloWorld.pdb* (opcjonalnie na potrzeby wdrożenia)

         Plik, który zawiera symbole debugowania. Aby wdrożyć ten plik, wraz z aplikacją, nie są wymagane, mimo że w przypadku, gdy konieczne zdebugowanie opublikowanej wersji aplikacji należy go zapisać.

      * *HelloWorld.runtimeconfig.json*

         Plik konfiguracji środowiska uruchomieniowego aplikacji. Go identyfikuje wersję programu .NET Core, która aplikacja została skompilowana do uruchamiania na. Aby uzyskać więcej informacji, zobacz [plików konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).  

   ![Wyświetlana plików publikowanych w oknie konsoli](media/publishing-with-visual-studio/published-files-output.png)

Proces publikowania tworzy wdrożenia zależny od struktury jest typu wdrożenia, gdzie opublikowana aplikacja jest uruchamiana na dowolnej platformie, obsługiwana przez platformy .NET Core za pomocą programu .NET Core, zainstalowane w systemie. Użytkownicy mogą uruchamiać aplikację, wysyłając `dotnet HelloWorld.dll` polecenia z okna konsoli.

Aby uzyskać więcej informacji na temat publikowania i wdrażania aplikacji .NET Core, zobacz [wdrożenie aplikacji programu .NET Core](../../core/deploying/index.md).
