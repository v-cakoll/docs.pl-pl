---
title: Wprowadzenie do platformy .NET Core
description: Znajdź zasoby, aby dowiedzieć się, jak tworzyć aplikacje .NET Core w systemach Windows, Linux i macOS.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 0968d9db1dbfbdc8c586328ee8e02315f17950b9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714393"
---
# <a name="get-started-with-net-core"></a>Wprowadzenie do platformy .NET Core

Ten artykuł zawiera informacje na temat rozpoczynania pracy z platformą .NET Core. Program .NET Core można zainstalować w systemach Windows, Linux i macOS. Możesz zakodować w ulubionym edytorze tekstów i tworzyć Międzyplatformowe biblioteki i aplikacje.

Jeśli nie masz pewności, co to jest platforma .NET Core, lub jak odnosi się do innych technologii .NET, Zacznij od omówienia [programu .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) . Po prostu, .NET Core to wieloplatformowa implementacja platformy .NET.

## <a name="create-an-application"></a>Tworzenie aplikacji

Najpierw pobierz i zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download) na komputerze.

Następnie otwórz Terminal, taki jak **PowerShell**, **wiersza polecenia**lub **bash**. Wpisz następujące polecenia `dotnet`, aby utworzyć i uruchomić C# aplikację:

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Powinny zostać wyświetlone następujące dane wyjściowe:

```console
Hello World!
```

Gratulacje! Utworzono prostą aplikację platformy .NET Core. Można również użyć [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (tylko Windows) lub [Visual Studio dla komputerów Mac](./tutorials/using-on-mac-vs.md) (tylko macOS), aby utworzyć aplikację platformy .NET Core.

## <a name="tutorials"></a>Samouczki

Zacznij opracowywać aplikacje platformy .NET Core, wykonując następujące Samouczki krok po kroku:

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

- [Tworzenie pierwszej aplikacji konsolowej .NET Core w programie Visual Studio 2019](./tutorials/with-visual-studio.md)
- [Kompilowanie biblioteki klas przy użyciu .NET Standard w programie Visual Studio](./tutorials/library-with-visual-studio.md)
- [Rozpoczynanie pracy z platformą .NET Core przy użyciu interfejs wiersza polecenia platformy .NET Core](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![ikona aparatu filmu wideo](./media/video-icon.png "Obejrzyj film") | Obejrzyj, [jak zainstalować i używać Visual Studio Code i środowiska .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) wideo w witrynie Channel 9. |
| ![ikona aparatu filmu wideo](./media/video-icon.png "Obejrzyj film") | Obejrzyj wideo z programem [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) w serwisie YouTube. |

Listę obsługiwanych wersji systemu Windows zawiera artykuł [zależności i wymagania dotyczące platformy .NET Core](install/dependencies.md?pivots=os-windows) .

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Zacznij opracowywać aplikacje platformy .NET Core, wykonując następujące Samouczki krok po kroku:

- [Rozpoczynanie pracy z platformą .NET Core przy użyciu wiersza polecenia](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![ikona aparatu filmu wideo](./media/video-icon.png "Obejrzyj film") | Obejrzyj film wideo [z wprowadzeniem do Visual Studio Code przy C# użyciu oprogramowania i platformy .NET Core w systemie Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu). |

Listę obsługiwanych dystrybucje i wersji systemu Linux znajduje się w artykule [zależności i wymagania dotyczące platformy .NET Core](install/dependencies.md?pivots=os-linux) .

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Zacznij opracowywać aplikacje platformy .NET Core, wykonując następujące Samouczki krok po kroku:

- [Rozpocznij pracę z platformą .NET Core w systemie macOS przy użyciu Visual Studio Code](./tutorials/using-on-macos.md)
- [Rozpoczynanie pracy z platformą .NET Core przy użyciu wiersza polecenia](./tutorials/cli-create-console-app.md)
- [Rozpoczynanie pracy z platformą .NET Core w systemie macOS przy użyciu programu Visual Studio dla komputerów Mac](./tutorials/using-on-mac-vs.md)
- [Tworzenie kompletnego rozwiązania .NET Core w systemie macOS przy użyciu Visual Studio dla komputerów Mac](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| ![ikona aparatu filmu wideo](media/video-icon.png "Obejrzyj film") | Obejrzyj film wideo [z wprowadzeniem do Visual Studio Code przy C# użyciu oprogramowania i platformy .NET Core w systemie macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac). |

Listę obsługiwanych wersji systemu OS X/macOS można znaleźć w artykule [zależności i wymagania dotyczące platformy .NET Core](install/dependencies.md?pivots=os-macos) .

---
