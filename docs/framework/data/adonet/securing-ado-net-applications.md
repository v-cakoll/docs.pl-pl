---
title: Zabezpieczanie aplikacji ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 75d78c505c81ce688e0ba0110c76712c71db1c4f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="f7911-102">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f7911-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="f7911-103">Pisanie zabezpieczonej aplikacji ADO.NET obejmuje więcej niż unikanie wspólnej kodowania problemów, takich jak nie Walidacja danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f7911-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="f7911-104">Aplikacja, która uzyskuje dostęp do danych ma wiele punktów potencjalnych awarii, które osoba atakująca może wykorzystać do pobrania, manipulowania lub zniszczenie poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="f7911-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="f7911-105">W związku z tym ważne jest zrozumienie wszystkie aspekty zabezpieczeń w procesie modelowania w fazie projektowania aplikacji, w celu jego ostatecznego wdrażaniem i konserwacją bieżących zagrożeń.</span><span class="sxs-lookup"><span data-stu-id="f7911-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="f7911-106">.NET Framework zapewnia wiele klas przydatne, usług i narzędzi do zabezpieczania i administrowania nim aplikacje baz danych.</span><span class="sxs-lookup"><span data-stu-id="f7911-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="f7911-107">Środowisko uruchomieniowe języka wspólnego (CLR) udostępnia środowisko bezpieczne dla kodu do uruchomienia, z zabezpieczeń dostępu kodu (CAS) dodatkowo ograniczyć uprawnienia kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f7911-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="f7911-108">Następujące zabezpieczonych danych access praktyk kodowania ogranicza uszkodzeń, które mogą być spowodowane potencjalnym osobom atakującym.</span><span class="sxs-lookup"><span data-stu-id="f7911-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="f7911-109">Pisanie kodu bezpiecznego nie chronią przed luk w zabezpieczeniach sam, podczas pracy z niezarządzane zasoby, takie jak bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f7911-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="f7911-110">Serwer baz danych, takich jak SQL Server ma swoje własne systemy zabezpieczeń, które zwiększenia poziomu bezpieczeństwa, implementując poprawnie.</span><span class="sxs-lookup"><span data-stu-id="f7911-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="f7911-111">Jednak nawet źródła danych przy użyciu systemu skuteczną ochronę można zaatakowany w przypadku ataków, jeśli nie został prawidłowo skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="f7911-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7911-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f7911-112">In This Section</span></span>  
 [<span data-ttu-id="f7911-113">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="f7911-113">Security Overview</span></span>](../../../../docs/framework/data/adonet/security-overview.md)  
 <span data-ttu-id="f7911-114">Zawiera zalecenia dotyczące projektowania bezpiecznych aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f7911-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="f7911-115">Bezpieczny dostęp do danych</span><span class="sxs-lookup"><span data-stu-id="f7911-115">Secure Data Access</span></span>](../../../../docs/framework/data/adonet/secure-data-access.md)  
 <span data-ttu-id="f7911-116">Opisuje sposób pracy z danymi ze źródła zabezpieczonych danych.</span><span class="sxs-lookup"><span data-stu-id="f7911-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="f7911-117">Zabezpieczanie aplikacje klienckich</span><span class="sxs-lookup"><span data-stu-id="f7911-117">Secure Client Applications</span></span>](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 <span data-ttu-id="f7911-118">W tym artykule opisano zagadnienia dotyczące zabezpieczeń dla aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="f7911-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="f7911-119">Zabezpieczenia dostępu kodu i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f7911-119">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="f7911-120">W tym artykule opisano, jak urzędy certyfikacji mogą pomóc chronić ADO.NET kodu.</span><span class="sxs-lookup"><span data-stu-id="f7911-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="f7911-121">Omówiono także sposób pracy z częściowa relacja zaufania.</span><span class="sxs-lookup"><span data-stu-id="f7911-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="f7911-122">Bezpieczeństwo danych i poufności informacji</span><span class="sxs-lookup"><span data-stu-id="f7911-122">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 <span data-ttu-id="f7911-123">Opisuje opcje szyfrowania dla aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f7911-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f7911-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="f7911-124">Related Sections</span></span>  
 [<span data-ttu-id="f7911-125">Zabezpieczenia serwera SQL</span><span class="sxs-lookup"><span data-stu-id="f7911-125">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="f7911-126">Opisuje funkcje zabezpieczeń programu SQL Server z punktu widzenia dewelopera.</span><span class="sxs-lookup"><span data-stu-id="f7911-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="f7911-127">Zagadnienia dotyczące bezpieczeństwa</span><span class="sxs-lookup"><span data-stu-id="f7911-127">Security Considerations</span></span>](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 <span data-ttu-id="f7911-128">W tym artykule opisano zabezpieczenia dla aplikacji programu Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="f7911-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="f7911-129">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="f7911-129">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="f7911-130">Zawiera łącza do tematów opisujących wszystkie aspekty zabezpieczeń w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7911-130">Contains links to topics describing all aspects of security in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="f7911-131">Narzędzia zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="f7911-131">Security Tools</span></span>](http://msdn.microsoft.com/library/2a3eb98a-2de6-4fba-b41c-01a74d354c11)  
 <span data-ttu-id="f7911-132">Narzędzia .NET framework do zabezpieczania i administrowanie zasadami zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f7911-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 [<span data-ttu-id="f7911-133">Zasoby służące do tworzenia bezpiecznych aplikacji</span><span class="sxs-lookup"><span data-stu-id="f7911-133">Resources for Creating Secure Applications</span></span>](http://msdn.microsoft.com/library/0ebf5f69-76f2-498a-a2df-83cf3443e132)  
 <span data-ttu-id="f7911-134">Zawiera łącza do tematów do tworzenia bezpiecznego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7911-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="f7911-135">Bibliografia dotycząca zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="f7911-135">Security Bibliography</span></span>](/visualstudio/ide/security-bibliography)  
 <span data-ttu-id="f7911-136">Zawiera linki do zasobów zewnętrznych dostępna online i drukowania.</span><span class="sxs-lookup"><span data-stu-id="f7911-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7911-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7911-137">See Also</span></span>  
 [<span data-ttu-id="f7911-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f7911-138">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="f7911-139">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="f7911-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
