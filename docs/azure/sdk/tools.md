---
title: Narzędzia dla deweloperów platformy Azure .NET i .NET Core
description: Pobierz narzędzia, aby rozpocząć korzystanie z bibliotek platformy Azure .NET ze środowiska Windows, Linux i Mac.
ms.date: 10/01/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 1c6370e4b3e5e6e901ba6ef56c65d794f3da5abe
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071942"
---
# <a name="tools-for-net-and-net-core-azure-developers"></a><span data-ttu-id="b11c0-103">Narzędzia dla deweloperów platformy Azure platformy .NET i core core</span><span class="sxs-lookup"><span data-stu-id="b11c0-103">Tools for .NET and .NET Core Azure developers</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="b11c0-104">Pliki do pobrania sdk</span><span class="sxs-lookup"><span data-stu-id="b11c0-104">SDK downloads</span></span>

<span data-ttu-id="b11c0-105">Biblioteki platformy Azure dla platformy .NET są implementowane jako [pakiety NuGet](https://www.nuget.org/packages?q=windowsazureofficial).</span><span class="sxs-lookup"><span data-stu-id="b11c0-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="b11c0-106">Zapoznaj się z [dokumentacją interfejsu API,](/dotnet/api/overview/azure/?view=azure-dotnet) aby uzyskać instrukcje instalacji uporządkowane przez usługę platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b11c0-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for installation instructions organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="b11c0-107">Narzędzia programistyczne</span><span class="sxs-lookup"><span data-stu-id="b11c0-107">Development tools</span></span>

<span data-ttu-id="b11c0-108">Visual Studio ma narzędzia dla wielu usług platformy Azure wbudowanych.</span><span class="sxs-lookup"><span data-stu-id="b11c0-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="b11c0-109">Niektóre usługi platformy Azure mają dostępne dodatkowe narzędzia lub emulatory, takie jak [Eksplorator usługi Azure Storage.](https://azure.microsoft.com/features/storage-explorer/)</span><span class="sxs-lookup"><span data-stu-id="b11c0-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="b11c0-110">W razie potrzeby zapoznaj się z dokumentacją usługi platformy Azure, aby uzyskać dodatkowe narzędzia.</span><span class="sxs-lookup"><span data-stu-id="b11c0-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="b11c0-111">Te instrukcje instalują zalecane środowisko programistyczne dla systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b11c0-111">These instructions install the recommended starting development environment for your operating system.</span></span>

## <a name="windows"></a>[<span data-ttu-id="b11c0-112">Windows</span><span class="sxs-lookup"><span data-stu-id="b11c0-112">Windows</span></span>](#tab/windows)

<span data-ttu-id="b11c0-113">Visual Studio w wersjach 2017 i nowszych mają wbudowaną obsługę tworzenia platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b11c0-113">Visual Studio versions 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="b11c0-114">W poniższych krokach opisano włączenie obsługi programistycznej platformy Azure w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b11c0-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="b11c0-115">W programie Visual Studio 2015 i wcześniejszych <a href="vs2015-install.md">należy postępować zgodnie z tymi instrukcjami.</a></span><span class="sxs-lookup"><span data-stu-id="b11c0-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="b11c0-116">Krok 1: Pobierz program Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="b11c0-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="b11c0-117">Ten krok można pominąć, jeśli masz już zainstalowany program Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="b11c0-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b11c0-118">Pobierz program Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="b11c0-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="b11c0-119">Krok 2: Instalowanie dwóch obciążeń platformy Azure</span><span class="sxs-lookup"><span data-stu-id="b11c0-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="b11c0-120">W instalatorze programu Visual Studio zainstaluj program Visual Studio (lub zmodyfikuj istniejącą instalację).</span><span class="sxs-lookup"><span data-stu-id="b11c0-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="b11c0-121">Upewnij się, że są wybrane obciążenia *deweloperów* i ASP.NET platformy Azure *i tworzenia sieci Web.*</span><span class="sxs-lookup"><span data-stu-id="b11c0-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="b11c0-122">Krok 3: Rozwijaj się za pomocą platformy .NET na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="b11c0-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="b11c0-123">Rozpocznij [wdrażanie pierwszej ASP.NET aplikacji sieci Web w usłudze Azure App Service.](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet)</span><span class="sxs-lookup"><span data-stu-id="b11c0-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="macos"></a>[<span data-ttu-id="b11c0-124">macOS</span><span class="sxs-lookup"><span data-stu-id="b11c0-124">macOS</span></span>](#tab/macos)

<span data-ttu-id="b11c0-125">Program Visual Studio dla komputerów Mac ma wszystko, czego potrzebujesz do tworzenia platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="b11c0-125">Visual Studio for Mac has everything you need for Azure development.</span></span>

### <a name="step-1-download-visual-studio-for-mac"></a><span data-ttu-id="b11c0-126">Krok 1: Pobierz program Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="b11c0-126">Step 1: Download Visual Studio for Mac</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b11c0-127">Pobieranie programu Visual Studio dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="b11c0-127">Download Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

<span data-ttu-id="b11c0-128">Podczas instalacji narzędzia platformy Azure są wybierane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="b11c0-128">During installation, Azure tools are selected by default.</span></span>

## <a name="linux"></a>[<span data-ttu-id="b11c0-129">Linux</span><span class="sxs-lookup"><span data-stu-id="b11c0-129">Linux</span></span>](#tab/linux)

<span data-ttu-id="b11c0-130">Visual Studio Code ma wszystko, czego potrzebujesz do tworzenia platformy Azure w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="b11c0-130">Visual Studio Code has everything you need for Azure development on Linux.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="b11c0-131">Krok 1: Pobierz podstawowy sdk .NET</span><span class="sxs-lookup"><span data-stu-id="b11c0-131">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="b11c0-132">Zestaw SDK i narzędzia wiersza polecenia dla aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b11c0-132">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b11c0-133">Pobierz core sdk .NET</span><span class="sxs-lookup"><span data-stu-id="b11c0-133">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="b11c0-134">Krok 2: Kod programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b11c0-134">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="b11c0-135">Edytuj i debuguj aplikacje .NET Core w dowolnym systemie operacyjnym: Windows, Mac i Linux.</span><span class="sxs-lookup"><span data-stu-id="b11c0-135">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b11c0-136">Pobierz kod programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b11c0-136">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

---
