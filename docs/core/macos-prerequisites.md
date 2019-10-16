---
title: Wymagania wstępne dotyczące platformy .NET Core na komputerach Mac
description: Obsługiwane wersje macOS i zależności programu .NET Core umożliwiają tworzenie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach macOS.
author: thraka
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 10/11/2019
ms.openlocfilehash: 2d4fc0b37be08988440325db8b507124c36bf053
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318319"
---
# <a name="prerequisites-for-net-core-on-macos"></a>Wymagania wstępne dotyczące platformy .NET Core w systemie macOS

W tym artykule przedstawiono obsługiwane wersje programu macOS i zależności programu .NET Core, które są potrzebne do tworzenia, wdrażania i uruchamiania aplikacji platformy .NET Core na maszynach macOS. Obsługiwane wersje systemu operacyjnego i zależności stosują się do trzech sposobów tworzenia aplikacji platformy .NET Core na komputerze Mac: za pośrednictwem [wiersza polecenia z ulubionym edytorem](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)i [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

## <a name="downloads-and-dependencies"></a>Pliki do pobrania i zależności

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

Platforma .NET Core 3,0 jest obsługiwana w systemie **MacOS High Sierra (wersja 10,13)** i nowszych wersjach. Wymagana jest architektura procesora **x64** .

Pobierz i Zainstaluj zestaw .NET Core SDK ze strony [plików do pobrania w programie .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0) . [Obsługiwane wersje systemu operacyjnego .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych, dystrybucji i wersji systemu operacyjnego .NET 3,0 Core

Listę znanych problemów można znaleźć w artykule [znane problemy dotyczące programu .NET Core](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-known-issues.md).

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

Platforma .NET Core 2,2 jest obsługiwana w **macOS Sierra (wersja 10,12)** i nowszych wersjach. Wymagana jest architektura procesora **x64** .

Pobierz i Zainstaluj zestaw .NET Core SDK ze strony [plików do pobrania w programie .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) . [Obsługiwane wersje systemu operacyjnego .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych, dystrybucji i wersji systemu operacyjnego .NET 2,2 Core

Listę znanych problemów można znaleźć w artykule [znane problemy dotyczące programu .NET Core](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-known-issues.md).

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

Platforma .NET Core 2,1 jest obsługiwana w **macOS Sierra (wersja 10,12)** i nowszych wersjach. Wymagana jest architektura procesora **x64** .

Pobierz i Zainstaluj zestaw .NET Core SDK ze strony [plików do pobrania w programie .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1) . [Obsługiwane wersje systemu operacyjnego .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych, dystrybucji i wersji systemu operacyjnego .NET 2,1 Core

Listę znanych problemów można znaleźć w artykule [znane problemy dotyczące programu .NET Core](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-known-issues.md).

---

## <a name="libgdiplus"></a>libgdiplus

Aplikacje .NET Core używające zestawu *System. Drawing. Common* wymagają zainstalowania libgdiplus.

Łatwym sposobem uzyskania libgdiplus jest użycie Menedżera pakietów [oprogramowania homebrew ("rozwiązania brew")](https://brew.sh/) dla macOS. Po zainstalowaniu *rozwiązania brew*Zainstaluj libgdiplus, wykonując następujące polecenia w wierszu terminalu (polecenie):

```console
brew update
brew install libgdiplus
```

## <a name="visual-studio-for-mac"></a>Visual Studio for Mac

Za pomocą dowolnego edytora można opracowywać aplikacje platformy .NET Core przy użyciu zestaw .NET Core SDK. Jeśli jednak chcesz opracowywać aplikacje .NET Core na komputerze Mac w zintegrowanym środowisku programistycznym, możesz użyć [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).
