---
title: Instalowanie języka F#
description: Dowiedz się, F# jak zainstalować program na różne sposoby.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346565"
---
# <a name="install-f"></a><span data-ttu-id="edee2-103">Zainstaluj program F\#</span><span class="sxs-lookup"><span data-stu-id="edee2-103">Install F\#</span></span>

<span data-ttu-id="edee2-104">Program można zainstalować F# na wiele sposobów, w zależności od środowiska.</span><span class="sxs-lookup"><span data-stu-id="edee2-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="edee2-105">Instalowanie F# za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="edee2-105">Install F# with Visual Studio</span></span>

1. <span data-ttu-id="edee2-106">Jeśli pobierasz [program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) po raz pierwszy, najpierw zainstaluje Instalator programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="edee2-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for the first time, it will first install Visual Studio Installer.</span></span> <span data-ttu-id="edee2-107">Zainstaluj odpowiednią wersję programu Visual Studio z Instalatora.</span><span class="sxs-lookup"><span data-stu-id="edee2-107">Install the appropriate edition of Visual Studio from the installer.</span></span>

   <span data-ttu-id="edee2-108">Jeśli masz już zainstalowany program Visual Studio, wybierz pozycję **Modyfikuj** obok wersji, która ma zostać dodana F# .</span><span class="sxs-lookup"><span data-stu-id="edee2-108">If you already have Visual Studio installed, choose **Modify** next to the edition you want to add F# to.</span></span>

2. <span data-ttu-id="edee2-109">Na stronie obciążenia wybierz obciążenie **ASP.NET i sieci Web** , F# w tym obsługę platformy .net core dla projektów ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="edee2-109">On the Workloads page, select the **ASP.NET and web development** workload, which includes F# and .NET Core support for ASP.NET Core projects.</span></span>

3. <span data-ttu-id="edee2-110">Wybierz pozycję **Modyfikuj** w prawym dolnym rogu, aby zainstalować wszystkie wybrane elementy.</span><span class="sxs-lookup"><span data-stu-id="edee2-110">Choose **Modify** in the lower right-hand corner to install everything you've selected.</span></span>

   <span data-ttu-id="edee2-111">Następnie możesz otworzyć program Visual Studio F# , wybierając pozycję **Uruchom** w Instalator programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="edee2-111">You can then open Visual Studio with F# by choosing **Launch** in Visual Studio Installer.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="edee2-112">Zainstaluj F# przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="edee2-112">Install F# with Visual Studio Code</span></span>

1. <span data-ttu-id="edee2-113">Upewnij się, że masz zainstalowaną i dostępną usługę [git](https://git-scm.com/download) do swojej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="edee2-113">Ensure you have [git](https://git-scm.com/download) installed and available on your PATH.</span></span> <span data-ttu-id="edee2-114">Można sprawdzić, czy jest poprawnie zainstalowana, wprowadzając `git --version` w wierszu polecenia i naciskając klawisz **Enter**.</span><span class="sxs-lookup"><span data-stu-id="edee2-114">You can verify that it's installed correctly by entering `git --version` at a command prompt and pressing **Enter**.</span></span>

2. <span data-ttu-id="edee2-115">Zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download) i [Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="edee2-115">Install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com).</span></span>

3. <span data-ttu-id="edee2-116">Wybierz ikonę rozszerzenia i wyszukaj ciąg "Ionide":</span><span class="sxs-lookup"><span data-stu-id="edee2-116">Select the Extensions icon and search for "Ionide":</span></span>

   <span data-ttu-id="edee2-117">Jedyną wtyczką wymaganą F# do obsługi w Visual Studio Code jest [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="edee2-117">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="edee2-118">Można jednak zainstalować [Ionide-fałszywych](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) , aby uzyskać [fałszywe](https://fake.build/) wsparcie i [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) , aby uzyskać pomoc techniczną [Paket](https://fsprojects.github.io/Paket/) .</span><span class="sxs-lookup"><span data-stu-id="edee2-118">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="edee2-119">FAŁSZYWE i Paket są dodatkowymi F# narzędziami społecznościowymi do kompilowania projektów i zarządzania zależnościami.</span><span class="sxs-lookup"><span data-stu-id="edee2-119">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="edee2-120">Zainstaluj F# przy użyciu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="edee2-120">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="edee2-121">F#Program jest instalowany domyślnie w [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)niezależnie od tego, która konfiguracja została wybrana.</span><span class="sxs-lookup"><span data-stu-id="edee2-121">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="edee2-122">Po zakończeniu instalacji wybierz pozycję **Uruchom program Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="edee2-122">After the install completes, choose **Start Visual Studio**.</span></span> <span data-ttu-id="edee2-123">Program Visual Studio można także otworzyć w programie macOS.</span><span class="sxs-lookup"><span data-stu-id="edee2-123">You can also open Visual Studio through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="edee2-124">Zainstaluj F# na serwerze kompilacji</span><span class="sxs-lookup"><span data-stu-id="edee2-124">Install F# on a build server</span></span>

<span data-ttu-id="edee2-125">Jeśli używasz platformy .NET Core lub .NET Framework za pomocą zestawu .NET SDK, wystarczy zainstalować zestaw .NET SDK na serwerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="edee2-125">If you're using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="edee2-126">Ma wszystko, czego potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="edee2-126">It has everything you need.</span></span>

<span data-ttu-id="edee2-127">Jeśli używasz .NET Framework i **nie** używasz zestawu .NET SDK, musisz zainstalować [Visual Studio Build Tools jednostkę SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) na serwerze z systemem Windows.</span><span class="sxs-lookup"><span data-stu-id="edee2-127">If you're using .NET Framework and you are **not** using the .NET SDK, then you'll need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="edee2-128">W instalatorze wybierz pozycję **narzędzia kompilacji klasycznej platformy .NET**, a następnie wybierz składnik  **F# kompilatora** po prawej stronie menu Instalatora.</span><span class="sxs-lookup"><span data-stu-id="edee2-128">In the installer, select **.NET desktop build tools**, and then select the **F# compiler** component on the right-hand side of the installer menu.</span></span>
