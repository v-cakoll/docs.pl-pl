---
title: Wprowadzenie do języka C# i Visual Studio Code — przewodnik C#
description: Informacje o sposobie tworzenia i debugowania w języku C# za pomocą programu Visual Studio Code pierwszej aplikacji platformy .NET Core.
author: kendrahavens
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: conceptual
ms.prod: .net
ms.technology: devlang-csharp
ms.workload:
- dotnetcore
ms.openlocfilehash: d4ee1c9ef66ef61156453786f65d16470d7a5ea2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-c-and-visual-studio-code"></a>Wprowadzenie do języka C# i Visual Studio Code

Oprogramowanie .NET core umożliwia szybka, modularna platforma do tworzenia aplikacji działających w systemach Windows, Linux i macOS. Za pomocą programu Visual Studio Code rozszerzenia C# Aby uzyskać zaawansowane edytowania z pełną obsługę funkcji IntelliSense języka C# (uzupełnianie kodu inteligentne) i debugowania.

## <a name="prerequisites"></a>Wymagania wstępne

1. Zainstaluj [kodu programu Visual Studio](https://code.visualstudio.com/).
2. Zainstaluj [.NET Core SDK](https://www.microsoft.com/net/download/core).
3. Zainstaluj [C# rozszerzenia](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp) dla programu Visual Studio Code. Aby uzyskać więcej informacji o sposobie instalowania rozszerzeń w Visual Studio Code, zobacz [VS kodu rozszerzenie Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).

## <a name="hello-world"></a>Witaj Świecie

Rozpocznijmy prosty program .NET Core "Hello World":

1. Otwórz projekt:

    * Otwórz kod programu Visual Studio.
    * Kliknij ikonę Explorer z menu po lewej stronie, a następnie kliknij przycisk **Otwórz Folder**.
    * Wybierz **pliku** > **Otwórz Folder** z poziomu menu głównego, aby otworzyć folder ma projektu C# w i kliknij przycisk **wybierz Folder**. W naszym przykładzie tworzymy folderu dla naszych projektu o nazwie *HelloWorld*.

      ![VSCodeOpenFolder](media/with-visual-studio-code/vscodeopenfolder.png)

2. Inicjowanie projektu C#:
    * Otwórz Terminal zintegrowane z kodem Visual Studio, wybierając **widoku** > **zintegrowane Terminal** z poziomu menu głównego.
    * W oknie terminalu wpisz `dotnet new console`.
    * To polecenie tworzy `Program.cs` plik w folderze z programem proste "Hello World" już zapisane razem z pliku projektu C# o nazwie `HelloWorld.csproj`.

      ![Nowe polecenie dotnet](media/with-visual-studio-code/dotnetnew.png)

3. Aby usunąć zasoby kompilacji:

    * Aby uzyskać **.NET Core 1.x**, typ `dotnet restore`. Uruchomiona `dotnet restore` zapewnia dostęp do wymagane pakiety platformy .NET Core, które są wymagane, aby skompilować projekt.

      ![Polecenie restore dotnet](media/with-visual-studio-code/dotnetrestore.png)

      [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

4. Uruchom program "Hello World":

    * Typ `dotnet run`. 

      ![Dotnet, uruchom polecenie](media/with-visual-studio-code/dotnetrun.png)

Można również obejrzeć krótki samouczek wideo, aby uzyskać dalszą pomoc Instalatora na [Windows](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core), [macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core-on-MacOS), lub [Linux](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

## <a name="debug"></a>Debugowanie

1. Otwórz *Program.cs* , klikając go. Przy pierwszym otwarciu pliku C# w programie Visual Studio Code, [OmniSharp](http://www.omnisharp.net/) ładuje w edytorze.

    ![Otwórz plik Program.cs](media/with-visual-studio-code/opencs.png)

2. Visual Studio Code powinien monit o dodanie brakujące zasoby do tworzenia i debugowanie aplikacji. Wybierz **tak**. 

    ![Monituj o brakujących zasobów](media/with-visual-studio-code/missing-assets.png)

3. Aby otworzyć widok debugowania, kliknij ikonę debugowanie z menu po lewej stronie.

    ![Otwórz kartę debugowania](media/with-visual-studio-code/opendebug.png)

4. Zlokalizuj zieloną strzałkę u góry okienka. Upewnij się, że ma listy rozwijanej obok niej `.NET Core Launch (console)` wybrane.

    ![Wybieranie platformy .NET Core](media/with-visual-studio-code/selectcore.png)

5. Dodaj punkt przerwania do projektu, klikając **marginesu edytora**, czyli miejsce po lewej stronie numerów wierszy w edytorze, obok wiersza 9.

    ![Ustawienia punktu przerwania](media/with-visual-studio-code/setbreakpoint.png)

6. Aby rozpocząć debugowanie, wybierz <kbd>F5</kbd> lub zieloną strzałkę. Debuger zatrzymuje wykonanie programu, po osiągnięciu punktu przerwania ustawionych w poprzednim kroku.
    * Podczas debugowania, możesz wyświetlić zmiennych lokalnych w górnym okienku po lewej stronie lub za pomocą konsoli debugowania.

    ![Uruchom i debugowania](media/with-visual-studio-code/rundebug.png)

7. Wybierz zieloną strzałkę u góry, aby kontynuować, debugowanie, lub czerwonego kwadratu u góry, aby zatrzymać.

> [!TIP] 
> Aby uzyskać więcej informacji oraz wskazówki na debugowanie .NET Core za pomocą OmniSharp w programie Visual Studio Code, zobacz [instrukcje dotyczące konfigurowania debuger .NET Core](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).

## <a name="see-also"></a>Zobacz także
[Konfigurowanie programu Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)   
[Profilowanie kodu Visual Studio](https://code.visualstudio.com/Docs/editor/debugging)
