---
title: Dokumentacja .NET Framework
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
ms.openlocfilehash: e5a86b3abf821a37944a0e478d0bc8f1bea31ccb
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699054"
---
# <a name="net-framework-guide"></a><span data-ttu-id="8ebb5-102">.NET framework — przewodnik</span><span class="sxs-lookup"><span data-stu-id="8ebb5-102">.NET Framework Guide</span></span>

> [!NOTE]
> <span data-ttu-id="8ebb5-103">Ten .NET Framework zestawu zawartości zawiera informacje dotyczące .NET Framework wersji 4,5 do 4,8.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-103">This .NET Framework content set includes information for .NET Framework versions 4.5 through 4.8.</span></span> <span data-ttu-id="8ebb5-104">Aby pobrać .NET Framework, zobacz [instalowanie .NET Framework](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="8ebb5-104">To download the .NET Framework, see [Installing the .NET Framework](./install/guide-for-developers.md).</span></span> <span data-ttu-id="8ebb5-105">Aby zapoznać się z listą nowych funkcji i zmian w środowisku .NET Framework, zobacz [co nowego w .NET Framework](./whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ebb5-105">For a list of new features and changes in the NET Framework, see [What's New in the .NET Framework](./whats-new/index.md).</span></span> <span data-ttu-id="8ebb5-106">Aby zapoznać się z listą obsługiwanych platform, zobacz [wymagania systemowe .NET Framework](./get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ebb5-106">For a list of supported platforms, see [.NET Framework System Requirements](./get-started/system-requirements.md).</span></span> <span data-ttu-id="8ebb5-107">Aby uzyskać dokumentację dotyczącą starszych wersji .NET Framework, zobacz [dokumentację dotyczącą poprzednich wersji programu .NET](https://docs.microsoft.com/previous-versions/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="8ebb5-107">For documentation about older versions of the .NET Framework, see [.NET previous versions documentation](https://docs.microsoft.com/previous-versions/dotnet/).</span></span>

<span data-ttu-id="8ebb5-108">.NET Framework to platforma programistyczna służąca do tworzenia aplikacji dla sieci Web, systemu Windows, Windows Phone, systemu Windows Server i Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-108">The .NET Framework is a development platform for building apps for web, Windows, Windows Phone, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="8ebb5-109">Składa się ze środowiska uruchomieniowego języka wspólnego (CLR) i biblioteki klas .NET Framework, która obejmuje szeroką gamę funkcji i obsługę wielu standardów branżowych.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-109">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="8ebb5-110">.NET Framework udostępnia wiele usług, w tym zarządzanie pamięcią, bezpieczeństwo typów i pamięci, zabezpieczenia, sieci i wdrażanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-110">The .NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="8ebb5-111">Zapewnia ona łatwą w użyciu struktury danych i interfejsy API, które stanowią abstrakcyjny system operacyjny Windows niższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-111">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="8ebb5-112">Możesz użyć różnych języków programowania z .NET Framework, w tym C#, F#i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-112">You can use different programming languages with the .NET Framework, including C#, F#, and Visual Basic.</span></span>

<span data-ttu-id="8ebb5-113">Aby uzyskać ogólne wprowadzenie do .NET Framework dla użytkowników i deweloperów, zobacz [wprowadzenie](./get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ebb5-113">For a general introduction to the .NET Framework for both users and developers, see [Getting Started](./get-started/index.md).</span></span> <span data-ttu-id="8ebb5-114">Aby zapoznać się z wprowadzeniem do architektury i kluczowych funkcji .NET Framework, zobacz [Omówienie](./get-started/overview.md).</span><span class="sxs-lookup"><span data-stu-id="8ebb5-114">For an introduction to the architecture and key features of the .NET Framework, see the [overview](./get-started/overview.md).</span></span>

<span data-ttu-id="8ebb5-115">.NET Framework może być używana z [kontenerami](/virtualization/windowscontainers/about/)Docker i Windows.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-115">The .NET Framework can be used with Docker and with [Windows Containers](/virtualization/windowscontainers/about/).</span></span>

## <a name="installation"></a><span data-ttu-id="8ebb5-116">Instalacja</span><span class="sxs-lookup"><span data-stu-id="8ebb5-116">Installation</span></span>

<span data-ttu-id="8ebb5-117">.NET Framework jest dostarczany z systemem Windows, umożliwiając uruchamianie aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-117">The .NET Framework comes with Windows, enabling you to run .NET Framework applications.</span></span> <span data-ttu-id="8ebb5-118">Może być potrzebna nowsza wersja .NET Framework niż ta, która jest dostarczana z wersją systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-118">You may need a later version of the .NET Framework than the one that comes with your Windows version.</span></span> <span data-ttu-id="8ebb5-119">Aby uzyskać więcej informacji, zobacz [instalowanie .NET Framework w systemie Windows](./install/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ebb5-119">For more information, see [Install the .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="8ebb5-120">Zobacz [naprawa .NET Framework,](./install/repair.md) aby dowiedzieć się, jak naprawić instalację .NET Framework, jeśli występują błędy podczas instalowania .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-120">See [Repair the .NET Framework](./install/repair.md) to learn how to repair your .NET Framework installation if you're experiencing errors when installing the .NET Framework.</span></span>

<span data-ttu-id="8ebb5-121">Aby uzyskać szczegółowe informacje na temat pobierania .NET Framework, zobacz [instalowanie .NET Framework dla deweloperów](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="8ebb5-121">For more detailed information on downloading the .NET Framework, see [Install the .NET Framework for developers](./install/guide-for-developers.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8ebb5-122">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8ebb5-122">In this section</span></span>

* [<span data-ttu-id="8ebb5-123">Co nowego?</span><span class="sxs-lookup"><span data-stu-id="8ebb5-123">What's New</span></span>](./whats-new/index.md)  
<span data-ttu-id="8ebb5-124">Opis najważniejszych nowych funkcji i zmian w najnowszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="8ebb5-125">Zawiera listy nieaktualnych typów i elementów członkowskich, a także przewodnik migracji aplikacji z poprzedniej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>

* [<span data-ttu-id="8ebb5-126">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8ebb5-126">Get Started</span></span>](./get-started/index.md)  
<span data-ttu-id="8ebb5-127">Wyczerpujące omówienie programu .NET Framework i łącza do dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>

* [<span data-ttu-id="8ebb5-128">Przewodnik instalacji</span><span class="sxs-lookup"><span data-stu-id="8ebb5-128">Installation Guide</span></span>](./install/index.md)  
<span data-ttu-id="8ebb5-129">Zawiera zasoby i wskazówki dotyczące instalacji .NET Framework i rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-129">Provides resources and guidance about .NET Framework installation and troubleshooting.</span></span>

* [<span data-ttu-id="8ebb5-130">Przewodnik migracji</span><span class="sxs-lookup"><span data-stu-id="8ebb5-130">Migration Guide</span></span>](./migration-guide/index.md)  
<span data-ttu-id="8ebb5-131">Zawiera zasoby i listę zmian, które należy wziąć pod uwagę w przypadku migrowania aplikacji do nowej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-131">Provides resources and a list of changes you need to consider if you're migrating your application to a new version of the .NET Framework.</span></span>

* [<span data-ttu-id="8ebb5-132">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="8ebb5-132">Development Guide</span></span>](./development-guide.md)  
<span data-ttu-id="8ebb5-133">Przewodnik po wszystkich obszarach kluczowych technologii i zadaniach związanych z rozwojem aplikacji, takich jak tworzenie, konfigurowanie, debugowanie, zabezpieczanie i wdrażanie aplikacji, oraz informacje na temat programowania dynamicznego, interoperacyjności, rozszerzalności, zarządzania pamięcią i wątków.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-133">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>

* [<span data-ttu-id="8ebb5-134">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="8ebb5-134">Tools</span></span>](./tools/index.md)  
<span data-ttu-id="8ebb5-135">Opis narzędzi, które pomagają tworzyć, konfigurować i wdrażać aplikacje przy użyciu technologii programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-135">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>

* [<span data-ttu-id="8ebb5-136">Dodatkowe biblioteki klas i interfejsy API</span><span class="sxs-lookup"><span data-stu-id="8ebb5-136">Additional class libraries and APIs</span></span>](./additional-apis/index.md)  
<span data-ttu-id="8ebb5-137">Zawiera dokumentację prywatnych interfejsów API .NET Framework używanych przez narzędzia firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8ebb5-137">Provides documentation for private .NET Framework APIs used by Microsoft tools.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ebb5-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ebb5-138">See also</span></span>

- [<span data-ttu-id="8ebb5-139">Biblioteka klas .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8ebb5-139">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.8)
