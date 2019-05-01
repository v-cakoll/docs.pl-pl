---
title: Zabezpieczenia w .NET
ms.date: 06/04/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, security
- security [.NET], about security
- application development [.NET], security
- security [.NET Framework]
- security [.NET]
ms.assetid: 9a9621d7-8883-4a4f-a874-65e8e09e20a6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e60f463d5a691cb84a30c169e471aa905b2db17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61860558"
---
# <a name="security-in-net"></a><span data-ttu-id="69b73-102">Zabezpieczenia w .NET</span><span class="sxs-lookup"><span data-stu-id="69b73-102">Security in .NET</span></span>
<span data-ttu-id="69b73-103">Środowisko uruchomieniowe języka wspólnego i platformy .NET zawierają wiele klas przydatne i usług, które umożliwiają deweloperom łatwe pisać bezpieczny kod i umożliwiają administratorom systemu dostosować uprawnienia udzielone do kodu, dzięki czemu mogą uzyskać dostęp zasobów chronionych.</span><span class="sxs-lookup"><span data-stu-id="69b73-103">The common language runtime and the .NET provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="69b73-104">Ponadto środowisko uruchomieniowe i platformy .NET zawierają przydatne klasach i usługach, które ułatwiają korzystanie z kryptografią i opartej na rolach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="69b73-104">In addition, the runtime and the .NET provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69b73-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="69b73-105">In This Section</span></span>  

 [<span data-ttu-id="69b73-106">Główne pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="69b73-106">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="69b73-107">Zawiera omówienie języka wspólnego, funkcje zabezpieczeń środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="69b73-107">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="69b73-108">Ta sekcja ma znaczenie dla deweloperów i administratorów systemu.</span><span class="sxs-lookup"><span data-stu-id="69b73-108">This section is of interest to developers and system administrators.</span></span>  
  
 [<span data-ttu-id="69b73-109">Zabezpieczenia oparte na rolach</span><span class="sxs-lookup"><span data-stu-id="69b73-109">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)  
 <span data-ttu-id="69b73-110">W tym artykule opisano, jak korzystać z zabezpieczeń opartych na rolach w kodzie.</span><span class="sxs-lookup"><span data-stu-id="69b73-110">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="69b73-111">Ta sekcja ma znaczenie dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="69b73-111">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="69b73-112">Model kryptografii</span><span class="sxs-lookup"><span data-stu-id="69b73-112">Cryptography Model</span></span>](../../../docs/standard/security/cryptography-model.md)  
 <span data-ttu-id="69b73-113">Zawiera omówienie usług kryptograficznych programu .NET.</span><span class="sxs-lookup"><span data-stu-id="69b73-113">Provides an overview of cryptographic services provided by .NET.</span></span> <span data-ttu-id="69b73-114">Ta sekcja ma znaczenie dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="69b73-114">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="69b73-115">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="69b73-115">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="69b73-116">Opisuje niektóre najlepsze rozwiązania dotyczące tworzenia niezawodnych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="69b73-116">Describes some of the best practices for creating reliable .NET applications.</span></span> <span data-ttu-id="69b73-117">Ta sekcja ma znaczenie dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="69b73-117">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="69b73-118">Wytyczne dotyczące bezpiecznego programowania dla niezarządzanego kodu</span><span class="sxs-lookup"><span data-stu-id="69b73-118">Secure Coding Guidelines for Unmanaged Code</span></span>](../../../docs/framework/security/secure-coding-guidelines-for-unmanaged-code.md)  
 <span data-ttu-id="69b73-119">W tym artykule opisano niektóre najlepsze rozwiązania i problemy dotyczące zabezpieczeń podczas wywoływania niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="69b73-119">Describes some of the best practices and security concerns when calling unmanaged code.</span></span>  
  
 [<span data-ttu-id="69b73-120">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="69b73-120">Windows Identity Foundation</span></span>](../../../docs/framework/security/index.md)  
 <span data-ttu-id="69b73-121">W tym artykule opisano, jak można zaimplementować tożsamości opartej na oświadczeniach w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="69b73-121">Describes how you can implement claims-based identity in your applications.</span></span>  

<span data-ttu-id="69b73-122">[Zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md) opisano istotne zmiany w systemie zabezpieczeń .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69b73-122">[Security Changes](../../../docs/framework/security/security-changes.md) Describes important changes to the .NET Framework security system.</span></span>

## <a name="related-sections"></a><span data-ttu-id="69b73-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="69b73-123">Related Sections</span></span>  
 [<span data-ttu-id="69b73-124">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="69b73-124">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="69b73-125">Przewodnik po wszystkich obszarach kluczowych technologii i zadaniach związanych z rozwojem aplikacji, takich jak tworzenie, konfigurowanie, debugowanie, zabezpieczanie i wdrażanie aplikacji, oraz informacje na temat programowania dynamicznego, interoperacyjności, rozszerzalności, zarządzania pamięcią i wątków.</span><span class="sxs-lookup"><span data-stu-id="69b73-125">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
