---
title: Narzędzia dla deweloperów platformy Azure
description: Pobierz narzędzia, aby rozpocząć korzystanie z bibliotek platformy Azure .NET ze środowiska systemów Windows, Linux i Mac.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: fa645b152f15550b25a3542ba0cdbb43799536b9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174954"
---
# <a name="azure-tools-for-developing-with-net"></a><span data-ttu-id="31bc4-103">Narzędzia platformy Azure do programowania przy użyciu platformy .NET</span><span class="sxs-lookup"><span data-stu-id="31bc4-103">Azure tools for developing with .NET</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="31bc4-104">Pliki do pobrania zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="31bc4-104">SDK downloads</span></span>

<span data-ttu-id="31bc4-105">Biblioteki platformy Azure dla platformy .NET są implementowane jako [pakiety NuGet](https://www.nuget.org/packages?q=windowsazureofficial).</span><span class="sxs-lookup"><span data-stu-id="31bc4-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="31bc4-106">Zobacz dokumentację [interfejsu API](/dotnet/api/overview/azure/?view=azure-dotnet) , aby zapoznać się z dokumentacją referencyjną uporządkowaną według usługi platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="31bc4-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for reference documentation organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="31bc4-107">Narzędzia programistyczne</span><span class="sxs-lookup"><span data-stu-id="31bc4-107">Development tools</span></span>

<span data-ttu-id="31bc4-108">Program Visual Studio zawiera narzędzia dla wielu wbudowanych usług platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="31bc4-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="31bc4-109">Niektóre usługi platformy Azure mają dostępne dodatkowe narzędzia lub emulatory, takie jak [Eksplorator usługi Azure Storage](https://azure.microsoft.com/features/storage-explorer/).</span><span class="sxs-lookup"><span data-stu-id="31bc4-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="31bc4-110">W razie potrzeby zapoznaj się z dokumentacją usługi platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="31bc4-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="31bc4-111">Wybierz odpowiednie środowisko programistyczne poniżej.</span><span class="sxs-lookup"><span data-stu-id="31bc4-111">Select your preferred development environment below.</span></span>

## <a name="visual-studio-on-windows"></a>[<span data-ttu-id="31bc4-112">Program Visual Studio w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="31bc4-112">Visual Studio on Windows</span></span>](#tab/vs)

<span data-ttu-id="31bc4-113">Program Visual Studio w wersji 2017 lub nowszej ma wbudowaną obsługę programowania na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="31bc4-113">Visual Studio version 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="31bc4-114">Poniższe kroki opisują włączenie obsługi projektowania platformy Azure w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="31bc4-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="31bc4-115">W przypadku programu Visual Studio 2015 i wcześniejszych należy <a href="vs2015-install.md">wykonać te instrukcje</a>.</span><span class="sxs-lookup"><span data-stu-id="31bc4-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="31bc4-116">Krok 1. Pobieranie programu Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="31bc4-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="31bc4-117">Możesz pominąć ten krok, jeśli masz już zainstalowany program Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="31bc4-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="31bc4-118">Pobierz program Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="31bc4-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="31bc4-119">Krok 2. Instalowanie dwóch obciążeń platformy Azure</span><span class="sxs-lookup"><span data-stu-id="31bc4-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="31bc4-120">W Instalatorze programu Visual Studio Zainstaluj program Visual Studio (lub zmodyfikuj istniejącą instalację).</span><span class="sxs-lookup"><span data-stu-id="31bc4-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="31bc4-121">Upewnij się, że wybrano obciążenia na *platformie Azure* i *ASP.NET i programowanie dla sieci Web* .</span><span class="sxs-lookup"><span data-stu-id="31bc4-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="31bc4-122">Krok 3. Programowanie przy użyciu platformy .NET na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="31bc4-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="31bc4-123">Zacznij od [wdrożenia pierwszej ASP.NET Core aplikacji sieci Web na Azure App Service](/azure/app-service-web/app-service-web-get-started-dotnet).</span><span class="sxs-lookup"><span data-stu-id="31bc4-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="visual-studio-code-cross-platform"></a>[<span data-ttu-id="31bc4-124">Visual Studio Code (wiele platform)</span><span class="sxs-lookup"><span data-stu-id="31bc4-124">Visual Studio Code (cross-platform)</span></span>](#tab/vscode)

<span data-ttu-id="31bc4-125">Visual Studio Code ma wszystko, czego potrzebujesz do tworzenia aplikacji dla wielu platform na platformie Azure.</span><span class="sxs-lookup"><span data-stu-id="31bc4-125">Visual Studio Code has everything you need for cross-platform Azure development.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="31bc4-126">Krok 1. Pobieranie zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="31bc4-126">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="31bc4-127">Zestaw SDK i narzędzia wiersza polecenia dla aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="31bc4-127">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="31bc4-128">Pobierz zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="31bc4-128">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="31bc4-129">Krok 2. Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="31bc4-129">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="31bc4-130">Edytuj i Debuguj aplikacje platformy .NET Core w dowolnym systemie operacyjnym: Windows, Mac i Linux.</span><span class="sxs-lookup"><span data-stu-id="31bc4-130">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="31bc4-131">Pobierz Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="31bc4-131">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

### <a name="step-3-azure-tools-extension"></a><span data-ttu-id="31bc4-132">Krok 3. rozszerzenie narzędzi platformy Azure</span><span class="sxs-lookup"><span data-stu-id="31bc4-132">Step 3: Azure Tools extension</span></span>

<span data-ttu-id="31bc4-133">Zainstaluj rozszerzenie narzędzi platformy Azure w Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="31bc4-133">Install the Azure Tools extension in Visual Studio Code.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="31bc4-134">Zainstaluj rozszerzenie narzędzi platformy Azure</span><span class="sxs-lookup"><span data-stu-id="31bc4-134">Install Azure Tools extension</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)

### <a name="step-4-develop-with-net-on-azure"></a><span data-ttu-id="31bc4-135">Krok 4. Programowanie przy użyciu platformy .NET na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="31bc4-135">Step 4: Develop with .NET on Azure</span></span>

<span data-ttu-id="31bc4-136">Zacznij od [wdrożenia pierwszej ASP.NET Core aplikacji sieci Web na Azure App Service w systemie Linux](/azure/app-service/containers/quickstart-dotnetcore).</span><span class="sxs-lookup"><span data-stu-id="31bc4-136">Get started by [deploying your first ASP.NET Core web app on Azure App Service on Linux](/azure/app-service/containers/quickstart-dotnetcore).</span></span>

---
