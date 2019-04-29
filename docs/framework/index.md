---
title: W dokumentacji .NET framework
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- f61f02f2-2f20-483d-8f56-a9c8f3a54986
helpviewer_keywords:
- .NET Framework, documentation
- documentation, .NET Framework
ms.assetid: f61f02f2-2f20-483d-8f56-a9c8f3a54986
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6e21d2514ad357c906885750d9320575bdb75b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643936"
---
# <a name="net-framework-guide"></a><span data-ttu-id="34e38-102">.NET framework — przewodnik</span><span class="sxs-lookup"><span data-stu-id="34e38-102">.NET Framework Guide</span></span>

> [!NOTE]
> <span data-ttu-id="34e38-103">Ten zestaw zawartości .NET Framework zawiera informacje o wersji programu .NET Framework 4.5, za pośrednictwem 4.8.</span><span class="sxs-lookup"><span data-stu-id="34e38-103">This .NET Framework content set includes information for .NET Framework versions 4.5 through 4.8.</span></span> <span data-ttu-id="34e38-104">Aby pobrać program .NET Framework, zobacz [Instalowanie programu .NET Framework](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="34e38-104">To download the .NET Framework, see [Installing the .NET Framework](./install/guide-for-developers.md).</span></span> <span data-ttu-id="34e38-105">Aby uzyskać listę nowych funkcji i zmian w .NET Framework, zobacz [What's New in .NET Framework](./whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="34e38-105">For a list of new features and changes in the NET Framework, see [What's New in the .NET Framework](./whats-new/index.md).</span></span> <span data-ttu-id="34e38-106">Aby uzyskać listę obsługiwanych platform, zobacz [.NET Framework System Requirements](./get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34e38-106">For a list of supported platforms, see [.NET Framework System Requirements](./get-started/system-requirements.md).</span></span> <span data-ttu-id="34e38-107">Aby uzyskać dokumentację starszych wersji programu .NET Framework, zobacz [dokumentacja poprzednich wersji .NET](https://docs.microsoft.com/previous-versions/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="34e38-107">For documentation about older versions of the .NET Framework, see [.NET previous versions documentation](https://docs.microsoft.com/previous-versions/dotnet/).</span></span>

<span data-ttu-id="34e38-108">.NET Framework to platforma deweloperska do tworzenia aplikacji dla sieci web, Windows, Windows Phone, Windows Server i Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="34e38-108">The .NET Framework is a development platform for building apps for web, Windows, Windows Phone, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="34e38-109">Obraz zawiera środowisko uruchomieniowe języka wspólnego (CLR) i biblioteki klas .NET Framework, która obejmuje szerokiej gamy funkcji oraz obsługę wielu standardów branżowych.</span><span class="sxs-lookup"><span data-stu-id="34e38-109">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="34e38-110">.NET Framework zawiera wiele usług, w tym zarządzanie pamięcią, bezpieczeństwo typu i pamięci, zabezpieczenia, sieci i wdrażanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34e38-110">The .NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="34e38-111">Zapewnia ona struktur danych łatwy w użyciu i interfejsów API, które abstrakcji systemu operacyjnego Windows niższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="34e38-111">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="34e38-112">Za pomocą różnych języków programowania .NET Framework, w tym C#, F#i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="34e38-112">You can use different programming languages with the .NET Framework, including C#, F#, and Visual Basic.</span></span>

<span data-ttu-id="34e38-113">Aby uzyskać ogólne wprowadzenie do programu .NET Framework dla użytkowników i deweloperów — zobacz [wprowadzenie](./get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="34e38-113">For a general introduction to the .NET Framework for both users and developers, see [Getting Started](./get-started/index.md).</span></span> <span data-ttu-id="34e38-114">Aby zapoznać się z wprowadzeniem do architektury i kluczowe funkcje programu .NET Framework, zobacz [Przegląd](./get-started/overview.md).</span><span class="sxs-lookup"><span data-stu-id="34e38-114">For an introduction to the architecture and key features of the .NET Framework, see the [overview](./get-started/overview.md).</span></span>

<span data-ttu-id="34e38-115">.NET Framework mogą być używane, za pomocą platformy Docker, jak i z [kontenery Windows](/virtualization/windowscontainers/about/).</span><span class="sxs-lookup"><span data-stu-id="34e38-115">The .NET Framework can be used with Docker and with [Windows Containers](/virtualization/windowscontainers/about/).</span></span> <span data-ttu-id="34e38-116">Zobacz [wdrażania .NET Framework aplikacje przy użyciu rozwiązania Docker](./docker/index.md) Aby dowiedzieć się, jak uruchamiać aplikacje w kontenerach platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="34e38-116">See [Deploying .NET Framework applications with Docker](./docker/index.md) to learn how to run your applications in Docker containers.</span></span>

## <a name="installation"></a><span data-ttu-id="34e38-117">Instalacja</span><span class="sxs-lookup"><span data-stu-id="34e38-117">Installation</span></span>

<span data-ttu-id="34e38-118">.NET Framework jest powiązana z Windows, co umożliwia uruchamianie aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34e38-118">The .NET Framework comes with Windows, enabling you to run .NET Framework applications.</span></span> <span data-ttu-id="34e38-119">Może być konieczne nowszej wersji programu .NET Framework niż ta, która pochodzi z wersją Windows.</span><span class="sxs-lookup"><span data-stu-id="34e38-119">You may need a later version of the .NET Framework than the one that comes with your Windows version.</span></span> <span data-ttu-id="34e38-120">Aby uzyskać więcej informacji, zobacz [Instalowanie programu .NET Framework na Windows](./install/index.md).</span><span class="sxs-lookup"><span data-stu-id="34e38-120">For more information, see [Install the .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="34e38-121">Zobacz [naprawy programu .NET Framework](./install/repair.md) dowiesz się, jak naprawić instalację .NET Framework, jeśli występują błędy podczas instalowania programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34e38-121">See [Repair the .NET Framework](./install/repair.md) to learn how to repair your .NET Framework installation if you're experiencing errors when installing the .NET Framework.</span></span>

<span data-ttu-id="34e38-122">Aby uzyskać szczegółowe informacje o pobieraniu programu .NET Framework, zobacz [Instalowanie programu .NET Framework dla deweloperów](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="34e38-122">For more detailed information on downloading the .NET Framework, see [Install the .NET Framework for developers](./install/guide-for-developers.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="34e38-123">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="34e38-123">In this section</span></span>

* [<span data-ttu-id="34e38-124">Co nowego</span><span class="sxs-lookup"><span data-stu-id="34e38-124">What's New</span></span>](./whats-new/index.md)  
<span data-ttu-id="34e38-125">Opis najważniejszych nowych funkcji i zmian w najnowszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34e38-125">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="34e38-126">Zawiera listy nieaktualnych typów i elementów członkowskich, a także przewodnik migracji aplikacji z poprzedniej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34e38-126">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>

* [<span data-ttu-id="34e38-127">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="34e38-127">Get Started</span></span>](./get-started/index.md)  
<span data-ttu-id="34e38-128">Wyczerpujące omówienie programu .NET Framework i łącza do dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="34e38-128">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>

* [<span data-ttu-id="34e38-129">Przewodnik instalacji</span><span class="sxs-lookup"><span data-stu-id="34e38-129">Installation Guide</span></span>](./install/index.md)  
<span data-ttu-id="34e38-130">Udostępnia zasoby i wskazówki dotyczące instalacji platformy .NET Framework i rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="34e38-130">Provides resources and guidance about .NET Framework installation and troubleshooting.</span></span>

* [<span data-ttu-id="34e38-131">Przewodnik migracji</span><span class="sxs-lookup"><span data-stu-id="34e38-131">Migration Guide</span></span>](./migration-guide/index.md)  
<span data-ttu-id="34e38-132">Udostępnia zasoby i listę zmian, które należy wziąć pod uwagę, jeśli przenosisz aplikację do nowej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34e38-132">Provides resources and a list of changes you need to consider if you're migrating your application to a new version of the .NET Framework.</span></span>

* [<span data-ttu-id="34e38-133">.NET Framework na platformie Docker — przewodnik</span><span class="sxs-lookup"><span data-stu-id="34e38-133">.NET Framework on Docker Guide</span></span>](./docker/index.md)  
<span data-ttu-id="34e38-134">Zapewnia zasoby do uruchamiania aplikacji .NET Framework za pomocą platformy Docker, przy użyciu kontenerów Windows.</span><span class="sxs-lookup"><span data-stu-id="34e38-134">Provides resources to run .NET Framework applications with Docker, using Windows Containers.</span></span>

* [<span data-ttu-id="34e38-135">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="34e38-135">Development Guide</span></span>](./development-guide.md)  
<span data-ttu-id="34e38-136">Przewodnik po wszystkich obszarach kluczowych technologii i zadaniach związanych z rozwojem aplikacji, takich jak tworzenie, konfigurowanie, debugowanie, zabezpieczanie i wdrażanie aplikacji, oraz informacje na temat programowania dynamicznego, interoperacyjności, rozszerzalności, zarządzania pamięcią i wątków.</span><span class="sxs-lookup"><span data-stu-id="34e38-136">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>

* [<span data-ttu-id="34e38-137">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="34e38-137">Tools</span></span>](./tools/index.md)  
<span data-ttu-id="34e38-138">Opis narzędzi, które pomagają tworzyć, konfigurować i wdrażać aplikacje przy użyciu technologii programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="34e38-138">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>

* [<span data-ttu-id="34e38-139">Dodatkowe biblioteki klas i interfejsy API</span><span class="sxs-lookup"><span data-stu-id="34e38-139">Additional class libraries and APIs</span></span>](./additional-apis/index.md)  
<span data-ttu-id="34e38-140">Zawiera dokumentację dotyczącą prywatny Framework interfejsów API platformy .NET używana przez narzędzia firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="34e38-140">Provides documentation for private .NET Framework APIs used by Microsoft tools.</span></span>

## <a name="see-also"></a><span data-ttu-id="34e38-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34e38-141">See also</span></span>

* [<span data-ttu-id="34e38-142">Biblioteka klas programu .NET framework</span><span class="sxs-lookup"><span data-stu-id="34e38-142">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.8)