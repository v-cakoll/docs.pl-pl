---
title: Instalowanie języka F#
description: Dowiedz się, jak zainstalować F# na różne sposoby.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400247"
---
# <a name="install-f"></a><span data-ttu-id="c32e7-103">Instalacja F\#</span><span class="sxs-lookup"><span data-stu-id="c32e7-103">Install F\#</span></span>

<span data-ttu-id="c32e7-104">F# można zainstalować na wiele sposobów, w zależności od środowiska.</span><span class="sxs-lookup"><span data-stu-id="c32e7-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="c32e7-105">Instalowanie języka F# za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c32e7-105">Install F# with Visual Studio</span></span>

1. <span data-ttu-id="c32e7-106">Jeśli pobierasz [program Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) po raz pierwszy, najpierw zainstaluje Instalator programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c32e7-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for the first time, it will first install Visual Studio Installer.</span></span> <span data-ttu-id="c32e7-107">Zainstaluj odpowiednią wersję programu Visual Studio z instalatora.</span><span class="sxs-lookup"><span data-stu-id="c32e7-107">Install the appropriate edition of Visual Studio from the installer.</span></span>

   <span data-ttu-id="c32e7-108">Jeśli masz już zainstalowany program Visual Studio, wybierz **pozycję Modyfikuj** obok wersji, do której chcesz dodać F#.</span><span class="sxs-lookup"><span data-stu-id="c32e7-108">If you already have Visual Studio installed, choose **Modify** next to the edition you want to add F# to.</span></span>

2. <span data-ttu-id="c32e7-109">Na stronie Obciążenia wybierz ASP.NET i obciążenie **programistyczne sieci Web,** które obejmuje obsługę f# i .NET Core dla ASP.NET projektów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="c32e7-109">On the Workloads page, select the **ASP.NET and web development** workload, which includes F# and .NET Core support for ASP.NET Core projects.</span></span>

3. <span data-ttu-id="c32e7-110">Wybierz **pozycję Modyfikuj** w prawym dolnym rogu, aby zainstalować wszystko, co wybrano.</span><span class="sxs-lookup"><span data-stu-id="c32e7-110">Choose **Modify** in the lower right-hand corner to install everything you've selected.</span></span>

   <span data-ttu-id="c32e7-111">Następnie można otworzyć program Visual Studio z f# wybierając **Uruchom** w Instalatorze programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c32e7-111">You can then open Visual Studio with F# by choosing **Launch** in Visual Studio Installer.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="c32e7-112">Instalowanie języka F# za pomocą kodu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c32e7-112">Install F# with Visual Studio Code</span></span>

1. <span data-ttu-id="c32e7-113">Upewnij się, że [masz zainstalowany git](https://git-scm.com/download) i dostępne na path.</span><span class="sxs-lookup"><span data-stu-id="c32e7-113">Ensure you have [git](https://git-scm.com/download) installed and available on your PATH.</span></span> <span data-ttu-id="c32e7-114">Można sprawdzić, czy jest poprawnie zainstalowany, `git --version` wprowadzając w wierszu polecenia i naciskając **klawisz Enter**.</span><span class="sxs-lookup"><span data-stu-id="c32e7-114">You can verify that it's installed correctly by entering `git --version` at a command prompt and pressing **Enter**.</span></span>

2. <span data-ttu-id="c32e7-115">Zainstaluj zestaw [SDK .NET Core](https://dotnet.microsoft.com/download) i [kod programu Visual Studio](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="c32e7-115">Install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com).</span></span>

3. <span data-ttu-id="c32e7-116">Wybierz ikonę Rozszerzenia i wyszukaj hasło "Jonid":</span><span class="sxs-lookup"><span data-stu-id="c32e7-116">Select the Extensions icon and search for "Ionide":</span></span>

   <span data-ttu-id="c32e7-117">Jedyną wtyczką wymaganą do obsługi języka F# w kodzie programu Visual Studio jest [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="c32e7-117">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="c32e7-118">Jednak, można również zainstalować [Ionide-FAKE,](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) aby uzyskać [fałszywe](https://fake.build/) wsparcie i [Jonide-Paket,](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) aby uzyskać wsparcie [Paket.](https://fsprojects.github.io/Paket/)</span><span class="sxs-lookup"><span data-stu-id="c32e7-118">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="c32e7-119">FAKE i Paket są dodatkowe narzędzia społeczności F# do tworzenia projektów i zarządzania zależnościami, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c32e7-119">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="c32e7-120">Instalowanie języka F# za pomocą programu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="c32e7-120">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="c32e7-121">F# jest instalowany domyślnie w [programie Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), niezależnie od wybranej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c32e7-121">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="c32e7-122">Po zakończeniu instalacji wybierz pozycję **Uruchom program Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c32e7-122">After the install completes, choose **Start Visual Studio**.</span></span> <span data-ttu-id="c32e7-123">Program Visual Studio można również otworzyć za pośrednictwem programu Finder w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="c32e7-123">You can also open Visual Studio through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="c32e7-124">Instalowanie języka F# na serwerze kompilacji</span><span class="sxs-lookup"><span data-stu-id="c32e7-124">Install F# on a build server</span></span>

<span data-ttu-id="c32e7-125">Jeśli używasz .NET Core lub .NET Framework za pośrednictwem .NET SDK, wystarczy zainstalować .NET SDK na serwerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c32e7-125">If you're using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="c32e7-126">Ma wszystko, czego potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="c32e7-126">It has everything you need.</span></span>

<span data-ttu-id="c32e7-127">Jeśli używasz programu .NET Framework i **nie** używasz sdk .NET, następnie należy zainstalować [visual studio kompilacji narzędzia skudoczli na](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) serwerze Windows Server.</span><span class="sxs-lookup"><span data-stu-id="c32e7-127">If you're using .NET Framework and you are **not** using the .NET SDK, then you'll need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="c32e7-128">W instalatorze wybierz **narzędzia kompilacji pulpitu .NET**, a następnie wybierz składnik **kompilatora F#** po prawej stronie menu instalatora.</span><span class="sxs-lookup"><span data-stu-id="c32e7-128">In the installer, select **.NET desktop build tools**, and then select the **F# compiler** component on the right-hand side of the installer menu.</span></span>
