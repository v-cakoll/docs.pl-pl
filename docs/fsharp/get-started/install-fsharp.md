---
title: Instalowanie języka F#
description: Dowiedz się, F# jak zainstalować program w oparciu o środowisko.
ms.date: 09/05/2019
ms.openlocfilehash: 18b660ff640904119d63f57405752a14f7673e0c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400720"
---
# <a name="install-f"></a><span data-ttu-id="42223-103">Zainstaluj program F\#</span><span class="sxs-lookup"><span data-stu-id="42223-103">Install F\#</span></span>

<span data-ttu-id="42223-104">Program można zainstalować F# na wiele sposobów, w zależności od środowiska.</span><span class="sxs-lookup"><span data-stu-id="42223-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="42223-105">Instalowanie F# za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="42223-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="42223-106">Jeśli pobierasz [program Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) po raz pierwszy, najpierw zainstaluje się Instalator programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="42223-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="42223-107">Zainstaluj odpowiednią jednostkę SKU programu Visual Studio z Instalatora.</span><span class="sxs-lookup"><span data-stu-id="42223-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="42223-108">Jeśli jest już zainstalowany, kliknij przycisk **Modyfikuj**.</span><span class="sxs-lookup"><span data-stu-id="42223-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="42223-109">Zobaczysz listę obciążeń.</span><span class="sxs-lookup"><span data-stu-id="42223-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="42223-110">Wybierz pozycję **ASP.NET i programowanie dla sieci Web** , co spowoduje zainstalowanie F# obsługi i platformy .NET Core na potrzeby projektów ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="42223-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span></span>

<span data-ttu-id="42223-111">Następnie kliknij przycisk **Modyfikuj** w prawym dolnym rogu.</span><span class="sxs-lookup"><span data-stu-id="42223-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="42223-112">Spowoduje to zainstalowanie wszystkich wybranych elementów.</span><span class="sxs-lookup"><span data-stu-id="42223-112">This will install everything you have selected.</span></span> <span data-ttu-id="42223-113">Następnie możesz otworzyć program Visual Studio 2017 z F# obsługą języka, klikając przycisk **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="42223-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="42223-114">Zainstaluj F# przy użyciu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="42223-114">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="42223-115">F#Program jest instalowany domyślnie w [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)niezależnie od tego, która konfiguracja została wybrana.</span><span class="sxs-lookup"><span data-stu-id="42223-115">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="42223-116">Po zakończeniu instalacji wybierz pozycję "Uruchom program Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="42223-116">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="42223-117">Możesz również uruchomić ją za poorednictwem wyszukiwania w witrynie macOS.</span><span class="sxs-lookup"><span data-stu-id="42223-117">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="42223-118">Zainstaluj F# przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="42223-118">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="42223-119">Aby można było korzystać z szablonów projektów, na ścieżce musi być zainstalowana i dostępna funkcja [git](https://git-scm.com/download) .</span><span class="sxs-lookup"><span data-stu-id="42223-119">You must have [git installed](https://git-scm.com/download) and available on your PATH to make use of project templates.</span></span> <span data-ttu-id="42223-120">Można sprawdzić, czy jest poprawnie zainstalowana, wpisując `git --version` w wierszu polecenia i naciskając klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="42223-120">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

### <a name="macostabmacos"></a>[<span data-ttu-id="42223-121">macOS</span><span class="sxs-lookup"><span data-stu-id="42223-121">macOS</span></span>](#tab/macos)

