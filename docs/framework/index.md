---
title: Dokumentacja programu .NET Framework
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- f61f02f2-2f20-483d-8f56-a9c8f3a54986
helpviewer_keywords:
- .NET Framework, documentation
- documentation, .NET Framework
ms.assetid: f61f02f2-2f20-483d-8f56-a9c8f3a54986
ms.openlocfilehash: d94d97cd1b519025ff360dc903558ea3656818d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181531"
---
# <a name="net-framework-guide"></a><span data-ttu-id="f4410-102">.NET framework — przewodnik</span><span class="sxs-lookup"><span data-stu-id="f4410-102">.NET Framework guide</span></span>

> [!NOTE]
> <span data-ttu-id="f4410-103">Ten zestaw zawartości programu .NET Framework zawiera informacje dotyczące programu .NET Framework w wersji od 4.5 do 4.8.</span><span class="sxs-lookup"><span data-stu-id="f4410-103">This .NET Framework content set includes information for .NET Framework versions 4.5 through 4.8.</span></span> <span data-ttu-id="f4410-104">Aby pobrać program .NET Framework, zobacz [Instalowanie programu .NET Framework](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="f4410-104">To download .NET Framework, see [Install .NET Framework](./install/guide-for-developers.md).</span></span> <span data-ttu-id="f4410-105">Aby uzyskać listę nowych funkcji i zmian w .NET Framework, zobacz [Co nowego w programach .NET Framework](./whats-new/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4410-105">For a list of new features and changes in .NET Framework, see [What's New in .NET Framework](./whats-new/index.md).</span></span> <span data-ttu-id="f4410-106">Aby uzyskać listę obsługiwanych platform, zobacz [.NET Framework Wymagania systemowe](./get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4410-106">For a list of supported platforms, see [.NET Framework System Requirements](./get-started/system-requirements.md).</span></span> <span data-ttu-id="f4410-107">Dokumentacja dotycząca starszych wersji programu .NET Framework można znaleźć w [dokumentacji dotyczącej poprzednich wersji platformy .NET](https://docs.microsoft.com/previous-versions/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="f4410-107">For documentation about older versions of .NET Framework, see [.NET previous versions documentation](https://docs.microsoft.com/previous-versions/dotnet/).</span></span>

<span data-ttu-id="f4410-108">Program .NET Framework to platforma programowa do tworzenia aplikacji dla sieci Web, Systemu Windows, Windows Server i Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="f4410-108">.NET Framework is a development platform for building apps for web, Windows, Windows Server, and Microsoft Azure.</span></span> <span data-ttu-id="f4410-109">Składa się ze środowiska wykonawczego języka wspólnego (CLR) i biblioteki klas .NET Framework, która zawiera szeroki zakres funkcji i obsługi wielu standardów branżowych.</span><span class="sxs-lookup"><span data-stu-id="f4410-109">It consists of the common language runtime (CLR) and the .NET Framework class library, which includes a broad range of functionality and support for many industry standards.</span></span>

<span data-ttu-id="f4410-110">.NET Framework zapewnia wiele usług, w tym zarządzanie pamięcią, bezpieczeństwo typów i pamięci, zabezpieczenia, sieci i wdrażanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4410-110">.NET Framework provides many services, including memory management, type and memory safety, security, networking, and application deployment.</span></span> <span data-ttu-id="f4410-111">Zapewnia łatwe w użyciu struktury danych i interfejsy API, które abstrakcji niższego poziomu systemu operacyjnego Windows.</span><span class="sxs-lookup"><span data-stu-id="f4410-111">It provides easy-to-use data structures and APIs that abstract the lower-level Windows operating system.</span></span> <span data-ttu-id="f4410-112">W programie .NET Framework można używać różnych języków programowania, w tym języka C#, F#i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f4410-112">You can use different programming languages with .NET Framework, including C#, F#, and Visual Basic.</span></span>

<span data-ttu-id="f4410-113">Aby uzyskać ogólne wprowadzenie do programu .NET Framework zarówno dla użytkowników, jak i deweloperów, zobacz [Wprowadzenie](./get-started/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4410-113">For a general introduction to .NET Framework for both users and developers, see [Getting Started](./get-started/index.md).</span></span> <span data-ttu-id="f4410-114">Aby zapoznać się z wprowadzeniem do architektury i kluczowych funkcji programu .NET Framework, zobacz [omówienie](./get-started/overview.md).</span><span class="sxs-lookup"><span data-stu-id="f4410-114">For an introduction to the architecture and key features of .NET Framework, see the [overview](./get-started/overview.md).</span></span>

<span data-ttu-id="f4410-115">Program .NET Framework może być używany z platformą Docker i [kontenerami systemu Windows](/virtualization/windowscontainers/about/).</span><span class="sxs-lookup"><span data-stu-id="f4410-115">.NET Framework can be used with Docker and with [Windows Containers](/virtualization/windowscontainers/about/).</span></span>

## <a name="installation"></a><span data-ttu-id="f4410-116">Instalacja</span><span class="sxs-lookup"><span data-stu-id="f4410-116">Installation</span></span>

<span data-ttu-id="f4410-117">Program .NET Framework jest dostarczany z systemem Windows, który umożliwia uruchamianie aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4410-117">.NET Framework comes with Windows, which enables you to run .NET Framework applications.</span></span> <span data-ttu-id="f4410-118">Może być potrzebna nowsza wersja programu .NET Framework niż ta, która jest dostępna w wersji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f4410-118">You may need a later version of .NET Framework than the one that comes with your Windows version.</span></span> <span data-ttu-id="f4410-119">Aby uzyskać więcej informacji, zobacz [Instalowanie programu .NET Framework w systemie Windows](./install/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4410-119">For more information, see [Install .NET Framework on Windows](./install/index.md).</span></span>

<span data-ttu-id="f4410-120">Aby dowiedzieć się, jak naprawić instalację programu .NET Framework, jeśli podczas instalacji występują błędy, zobacz [Naprawianie programu .NET Framework](./install/repair.md).</span><span class="sxs-lookup"><span data-stu-id="f4410-120">To learn how to repair your .NET Framework installation if you're experiencing errors during installation, see [Repair .NET Framework](./install/repair.md).</span></span>

<span data-ttu-id="f4410-121">Aby uzyskać bardziej szczegółowe informacje dotyczące pobierania programu .NET Framework, zobacz [Instalowanie programu .NET Framework dla deweloperów](./install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="f4410-121">For more detailed information on downloading .NET Framework, see [Install the .NET Framework for developers](./install/guide-for-developers.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f4410-122">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f4410-122">In this section</span></span>

* [<span data-ttu-id="f4410-123">Co nowego</span><span class="sxs-lookup"><span data-stu-id="f4410-123">What's New</span></span>](./whats-new/index.md)  
<span data-ttu-id="f4410-124">Opis najważniejszych nowych funkcji i zmian w najnowszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4410-124">Describes key new features and changes in the latest versions of the .NET Framework.</span></span> <span data-ttu-id="f4410-125">Zawiera listy nieaktualnych typów i elementów członkowskich, a także przewodnik migracji aplikacji z poprzedniej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4410-125">Includes lists of obsolete types and members, and provides a guide for migrating your applications from the previous version of the .NET Framework.</span></span>

* [<span data-ttu-id="f4410-126">Rozpocząć</span><span class="sxs-lookup"><span data-stu-id="f4410-126">Get Started</span></span>](./get-started/index.md)  
<span data-ttu-id="f4410-127">Wyczerpujące omówienie programu .NET Framework i łącza do dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f4410-127">Provides a comprehensive overview of the .NET Framework and links to additional resources.</span></span>

* [<span data-ttu-id="f4410-128">Przewodnik instalacji</span><span class="sxs-lookup"><span data-stu-id="f4410-128">Installation Guide</span></span>](./install/index.md)  
<span data-ttu-id="f4410-129">Zawiera zasoby i wskazówki dotyczące instalacji i rozwiązywania problemów z platformą .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4410-129">Provides resources and guidance about .NET Framework installation and troubleshooting.</span></span>

* [<span data-ttu-id="f4410-130">Przewodnik po migracji</span><span class="sxs-lookup"><span data-stu-id="f4410-130">Migration Guide</span></span>](./migration-guide/index.md)  
<span data-ttu-id="f4410-131">Zawiera zasoby i listę zmian, które należy wziąć pod uwagę, jeśli przeprowadzasz migrację aplikacji do nowej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4410-131">Provides resources and a list of changes you need to consider if you're migrating your application to a new version of the .NET Framework.</span></span>

* [<span data-ttu-id="f4410-132">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="f4410-132">Development Guide</span></span>](./development-guide.md)  
<span data-ttu-id="f4410-133">Przewodnik po wszystkich obszarach kluczowych technologii i zadaniach związanych z rozwojem aplikacji, takich jak tworzenie, konfigurowanie, debugowanie, zabezpieczanie i wdrażanie aplikacji, oraz informacje na temat programowania dynamicznego, interoperacyjności, rozszerzalności, zarządzania pamięcią i wątków.</span><span class="sxs-lookup"><span data-stu-id="f4410-133">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>

* [<span data-ttu-id="f4410-134">narzędzia</span><span class="sxs-lookup"><span data-stu-id="f4410-134">Tools</span></span>](./tools/index.md)  
<span data-ttu-id="f4410-135">Opis narzędzi, które pomagają tworzyć, konfigurować i wdrażać aplikacje przy użyciu technologii programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f4410-135">Describes the tools that help you develop, configure, and deploy applications by using .NET Framework technologies.</span></span>

* [<span data-ttu-id="f4410-136">Dodatkowe biblioteki klas i interfejsy API</span><span class="sxs-lookup"><span data-stu-id="f4410-136">Additional class libraries and APIs</span></span>](./additional-apis/index.md)  
<span data-ttu-id="f4410-137">Zawiera dokumentację prywatnych interfejsów API programu .NET Framework używanych przez narzędzia firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4410-137">Provides documentation for private .NET Framework APIs used by Microsoft tools.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4410-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4410-138">See also</span></span>

* [<span data-ttu-id="f4410-139">Biblioteka klas programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f4410-139">.NET Framework Class Library</span></span>](/dotnet/api/?view=netframework-4.8)
