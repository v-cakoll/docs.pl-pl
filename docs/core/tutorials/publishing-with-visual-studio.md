---
title: Publikowanie aplikacji Hello World z programu Visual Studio 2017 r.
description: Publikowanie tworzy zestaw plików, które są wymagane do uruchamiania aplikacji.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.workload:
- dotnetcore
ms.openlocfilehash: f3cecbd39ee557a620cd779bdff6b630642e7f56
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a>Publikowanie aplikacji Hello World z programu Visual Studio 2017 r.

W [tworzenia aplikacji C# Hello World z platformą .NET Core w Visual Studio 2017](with-visual-studio.md) lub [tworzenia aplikacji Visual Basic Hello World z platformą .NET Core w Visual Studio 2017](vb-with-visual-studio.md), wbudowane Hello World aplikacji konsoli . W [debugowania aplikacji C# Hello World z programu Visual Studio 2017](debugging-with-visual-studio.md), przetestować go za pomocą debugera programu Visual Studio. Teraz, gdy masz pewność, że działa zgodnie z oczekiwaniami, można opublikować, aby uruchomić go innym użytkownikom. Publikowanie tworzy zestaw plików, które są wymagane do uruchamiania aplikacji i plików można wdrożyć, kopiując je na komputerze docelowym.

Aby opublikować i uruchom aplikację: 

1. Upewnij się, że program Visual Studio tworzy wersji aplikacji. W razie potrzeby zmień ustawienia konfiguracji kompilacji na pasku narzędzi z **debugowania** do **wersji**.

   ![Visual Studio paska narzędzi](media/publishing-with-visual-studio/toolbar.png)

1. Kliknij prawym przyciskiem myszy **HelloWorld** projektu (nie rozwiązanie HelloWorld) i wybierz **publikowania** z menu. Możesz też wybrać **publikowania HelloWorld** z głównym programu Visual Studio **kompilacji** menu.

   ![Visual Studio paska narzędzi](media/publishing-with-visual-studio/publish1.png)


   ![Visual Studio paska narzędzi](media/publishing-with-visual-studio/publishwindow.png)

1. Otwórz okno konsoli. Na przykład w **wpisz tutaj, aby wyszukać** tekst pola na pasku zadań systemu Windows, wprowadź `Command Prompt` (lub `cmd` skrócie) i Otwórz okno konsoli wybierając **wiersza polecenia** pulpitu Aplikacja lub naciskając klawisz Enter, jeśli jest zaznaczona w wynikach wyszukiwania.

1. Przejdź do opublikowanych aplikacji w `bin\release\PublishOutput` podkatalogu w katalogu projektu. Jak pokazano na poniższej ilustracji, opublikowanych danych wyjściowych zawiera cztery następujące pliki:

      * *HelloWorld.deps.json*

         Plik zależności środowiska uruchomieniowego aplikacji. Definiuje składników platformy .NET Core i bibliotek (w tym biblioteki dołączanej dynamicznie, która zawiera aplikację) wymagane do uruchamiania aplikacji. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).
 
      * *HelloWorld.dll*

         Plik, który zawiera aplikację. Jest biblioteką dołączaną dynamicznie, który może zostać wykonany, wprowadzając `dotnet HelloWorld.dll` polecenie w oknie konsoli. 

      * *HelloWorld.pdb* (opcjonalny w przypadku wdrażania)

         Plik, który zawiera symbole debugowania. Nie są wymagane do wdrożenia tego pliku wraz z aplikacji, ale należy zapisać go w przypadku, gdy trzeba debugowania opublikowanej wersji aplikacji.

      * *HelloWorld.runtimeconfig.json*

         Plik konfiguracji środowiska uruchomieniowego aplikacji. Identyfikuje wersję platformy .NET Core, utworzony aplikacji do uruchamiania na. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).  

   ![Wyświetlanie plików publikowanych okna konsoli](media/publishing-with-visual-studio/publishedfiles.png)

Proces publikowania tworzy wdrożenia zależne od framework jest typ wdrożenia, którym opublikowana aplikacja będzie działać w żadnej platformy obsługiwanej przez oprogramowanie .NET Core z platformą .NET Core zainstalowane w systemie. Użytkownicy mogą korzystać z aplikacji, wysyłając `dotnet HelloWorld.dll` polecenie z poziomu okna konsoli.

Aby uzyskać więcej informacji dotyczących publikowania i wdrażania aplikacji .NET Core, zobacz [wdrażanie aplikacji .NET Core](../../core/deploying/index.md).
