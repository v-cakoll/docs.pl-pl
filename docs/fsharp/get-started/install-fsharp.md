---
title: ZainstalujF#
description: Dowiedz się, jak zainstalować F# zależności od używanego środowiska.
ms.date: 08/28/2018
ms.openlocfilehash: 873d3021ba884ec81992469e5d0f3b7c18b1e0f4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975254"
---
# <a name="install-f"></a><span data-ttu-id="15e82-103">Zainstaluj F\#</span><span class="sxs-lookup"><span data-stu-id="15e82-103">Install F\#</span></span>

<span data-ttu-id="15e82-104">Możesz zainstalować F# na wiele sposobów, w zależności od środowiska.</span><span class="sxs-lookup"><span data-stu-id="15e82-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="15e82-105">Zainstaluj F# za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="15e82-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="15e82-106">Jeśli masz pobieranie [programu Visual Studio](https://visualstudio.microsoft.com/) po raz pierwszy zostanie najpierw zainstalować Instalatora programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="15e82-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="15e82-107">Zainstaluj odpowiednie jednostki SKU programu Visual Studio z poziomu Instalatora.</span><span class="sxs-lookup"><span data-stu-id="15e82-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="15e82-108">Jeśli masz już zainstalowany, kliknij przycisk **Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="15e82-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="15e82-109">Następnie zobaczysz listę obciążeń.</span><span class="sxs-lookup"><span data-stu-id="15e82-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="15e82-110">Wybierz **ASP.NET i tworzenie aplikacji internetowych** które zainstaluje F# pomocy technicznej i .NET Core obsługuje dla projektów ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="15e82-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span></span>

<span data-ttu-id="15e82-111">Następnie kliknij przycisk **Modyfikuj** w dolnym po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="15e82-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="15e82-112">Spowoduje to zainstalowanie wszystko, co jest wybrane.</span><span class="sxs-lookup"><span data-stu-id="15e82-112">This will install everything you have selected.</span></span> <span data-ttu-id="15e82-113">Następnie możesz otworzyć Visual Studio 2017 z F# języki, klikając **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="15e82-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="15e82-114">Zainstaluj F# z programem Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="15e82-114">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="15e82-115">F#jest instalowany domyślnie w [programu Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/), niezależnie od tego, która Konfiguracja wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="15e82-115">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/), no matter which configuration you choose.</span></span>

<span data-ttu-id="15e82-116">Po zakończeniu instalacji wybierz pozycję "Uruchom Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="15e82-116">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="15e82-117">Można również uruchomić go za pomocą wyszukiwania w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="15e82-117">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="15e82-118">Zainstaluj F# za pomocą programu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="15e82-118">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="15e82-119">Konieczne jest posiadanie [zainstalowane narzędzie git](https://git-scm.com/download) i dostępne w zmiennej PATH, aby użyć szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="15e82-119">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates.</span></span> <span data-ttu-id="15e82-120">Możesz sprawdzić, czy jest poprawnie zainstalowany, wpisując `git --version` w wierszu polecenia i naciskając klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="15e82-120">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="15e82-121">macOS</span><span class="sxs-lookup"><span data-stu-id="15e82-121">macOS</span></span>](#tab/macos)

<span data-ttu-id="15e82-122">[Narzędzie mono](https://www.mono-project.com) służy do [ F# Interactive](../tutorials/fsharp-interactive/index.md) pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="15e82-122">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="15e82-123">Najprostszym sposobem zainstalowania platformy Mono w systemie macOS jest za pośrednictwem Homebrew.</span><span class="sxs-lookup"><span data-stu-id="15e82-123">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="15e82-124">Po prostu wpisz następujące polecenie w terminalu:</span><span class="sxs-lookup"><span data-stu-id="15e82-124">Simply type the following into your terminal:</span></span>

```console
brew install mono
```

<span data-ttu-id="15e82-125">Zainstaluj również [zestawu .NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="15e82-125">Also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="15e82-126">Linux</span><span class="sxs-lookup"><span data-stu-id="15e82-126">Linux</span></span>](#tab/linux)

<span data-ttu-id="15e82-127">[Narzędzie mono](https://www.mono-project.com) służy do [ F# Interactive](../tutorials/fsharp-interactive/index.md) pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="15e82-127">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="15e82-128">W przypadku systemie Debian lub Ubuntu, można użyć następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="15e82-128">If you're on Debian or Ubuntu, you can use the following:</span></span>

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="15e82-129">Zainstaluj również [zestawu .NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="15e82-129">Also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="15e82-130">Windows</span><span class="sxs-lookup"><span data-stu-id="15e82-130">Windows</span></span>](#tab/windows)

<span data-ttu-id="15e82-131">Zainstaluj [programu Visual Studio z F# obsługuje](#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="15e82-131">Install [Visual Studio with F# support](#install-f-with-visual-studio).</span></span> <span data-ttu-id="15e82-132">Spowoduje to zainstalowanie wszystkich składników niezbędnych do zapisu, skompilowania i wykonania F# kodu.</span><span class="sxs-lookup"><span data-stu-id="15e82-132">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="15e82-133">Zainstaluj również [zestawu .NET Core SDK](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="15e82-133">Also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

<span data-ttu-id="15e82-134">Następnie należy [programu Visual Studio Code](https://code.visualstudio.com) zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="15e82-134">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="15e82-135">Następnie kliknij ikonę rozszerzenia i poszukaj pozycji "Ionide":</span><span class="sxs-lookup"><span data-stu-id="15e82-135">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="15e82-136">Wtyczka tylko wymagane dla F# pomoc techniczna w Visual Studio Code jest [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="15e82-136">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="15e82-137">Jednakże można także zainstalować [SFAŁSZOWANA Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) można pobrać [FAŁSZYWE](https://fsharp.github.io/FAKE/) pomocy technicznej i [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) można pobrać [Paket](https://fsprojects.github.io/Paket/) pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="15e82-137">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="15e82-138">FAŁSZYWE i Paket są naliczane dodatkowo F# narzędzia społeczności do kompilowania projektów i zarządzanie zależnościami, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="15e82-138">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>
