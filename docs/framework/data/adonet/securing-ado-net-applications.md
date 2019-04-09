---
title: Zabezpieczanie aplikacji ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: 32d3de15242aaf9cfacd9371289a5a0a675f884b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149386"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="2cb4c-102">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2cb4c-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="2cb4c-103">Zapisywanie bezpiecznych aplikacji ADO.NET obejmuje więcej niż unikanie typowych pułapek kodowania, takie jak nie sprawdzania poprawności danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="2cb4c-104">Aplikacja, która uzyskuje dostęp do danych ma wiele potencjalnych punktów awarii, które osoba atakująca może wykorzystać do pobrania, manipulowanie lub zniszczyć poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="2cb4c-105">W związku z tym ważne jest zrozumienie wszystkie aspekty zabezpieczeń z procesu w fazie projektowania aplikacji, jego ostatecznej wdrażania i konserwacji do modelowania zagrożeń.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="2cb4c-106">.NET Framework zawiera wiele klas użyteczne, usług i narzędzi do zabezpieczania i administrowania nim aplikacji baz danych.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="2cb4c-107">Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia środowisko bezpieczny dla kodu do uruchomienia, za pomocą zabezpieczeń dostępu kodu (CAS), aby dodatkowo ograniczyć uprawnienia kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="2cb4c-108">Po zabezpieczonych danych access kodowania ogranicza uszkodzeń, które mogą być spowodowane potencjalnym osobom atakującym.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="2cb4c-109">Pisanie bezpiecznego kodu nie zabezpieczyć się przed luk w zabezpieczeniach samodzielnie sprowokowane podczas pracy z niezarządzanych zasobów, takich jak bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="2cb4c-110">Serwer baz danych, takich jak SQL Server mają własne systemy zabezpieczeń, które zwiększyć poziom bezpieczeństwa w przypadku zaimplementowania poprawnie.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="2cb4c-111">Jednak nawet źródła danych w systemie zabezpieczeń można zaatakowany w przypadku ataków, jeśli nie został prawidłowo skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2cb4c-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2cb4c-112">In This Section</span></span>  
 [<span data-ttu-id="2cb4c-113">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2cb4c-113">Security Overview</span></span>](../../../../docs/framework/data/adonet/security-overview.md)  
 <span data-ttu-id="2cb4c-114">Zawiera zalecenia dotyczące projektowania bezpiecznych aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="2cb4c-115">Bezpieczny dostęp do danych</span><span class="sxs-lookup"><span data-stu-id="2cb4c-115">Secure Data Access</span></span>](../../../../docs/framework/data/adonet/secure-data-access.md)  
 <span data-ttu-id="2cb4c-116">W tym artykule opisano sposób pracy z danymi ze źródła zabezpieczonych danych.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="2cb4c-117">Zabezpieczanie aplikacji klienckich</span><span class="sxs-lookup"><span data-stu-id="2cb4c-117">Secure Client Applications</span></span>](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 <span data-ttu-id="2cb4c-118">W tym artykule opisano zagadnienia dotyczące zabezpieczeń dla aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="2cb4c-119">Zabezpieczenia dostępu kodu i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2cb4c-119">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="2cb4c-120">W tym artykule opisano, jak urzędy certyfikacji mogą chronić kodu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="2cb4c-121">Omówiono również sposób pracy z częściowej relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="2cb4c-122">Bezpieczeństwo danych i poufności informacji</span><span class="sxs-lookup"><span data-stu-id="2cb4c-122">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 <span data-ttu-id="2cb4c-123">W tym artykule opisano opcje szyfrowania dla aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2cb4c-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2cb4c-124">Related Sections</span></span>  
 [<span data-ttu-id="2cb4c-125">Zabezpieczenia serwera SQL</span><span class="sxs-lookup"><span data-stu-id="2cb4c-125">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="2cb4c-126">W tym artykule opisano funkcje zabezpieczeń programu SQL Server z perspektywy dewelopera.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="2cb4c-127">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2cb4c-127">Security Considerations</span></span>](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 <span data-ttu-id="2cb4c-128">W tym artykule opisano zabezpieczenia dla aplikacji platformy Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="2cb4c-129">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="2cb4c-129">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="2cb4c-130">Zawiera łącza do tematów opisujących wszystkie aspekty zabezpieczeń na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 [<span data-ttu-id="2cb4c-131">Narzędzia zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2cb4c-131">Security Tools</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))  
 <span data-ttu-id="2cb4c-132">Narzędzia programu .NET framework do zabezpieczania i administrowania zasadami zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 [<span data-ttu-id="2cb4c-133">Zasoby służące do tworzenia bezpiecznych aplikacji</span><span class="sxs-lookup"><span data-stu-id="2cb4c-133">Resources for Creating Secure Applications</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))  
 <span data-ttu-id="2cb4c-134">Zawiera łącza do tematów dotyczące tworzenia bezpiecznych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="2cb4c-135">Bibliografia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2cb4c-135">Security Bibliography</span></span>](/visualstudio/ide/security-bibliography)  
 <span data-ttu-id="2cb4c-136">Zawiera łącza do zasobów zewnętrznych, które są dostępne w tryb online i drukowania.</span><span class="sxs-lookup"><span data-stu-id="2cb4c-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb4c-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2cb4c-137">See also</span></span>

- [<span data-ttu-id="2cb4c-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2cb4c-138">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="2cb4c-139">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="2cb4c-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
