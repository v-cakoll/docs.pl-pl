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
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="55f01-103">Wymagania wstępne dotyczące platformy .NET Core w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="55f01-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="55f01-104">W tym artykule przedstawiono obsługiwane wersje programu macOS i zależności programu .NET Core, które są potrzebne do tworzenia, wdrażania i uruchamiania aplikacji platformy .NET Core na maszynach macOS.</span><span class="sxs-lookup"><span data-stu-id="55f01-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="55f01-105">Obsługiwane wersje systemu operacyjnego i zależności stosują się do trzech sposobów tworzenia aplikacji platformy .NET Core na komputerze Mac: za pośrednictwem [wiersza polecenia z ulubionym edytorem](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)i [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="55f01-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

## <a name="downloads-and-dependencies"></a><span data-ttu-id="55f01-106">Pliki do pobrania i zależności</span><span class="sxs-lookup"><span data-stu-id="55f01-106">Downloads and dependencies</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="55f01-107">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="55f01-107">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="55f01-108">Platforma .NET Core 3,0 jest obsługiwana w systemie **MacOS High Sierra (wersja 10,13)** i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="55f01-108">.NET Core 3.0 is supported on **macOS High Sierra (version 10.13)** and later versions.</span></span> <span data-ttu-id="55f01-109">Wymagana jest architektura procesora **x64** .</span><span class="sxs-lookup"><span data-stu-id="55f01-109">A **x64** CPU architecture is required.</span></span>

<span data-ttu-id="55f01-110">Pobierz i Zainstaluj zestaw .NET Core SDK ze strony [plików do pobrania w programie .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0) .</span><span class="sxs-lookup"><span data-stu-id="55f01-110">Download and install the .NET Core SDK from the [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0) page.</span></span> <span data-ttu-id="55f01-111">[Obsługiwane wersje systemu operacyjnego .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych, dystrybucji i wersji systemu operacyjnego .NET 3,0 Core</span><span class="sxs-lookup"><span data-stu-id="55f01-111">[.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="55f01-112">Listę znanych problemów można znaleźć w artykule [znane problemy dotyczące programu .NET Core](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="55f01-112">For a list of known issues, see [.NET Core known issues](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-known-issues.md).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="55f01-113">.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="55f01-113">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="55f01-114">Platforma .NET Core 2,2 jest obsługiwana w **macOS Sierra (wersja 10,12)** i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="55f01-114">.NET Core 2.2 is supported on **macOS Sierra (version 10.12)** and later versions.</span></span> <span data-ttu-id="55f01-115">Wymagana jest architektura procesora **x64** .</span><span class="sxs-lookup"><span data-stu-id="55f01-115">A **x64** CPU architecture is required.</span></span>

<span data-ttu-id="55f01-116">Pobierz i Zainstaluj zestaw .NET Core SDK ze strony [plików do pobrania w programie .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) .</span><span class="sxs-lookup"><span data-stu-id="55f01-116">Download and install the .NET Core SDK from the [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) page.</span></span> <span data-ttu-id="55f01-117">[Obsługiwane wersje systemu operacyjnego .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych, dystrybucji i wersji systemu operacyjnego .NET 2,2 Core</span><span class="sxs-lookup"><span data-stu-id="55f01-117">[.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="55f01-118">Listę znanych problemów można znaleźć w artykule [znane problemy dotyczące programu .NET Core](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="55f01-118">For a list of known issues, see [.NET Core known issues](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-known-issues.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="55f01-119">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="55f01-119">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="55f01-120">Platforma .NET Core 2,1 jest obsługiwana w **macOS Sierra (wersja 10,12)** i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="55f01-120">.NET Core 2.1 is supported on **macOS Sierra (version 10.12)** and later versions.</span></span> <span data-ttu-id="55f01-121">Wymagana jest architektura procesora **x64** .</span><span class="sxs-lookup"><span data-stu-id="55f01-121">A **x64** CPU architecture is required.</span></span>

<span data-ttu-id="55f01-122">Pobierz i Zainstaluj zestaw .NET Core SDK ze strony [plików do pobrania w programie .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1) .</span><span class="sxs-lookup"><span data-stu-id="55f01-122">Download and install the .NET Core SDK from the [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1) page.</span></span> <span data-ttu-id="55f01-123">[Obsługiwane wersje systemu operacyjnego .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych, dystrybucji i wersji systemu operacyjnego .NET 2,1 Core</span><span class="sxs-lookup"><span data-stu-id="55f01-123">[.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="55f01-124">Listę znanych problemów można znaleźć w artykule [znane problemy dotyczące programu .NET Core](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="55f01-124">For a list of known issues, see [.NET Core known issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-known-issues.md).</span></span>

---

## <a name="libgdiplus"></a><span data-ttu-id="55f01-125">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="55f01-125">libgdiplus</span></span>

<span data-ttu-id="55f01-126">Aplikacje .NET Core używające zestawu *System. Drawing. Common* wymagają zainstalowania libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="55f01-126">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="55f01-127">Łatwym sposobem uzyskania libgdiplus jest użycie Menedżera pakietów [oprogramowania homebrew ("rozwiązania brew")](https://brew.sh/) dla macOS.</span><span class="sxs-lookup"><span data-stu-id="55f01-127">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="55f01-128">Po zainstalowaniu *rozwiązania brew*Zainstaluj libgdiplus, wykonując następujące polecenia w wierszu terminalu (polecenie):</span><span class="sxs-lookup"><span data-stu-id="55f01-128">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install libgdiplus
```

## <a name="visual-studio-for-mac"></a><span data-ttu-id="55f01-129">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="55f01-129">Visual Studio for Mac</span></span>

<span data-ttu-id="55f01-130">Za pomocą dowolnego edytora można opracowywać aplikacje platformy .NET Core przy użyciu zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="55f01-130">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="55f01-131">Jeśli jednak chcesz opracowywać aplikacje .NET Core na komputerze Mac w zintegrowanym środowisku programistycznym, możesz użyć [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="55f01-131">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>
