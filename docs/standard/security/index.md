---
title: Zabezpieczenia w programie .NET Framework
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .NET Framework, security
- security [.NET Framework], about security
- application development [.NET Framework], security
- security [.NET Framework]
ms.assetid: 9a9621d7-8883-4a4f-a874-65e8e09e20a6
caps.latest.revision: 37
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7f8600da624ff75ce2dbd5c417f886d6b3b1ac37
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="security-in-the-net-framework"></a><span data-ttu-id="4305c-102">Zabezpieczenia w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4305c-102">Security in the .NET Framework</span></span>
<span data-ttu-id="4305c-103">Środowisko uruchomieniowe języka wspólnego i .NET Framework oferują wiele klas przydatne i usług, które umożliwiają deweloperom łatwe napisać kod bezpiecznego i umożliwiają administratorom systemu dostosować uprawnienia przyznane do kodu, dzięki czemu aplikacja może uzyskiwać dostępu do chronionych zasobów.</span><span class="sxs-lookup"><span data-stu-id="4305c-103">The common language runtime and the .NET Framework provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="4305c-104">Ponadto środowisko uruchomieniowe i .NET Framework zapewnia przydatne klasy i usług, które ułatwiają korzystanie z kryptografii i opartej na rolach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4305c-104">In addition, the runtime and the .NET Framework provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4305c-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4305c-105">In This Section</span></span>  
 [<span data-ttu-id="4305c-106">Zmiany zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="4305c-106">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)  
 <span data-ttu-id="4305c-107">W tym artykule opisano ważne zmiany w systemie zabezpieczeń .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4305c-107">Describes important changes to the .NET Framework security system.</span></span>  
  
 [<span data-ttu-id="4305c-108">Główne pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="4305c-108">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="4305c-109">Zawiera omówienie wspólnego języka środowiska uruchomieniowego funkcje zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4305c-109">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="4305c-110">Ta sekcja ma znaczenie dla deweloperów i administratorów systemu.</span><span class="sxs-lookup"><span data-stu-id="4305c-110">This section is of interest to developers and system administrators.</span></span>  
  
 [<span data-ttu-id="4305c-111">Zabezpieczenia oparte na rolach</span><span class="sxs-lookup"><span data-stu-id="4305c-111">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)  
 <span data-ttu-id="4305c-112">Opisuje sposób interakcji z opartej na rolach zabezpieczeń w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4305c-112">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="4305c-113">Ta sekcja ma znaczenie dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="4305c-113">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="4305c-114">Model kryptografii</span><span class="sxs-lookup"><span data-stu-id="4305c-114">Cryptography Model</span></span>](../../../docs/standard/security/cryptography-model.md)  
 <span data-ttu-id="4305c-115">Zawiera omówienie usług kryptograficznych usług świadczonych przez program .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4305c-115">Provides an overview of cryptographic services provided by the .NET Framework.</span></span> <span data-ttu-id="4305c-116">Ta sekcja ma znaczenie dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="4305c-116">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="4305c-117">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="4305c-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="4305c-118">Opisano niektóre najważniejsze wskazówki dotyczące tworzenia niezawodnych aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4305c-118">Describes some of the best practices for creating reliable .NET Framework applications.</span></span> <span data-ttu-id="4305c-119">Ta sekcja ma znaczenie dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="4305c-119">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="4305c-120">Wytyczne dotyczące bezpiecznego programowania dla niezarządzanego kodu</span><span class="sxs-lookup"><span data-stu-id="4305c-120">Secure Coding Guidelines for Unmanaged Code</span></span>](../../../docs/framework/security/secure-coding-guidelines-for-unmanaged-code.md)  
 <span data-ttu-id="4305c-121">Wywoływanie kodu niezarządzanego, należy opisano niektóre z najlepszych rozwiązań i bezpieczeństwem.</span><span class="sxs-lookup"><span data-stu-id="4305c-121">Describes some of the best practices and security concerns when calling unmanaged code.</span></span>  
  
 [<span data-ttu-id="4305c-122">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="4305c-122">Windows Identity Foundation</span></span>](../../../docs/framework/security/index.md)  
 <span data-ttu-id="4305c-123">W tym artykule opisano, jak można zaimplementować tożsamości opartego na oświadczeniach w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="4305c-123">Describes how you can implement claims-based identity in your applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4305c-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="4305c-124">Related Sections</span></span>  
 [<span data-ttu-id="4305c-125">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="4305c-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="4305c-126">Przewodnik po wszystkich obszarach kluczowych technologii i zadaniach związanych z rozwojem aplikacji, takich jak tworzenie, konfigurowanie, debugowanie, zabezpieczanie i wdrażanie aplikacji, oraz informacje na temat programowania dynamicznego, interoperacyjności, rozszerzalności, zarządzania pamięcią i wątków.</span><span class="sxs-lookup"><span data-stu-id="4305c-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
