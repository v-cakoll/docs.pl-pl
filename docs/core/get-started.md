---
title: Rozpoczynanie pracy z platformą .NET Core
description: Znajdź zasoby, aby dowiedzieć się, jak do kompilowania aplikacji platformy .NET Core w systemie Windows, Linux i macOS.
author: thraka
ms.author: adegeo
ms.date: 06/27/2018
ms.openlocfilehash: 2ec7f57250db8779552305b2ee69cbcf1db55d0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614161"
---
# <a name="get-started-with-net-core"></a>Rozpoczynanie pracy z platformą .NET Core

Ten artykuł zawiera informacje na temat rozpoczynania pracy z platformą .NET Core. .NET core można zainstalować na Windows, Linux i macOS. Można programować w swoim ulubionym edytorze tekstów i tworzenia bibliotek dla wielu platform i aplikacji. 

Jeśli wiesz nowości platformy .NET Core lub jak on odnosi się do innych technologii .NET, skorzystaj z [co to jest .NET](https://www.microsoft.com/net/learn/dotnet/what-is-dotnet) Przegląd. Najprościej mówiąc, .NET Core jest implementacją open source, dla wielu platform .NET.

## <a name="create-an-application"></a>Tworzenie aplikacji

Najpierw należy pobrać i zainstalować [zestawu .NET Core SDK](https://www.microsoft.com/net/download/) na tym komputerze.

Następnie otwórz terminal, takich jak **PowerShell**, **polecenia**, lub **bash**. Wpisz następujące polecenie `dotnet` polecenia, aby utworzyć i uruchomić aplikację w języku C#.

```console
dotnet new console --output sample1
dotnet run --project sample1
```

Powinny zostać wyświetlone następujące dane wyjściowe:

```console
Hello World!
```

Gratulacje! Utworzono prostą aplikację platformy .NET Core. Można również użyć [programu Visual Studio Code](tutorials/with-visual-studio-code.md), [programu Visual Studio 2017](tutorials/with-visual-studio.md) (tylko Windows), lub [programu Visual Studio dla komputerów Mac](tutorials/using-on-mac-vs.md) (macOS tylko), aby utworzyć aplikację platformy .NET Core.

## <a name="tutorials"></a>Samouczki

Możesz rozpocząć tworzenie aplikacji .NET Core, wykonując te samouczki krok po kroku.

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

* [Utwórz aplikację "Hello World" C# za pomocą programu .NET Core w programie Visual Studio 2017.](./tutorials/with-visual-studio.md)

* [Tworzenie biblioteki klas C#, w języku .NET Core w programie Visual Studio 2017.](./tutorials/library-with-visual-studio.md)

* [Tworzenie aplikacji Visual Basic "Hello World" przy użyciu platformy .NET Core w programie Visual Studio 2017.](./tutorials/vb-with-visual-studio.md)

* [Tworzenie biblioteki klas w języku Visual Basic i .NET Core w programie Visual Studio 2017.](./tutorials/vb-library-with-visual-studio.md)  

* Obejrzyj film wideo na [jak zainstalować i używać programu Visual Studio Code i platformy .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).

* Obejrzyj film wideo na [jak zainstalować i korzystać z programu Visual Studio 2017 i .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).

* [Wprowadzenie do platformy .NET Core przy użyciu wiersza polecenia.](tutorials/using-with-xplat-cli.md)

Zobacz [rozwoju wymagania wstępne dla Windows](windows-prerequisites.md) artykule Aby uzyskać listę obsługiwanych wersji Windows.

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Możesz rozpocząć tworzenie aplikacji .NET Core, wykonując te samouczki krok po kroku.

* [Wprowadzenie do platformy .NET Core przy użyciu wiersza polecenia.](tutorials/using-with-xplat-cli.md)

* Obejrzyj film wideo na [rozpoczęcie korzystania z programu Visual Studio Code przy użyciu języka C# i .NET Core w systemie Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

Zobacz [wymagania wstępne dotyczące programowania systemu Linux](linux-prerequisites.md) artykułu, aby uzyskać listę obsługiwane dystrybucje systemu Linux i wersji.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Możesz rozpocząć tworzenie aplikacji .NET Core, wykonując te samouczki krok po kroku.

* Obejrzyj film wideo na [rozpoczęcie korzystania z programu Visual Studio Code przy użyciu języka C# i .NET Core w systemie macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).

* [Wprowadzenie do platformy .NET Core w systemie macOS przy użyciu programu Visual Studio Code.](tutorials/using-on-macos.md)

* [Wprowadzenie do platformy .NET Core przy użyciu wiersza polecenia.](tutorials/using-with-xplat-cli.md)

* [Wprowadzenie do platformy .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac.](tutorials/using-on-mac-vs.md)

* [Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac.](tutorials/using-on-mac-vs-full-solution.md)

Zobacz [wymagania wstępne dotyczące programowania dla systemu macOS](macos-prerequisites.md) artykułu listę obsługiwanych systemów operacyjnych X / wersji systemu macOS.

---
