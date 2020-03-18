---
title: Wprowadzenie do programu .NET Core
description: Znajdź zasoby, aby dowiedzieć się, jak tworzyć aplikacje .NET Core w systemach Windows, Linux i macOS.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 0968d9db1dbfbdc8c586328ee8e02315f17950b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714393"
---
# <a name="get-started-with-net-core"></a>Wprowadzenie do programu .NET Core

Ten artykuł zawiera informacje dotyczące rozpoczynania pracy z platformą .NET Core. Program .NET Core można zainstalować w systemach Windows, Linux i macOS. Możesz kodować w swoim ulubionym edytorze tekstu i tworzyć biblioteki i aplikacje międzyplatformowe.

Jeśli nie masz pewności, co to jest program .NET Core lub jak odnosi się do innych technologii .NET, rozpocznij od omówienie Co to [jest .NET.](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) Mówiąc prościej, .NET Core jest implementacją platformy .NET typu open source na wielu platformach.

## <a name="create-an-application"></a>Tworzenie aplikacji

Najpierw pobierz i zainstaluj zestaw [SDK .NET Core](https://dotnet.microsoft.com/download) na komputerze.

Następnie otwórz terminal, taki jak **PowerShell,** **Wiersz polecenia**lub **bash**. Wpisz `dotnet` następujące polecenia, aby utworzyć i uruchomić aplikację C#:

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Powinny zostać wyświetlone następujące dane wyjściowe:

```console
Hello World!
```

Gratulacje! Utworzono prostą aplikację .NET Core. Można również użyć [kodu programu Visual Studio](./tutorials/with-visual-studio-code.md), Visual [Studio](./tutorials/with-visual-studio.md) (tylko windows) lub Visual Studio dla [komputerów Mac](./tutorials/using-on-mac-vs.md) (tylko macOS), aby utworzyć aplikację .NET Core.

## <a name="tutorials"></a>Samouczki

Wprowadzenie do tworzenia aplikacji .NET Core, wykonując następujące samouczki krok po kroku:

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

- [Tworzenie pierwszej aplikacji konsoli .NET Core w programie Visual Studio 2019](./tutorials/with-visual-studio.md)
- [Tworzenie biblioteki klas za pomocą programu .NET Standard w programie Visual Studio](./tutorials/library-with-visual-studio.md)
- [Wprowadzenie do programu .NET Core przy użyciu procesora CLI .NET Core](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![ikona kamery filmowych dla wideo](./media/video-icon.png "Obejrzyj film") | Zobacz, [jak zainstalować i używać programu Visual Studio Code i wideo .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) w kanale 9. |
| ![ikona kamery filmowych dla wideo](./media/video-icon.png "Obejrzyj film") | Obejrzyj filmy [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) w YouTube. |

Zobacz [.NET Core zależności i wymagania](install/dependencies.md?pivots=os-windows) artykułu dla listy obsługiwanych wersji systemu Windows.

# <a name="linux"></a>[Linux](#tab/linux)

Wprowadzenie do tworzenia aplikacji .NET Core, wykonując następujące samouczki krok po kroku:

- [Wprowadzenie do programu .NET Core przy użyciu wiersza polecenia](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![ikona kamery filmowych dla wideo](./media/video-icon.png "Obejrzyj film") | Obejrzyj klip wideo przedstawiający [wprowadzenie do programu Visual Studio Code przy użyciu wersji C# i .NET Core w programie Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu). |

Zobacz [.NET Core zależności i wymagania](install/dependencies.md?pivots=os-linux) artykułu dla listy obsługiwanych dystrybucji systemu Linux i wersji.

# <a name="macos"></a>[Macos](#tab/macos)

Wprowadzenie do tworzenia aplikacji .NET Core, wykonując następujące samouczki krok po kroku:

- [Rozpoczynanie pracy z platformą .NET Core w systemie macOS przy użyciu programu Visual Studio Code](./tutorials/using-on-macos.md)
- [Wprowadzenie do programu .NET Core przy użyciu wiersza polecenia](./tutorials/cli-create-console-app.md)
- [Rozpoczynanie pracy z platformą .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac](./tutorials/using-on-mac-vs.md)
- [Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| ![ikona kamery filmowych dla wideo](media/video-icon.png "Obejrzyj film") | Obejrzyj klip wideo przedstawiający [wprowadzenie do programu Visual Studio Code przy użyciu języka C# i programu .NET Core w systemie macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac). |

Zobacz [.NET Core zależności i wymagania](install/dependencies.md?pivots=os-macos) artykułu dla listy obsługiwanych wersji systemu OS X / macOS.

---
