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
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728592"
---
# <a name="security-in-net"></a><span data-ttu-id="ef055-102">Zabezpieczenia w .NET</span><span class="sxs-lookup"><span data-stu-id="ef055-102">Security in .NET</span></span>
<span data-ttu-id="ef055-103">Środowisko uruchomieniowe języka wspólnego i .NET zapewniają wiele klas przydatne i usług, które umożliwiają deweloperom łatwe napisać kod bezpiecznego i umożliwiają administratorom systemu dostosować uprawnienia przyznane do kodu, dzięki czemu aplikacja może uzyskiwać dostępu do chronionych zasobów.</span><span class="sxs-lookup"><span data-stu-id="ef055-103">The common language runtime and the .NET provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="ef055-104">Środowisko uruchomieniowe i .NET zapewniają dodatkowo przydatne klasy i usług, które ułatwiają korzystanie z kryptografii i opartej na rolach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ef055-104">In addition, the runtime and the .NET provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef055-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ef055-105">In This Section</span></span>  

 [<span data-ttu-id="ef055-106">Główne pojęcia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ef055-106">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="ef055-107">Zawiera omówienie wspólnego języka środowiska uruchomieniowego funkcje zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ef055-107">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="ef055-108">Ta sekcja ma znaczenie dla deweloperów i administratorów systemu.</span><span class="sxs-lookup"><span data-stu-id="ef055-108">This section is of interest to developers and system administrators.</span></span>  
  
 [<span data-ttu-id="ef055-109">Zabezpieczenia oparte na rolach</span><span class="sxs-lookup"><span data-stu-id="ef055-109">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)  
 <span data-ttu-id="ef055-110">Opisuje sposób interakcji z opartej na rolach zabezpieczeń w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ef055-110">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="ef055-111">Ta sekcja ma znaczenie dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="ef055-111">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="ef055-112">Model kryptografii</span><span class="sxs-lookup"><span data-stu-id="ef055-112">Cryptography Model</span></span>](../../../docs/standard/security/cryptography-model.md)  
 <span data-ttu-id="ef055-113">Zawiera omówienie usług kryptograficznych programu .NET.</span><span class="sxs-lookup"><span data-stu-id="ef055-113">Provides an overview of cryptographic services provided by .NET.</span></span> <span data-ttu-id="ef055-114">Ta sekcja ma znaczenie dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="ef055-114">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="ef055-115">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="ef055-115">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="ef055-116">Opisano niektóre najważniejsze wskazówki dotyczące tworzenia niezawodnych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="ef055-116">Describes some of the best practices for creating reliable .NET applications.</span></span> <span data-ttu-id="ef055-117">Ta sekcja ma znaczenie dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="ef055-117">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="ef055-118">Wytyczne dotyczące bezpiecznego programowania dla niezarządzanego kodu</span><span class="sxs-lookup"><span data-stu-id="ef055-118">Secure Coding Guidelines for Unmanaged Code</span></span>](../../../docs/framework/security/secure-coding-guidelines-for-unmanaged-code.md)  
 <span data-ttu-id="ef055-119">Wywoływanie kodu niezarządzanego, należy opisano niektóre z najlepszych rozwiązań i bezpieczeństwem.</span><span class="sxs-lookup"><span data-stu-id="ef055-119">Describes some of the best practices and security concerns when calling unmanaged code.</span></span>  
  
 [<span data-ttu-id="ef055-120">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="ef055-120">Windows Identity Foundation</span></span>](../../../docs/framework/security/index.md)  
 <span data-ttu-id="ef055-121">W tym artykule opisano, jak można zaimplementować tożsamości opartego na oświadczeniach w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="ef055-121">Describes how you can implement claims-based identity in your applications.</span></span>  

<span data-ttu-id="ef055-122">[Zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md) opisano ważne zmiany zabezpieczeń systemu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef055-122">[Security Changes](../../../docs/framework/security/security-changes.md) Describes important changes to the .NET Framework security system.</span></span>

## <a name="related-sections"></a><span data-ttu-id="ef055-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ef055-123">Related Sections</span></span>  
 [<span data-ttu-id="ef055-124">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="ef055-124">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="ef055-125">Przewodnik po wszystkich obszarach kluczowych technologii i zadaniach związanych z rozwojem aplikacji, takich jak tworzenie, konfigurowanie, debugowanie, zabezpieczanie i wdrażanie aplikacji, oraz informacje na temat programowania dynamicznego, interoperacyjności, rozszerzalności, zarządzania pamięcią i wątków.</span><span class="sxs-lookup"><span data-stu-id="ef055-125">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