<span data-ttu-id="42223-122">Narzędzie [mono](https://www.mono-project.com) jest używane na potrzeby [ F# interaktywnej](../tutorials/fsharp-interactive/index.md) obsługi.</span><span class="sxs-lookup"><span data-stu-id="42223-122">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="42223-123">Najprostszym sposobem instalacji narzędzia mono w systemie macOS jest za pośrednictwem oprogramowania homebrew.</span><span class="sxs-lookup"><span data-stu-id="42223-123">The easiest way to install Mono on macOS is via Homebrew.</span></span> <span data-ttu-id="42223-124">Po prostu wpisz następujące elementy w terminalu:</span><span class="sxs-lookup"><span data-stu-id="42223-124">Simply type the following into your terminal:</span></span>

```console
brew install mono
```

<span data-ttu-id="42223-125">Zainstaluj również [zestaw .NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="42223-125">Also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="linuxtablinux"></a>[<span data-ttu-id="42223-126">Linux</span><span class="sxs-lookup"><span data-stu-id="42223-126">Linux</span></span>](#tab/linux)

<span data-ttu-id="42223-127">Narzędzie [mono](https://www.mono-project.com) jest używane na potrzeby [ F# interaktywnej](../tutorials/fsharp-interactive/index.md) obsługi.</span><span class="sxs-lookup"><span data-stu-id="42223-127">[Mono](https://www.mono-project.com) is used for [F# Interactive](../tutorials/fsharp-interactive/index.md) support.</span></span> <span data-ttu-id="42223-128">Jeśli korzystasz z programu debian lub Ubuntu, możesz skorzystać z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="42223-128">If you're on Debian or Ubuntu, you can use the following:</span></span>

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

<span data-ttu-id="42223-129">Zainstaluj również [zestaw .NET Core SDK](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="42223-129">Also install the [.NET Core SDK](https://www.microsoft.com/net/download).</span></span>

### <a name="windowstabwindows"></a>[<span data-ttu-id="42223-130">Windows</span><span class="sxs-lookup"><span data-stu-id="42223-130">Windows</span></span>](#tab/windows)

<span data-ttu-id="42223-131">Zainstaluj [program Visual Studio F# z obsługą techniczną](#install-f-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="42223-131">Install [Visual Studio with F# support](#install-f-with-visual-studio).</span></span> <span data-ttu-id="42223-132">Spowoduje to zainstalowanie wszystkich składników niezbędnych do pisania, kompilowania i wykonywania F# kodu.</span><span class="sxs-lookup"><span data-stu-id="42223-132">This installs all the necessary components to write, compile, and execute F# code.</span></span>

<span data-ttu-id="42223-133">Zainstaluj również [zestaw .NET Core SDK](https://www.microsoft.com/net/download/).</span><span class="sxs-lookup"><span data-stu-id="42223-133">Also install the [.NET Core SDK](https://www.microsoft.com/net/download/).</span></span>

---

<span data-ttu-id="42223-134">Następnie konieczne będzie zainstalowanie [Visual Studio Code](https://code.visualstudio.com) .</span><span class="sxs-lookup"><span data-stu-id="42223-134">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="42223-135">Następnie kliknij ikonę rozszerzenia i wyszukaj ciąg "Ionide":</span><span class="sxs-lookup"><span data-stu-id="42223-135">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="42223-136">Jedyną wtyczką wymaganą F# do obsługi w Visual Studio Code jest [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="42223-136">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="42223-137">Można jednak zainstalować [Ionide-fałszywych](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) , aby uzyskać [fałszywe](https://fsharp.github.io/FAKE/) wsparcie i [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) , aby uzyskać pomoc techniczną [Paket](https://fsprojects.github.io/Paket/) .</span><span class="sxs-lookup"><span data-stu-id="42223-137">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fsharp.github.io/FAKE/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="42223-138">FAŁSZYWE i Paket są dodatkowymi F# narzędziami społecznościowymi do kompilowania projektów i zarządzania zależnościami.</span><span class="sxs-lookup"><span data-stu-id="42223-138">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="42223-139">Zainstaluj F# na serwerze kompilacji</span><span class="sxs-lookup"><span data-stu-id="42223-139">Install F# on a Build Server</span></span>

<span data-ttu-id="42223-140">Jeśli używasz platformy .NET Core lub .NET Framework za pomocą zestawu .NET SDK, wystarczy zainstalować zestaw .NET SDK na serwerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="42223-140">If you are using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="42223-141">Ma wszystko, czego potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="42223-141">It has everything you need.</span></span>

<span data-ttu-id="42223-142">Jeśli używasz .NET Framework i **nie** używasz zestawu .NET SDK, musisz zainstalować [Visual Studio Build Tools jednostkę SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) na serwerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="42223-142">If you are using .NET Framework and you are **not** using the .NET SDK, then you will need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="42223-143">W instalatorze wybierz pozycję **narzędzia kompilacji klasycznej platformy .NET** , a następnie wybierz składnik  **F# kompilatora** po prawej stronie menu Instalatora.</span><span class="sxs-lookup"><span data-stu-id="42223-143">In the installer, select **.NET desktop build tools** and then select the **F# compiler** component on the right side of the installer menu.</span></span>
