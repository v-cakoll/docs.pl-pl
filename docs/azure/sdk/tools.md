---
title: Narzędzia dla deweloperów platformy Azure .NET i platformy .NET Core
description: Pobierz narzędzia, aby rozpocząć korzystanie z bibliotek platformy Azure .NET ze środowiska systemów Windows, Linux i Mac.
ms.date: 10/01/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 1c6370e4b3e5e6e901ba6ef56c65d794f3da5abe
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071942"
---
# <a name="tools-for-net-and-net-core-azure-developers"></a><span data-ttu-id="c1f7d-103">Narzędzia dla deweloperów platformy .NET i platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="c1f7d-103">Tools for .NET and .NET Core Azure developers</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="c1f7d-104">Pliki do pobrania zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="c1f7d-104">SDK downloads</span></span>

<span data-ttu-id="c1f7d-105">Biblioteki platformy Azure dla platformy .NET są implementowane jako [pakiety NuGet](https://www.nuget.org/packages?q=windowsazureofficial).</span><span class="sxs-lookup"><span data-stu-id="c1f7d-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="c1f7d-106">Zapoznaj się z dokumentacją [interfejsu API](/dotnet/api/overview/azure/?view=azure-dotnet) w celu uzyskania instrukcji instalacji zorganizowanych według usługi platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="c1f7d-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for installation instructions organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="c1f7d-107">Narzędzia programistyczne</span><span class="sxs-lookup"><span data-stu-id="c1f7d-107">Development tools</span></span>

<span data-ttu-id="c1f7d-108">Program Visual Studio zawiera narzędzia dla wielu wbudowanych usług platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="c1f7d-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="c1f7d-109">Niektóre usługi platformy Azure mają dostępne dodatkowe narzędzia lub emulatory, takie jak [Eksplorator usługi Azure Storage](https://azure.microsoft.com/features/storage-explorer/).</span><span class="sxs-lookup"><span data-stu-id="c1f7d-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="c1f7d-110">W razie potrzeby zapoznaj się z dokumentacją usługi platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="c1f7d-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="c1f7d-111">Te instrukcje instalują zalecane uruchomienie środowiska deweloperskiego dla danego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c1f7d-111">These instructions install the recommended starting development environment for your operating system.</span></span>

## <a name="windows"></a>[<span data-ttu-id="c1f7d-112">Windows</span><span class="sxs-lookup"><span data-stu-id="c1f7d-112">Windows</span></span>](#tab/windows)

<span data-ttu-id="c1f7d-113">Program Visual Studio w wersji 2017 i nowszej ma wbudowaną obsługę programowania na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="c1f7d-113">Visual Studio versions 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="c1f7d-114">Poniższe kroki opisują włączenie obsługi projektowania platformy Azure w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c1f7d-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="c1f7d-115">W przypadku programu Visual Studio 2015 i wcześniejszych należy <a href="vs2015-install.md">wykonać te instrukcje</a>.</span><span class="sxs-lookup"><span data-stu-id="c1f7d-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="c1f7d-116">Krok 1. Pobieranie programu Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="c1f7d-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="c1f7d-117">Możesz pominąć ten krok, jeśli masz już zainstalowany program Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="c1f7d-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1f7d-118">Pobierz program Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="c1f7d-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="c1f7d-119">Krok 2. Instalowanie dwóch obciążeń platformy Azure</span><span class="sxs-lookup"><span data-stu-id="c1f7d-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="c1f7d-120">W Instalatorze programu Visual Studio Zainstaluj program Visual Studio (lub zmodyfikuj istniejącą instalację).</span><span class="sxs-lookup"><span data-stu-id="c1f7d-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="c1f7d-121">Upewnij się, że wybrano obciążenia na *platformie Azure* i *ASP.NET i programowanie dla sieci Web* .</span><span class="sxs-lookup"><span data-stu-id="c1f7d-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="c1f7d-122">Krok 3. Programowanie przy użyciu platformy .NET na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="c1f7d-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="c1f7d-123">Zacznij od [wdrożenia pierwszej ASP.NET Core aplikacji sieci Web na Azure App Service](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).</span><span class="sxs-lookup"><span data-stu-id="c1f7d-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="macos"></a>[<span data-ttu-id="c1f7d-124">macOS</span><span class="sxs-lookup"><span data-stu-id="c1f7d-124">macOS</span></span>](#tab/macos)

<span data-ttu-id="c1f7d-125">Visual Studio dla komputerów Mac ma wszystko, czego potrzebujesz do programowania na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="c1f7d-125">Visual Studio for Mac has everything you need for Azure development.</span></span>

### <a name="step-1-download-visual-studio-for-mac"></a><span data-ttu-id="c1f7d-126">Krok 1. Pobieranie Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="c1f7d-126">Step 1: Download Visual Studio for Mac</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1f7d-127">Pobierz Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="c1f7d-127">Download Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

<span data-ttu-id="c1f7d-128">Podczas instalacji domyślnie wybrane są narzędzia platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="c1f7d-128">During installation, Azure tools are selected by default.</span></span>

## <a name="linux"></a>[<span data-ttu-id="c1f7d-129">Linux</span><span class="sxs-lookup"><span data-stu-id="c1f7d-129">Linux</span></span>](#tab/linux)

<span data-ttu-id="c1f7d-130">Visual Studio Code ma wszystko, czego potrzebujesz do programowania na platformie Azure w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="c1f7d-130">Visual Studio Code has everything you need for Azure development on Linux.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="c1f7d-131">Krok 1. Pobieranie zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c1f7d-131">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="c1f7d-132">Zestaw SDK i narzędzia wiersza polecenia dla aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c1f7d-132">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1f7d-133">Pobierz zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="c1f7d-133">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="c1f7d-134">Krok 2. Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c1f7d-134">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="c1f7d-135">Edytuj i Debuguj aplikacje platformy .NET Core w dowolnym systemie operacyjnym: Windows, Mac i Linux.</span><span class="sxs-lookup"><span data-stu-id="c1f7d-135">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1f7d-136">Pobierz Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c1f7d-136">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

---
