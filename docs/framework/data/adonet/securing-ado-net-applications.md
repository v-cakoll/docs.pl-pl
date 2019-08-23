---
title: Zabezpieczanie aplikacji ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: d4c9c21f4d1f4a08ca6d676ee7b4c9e80709ba19
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963122"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="43f91-102">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="43f91-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="43f91-103">Pisanie zabezpieczonej aplikacji ADO.NET obejmuje więcej niż uniknięcie wspólnego kodowania pułapek, takie jak nieweryfikowanie danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="43f91-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="43f91-104">Aplikacja, która uzyskuje dostęp do danych, ma wiele potencjalnych punktów awarii, których atakujący może wykorzystać do pobierania, manipulowania lub niszczenia poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="43f91-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="43f91-105">W związku z tym ważne jest, aby zrozumieć wszystkie aspekty zabezpieczeń, od procesu modelowania zagrożeń podczas fazy projektowania aplikacji, do ostatecznego wdrożenia i trwającej konserwacji.</span><span class="sxs-lookup"><span data-stu-id="43f91-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="43f91-106">.NET Framework zawiera wiele przydatnych klas, usług i narzędzi do zabezpieczania i administrowania aplikacjami baz danych.</span><span class="sxs-lookup"><span data-stu-id="43f91-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="43f91-107">Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia bezpieczne dla typów środowisko kodu do uruchamiania w programie, a zabezpieczenia dostępu kodu (CAS) ograniczają dalsze uprawnienia do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="43f91-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="43f91-108">Zgodnie z bezpiecznymi praktykami kodowania dostępu do danych ograniczają szkody, które mogą zostać spowodowane przez potencjalną osobę atakującą.</span><span class="sxs-lookup"><span data-stu-id="43f91-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="43f91-109">Pisanie bezpiecznego kodu nie chroni przed atakami z użyciem niezarządzanych zasobów, takich jak bazy danych.</span><span class="sxs-lookup"><span data-stu-id="43f91-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="43f91-110">Większość baz danych serwera, takich jak SQL Server, ma własne systemy zabezpieczeń, które zwiększają bezpieczeństwo po poprawnym wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="43f91-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="43f91-111">Jednak nawet źródło danych z niezawodnym systemem zabezpieczeń może być ofiarą ataku, jeśli nie jest odpowiednio skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="43f91-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="43f91-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="43f91-112">In This Section</span></span>  
 [<span data-ttu-id="43f91-113">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="43f91-113">Security Overview</span></span>](../../../../docs/framework/data/adonet/security-overview.md)  
 <span data-ttu-id="43f91-114">Zawiera zalecenia dotyczące projektowania bezpiecznych aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="43f91-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="43f91-115">Bezpieczny dostęp do danych</span><span class="sxs-lookup"><span data-stu-id="43f91-115">Secure Data Access</span></span>](../../../../docs/framework/data/adonet/secure-data-access.md)  
 <span data-ttu-id="43f91-116">Opisuje sposób pracy z danymi z zabezpieczonego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="43f91-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="43f91-117">Zabezpieczanie aplikacje klienckich</span><span class="sxs-lookup"><span data-stu-id="43f91-117">Secure Client Applications</span></span>](../../../../docs/framework/data/adonet/secure-client-applications.md)  
 <span data-ttu-id="43f91-118">Opisuje zagadnienia dotyczące zabezpieczeń aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="43f91-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="43f91-119">Zabezpieczenia dostępu kodu i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="43f91-119">Code Access Security and ADO.NET</span></span>](../../../../docs/framework/data/adonet/code-access-security.md)  
 <span data-ttu-id="43f91-120">Opisuje, jak urzędy certyfikacji mogą chronić kod ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="43f91-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="43f91-121">Omówiono również sposób pracy z częściowym zaufaniem.</span><span class="sxs-lookup"><span data-stu-id="43f91-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="43f91-122">Bezpieczeństwo danych i poufności informacji</span><span class="sxs-lookup"><span data-stu-id="43f91-122">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 <span data-ttu-id="43f91-123">Opisuje opcje szyfrowania dla aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="43f91-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="43f91-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="43f91-124">Related Sections</span></span>  
 [<span data-ttu-id="43f91-125">Zabezpieczenia serwera SQL</span><span class="sxs-lookup"><span data-stu-id="43f91-125">SQL Server Security</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="43f91-126">Opisuje funkcje zabezpieczeń SQL Server z perspektywy dewelopera.</span><span class="sxs-lookup"><span data-stu-id="43f91-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="43f91-127">Zagadnienia dotyczące bezpieczeństwa</span><span class="sxs-lookup"><span data-stu-id="43f91-127">Security Considerations</span></span>](../../../../docs/framework/data/adonet/ef/security-considerations.md)  
 <span data-ttu-id="43f91-128">Opisuje zabezpieczenia Entity Framework aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43f91-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="43f91-129">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="43f91-129">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="43f91-130">Zawiera łącza do tematów opisujących wszystkie aspekty zabezpieczeń w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="43f91-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="43f91-131">[Narzędzia zabezpieczeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="43f91-131">[Security Tools](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="43f91-132">.NET Framework narzędzia do zabezpieczania zasad zabezpieczeń i administrowania nimi.</span><span class="sxs-lookup"><span data-stu-id="43f91-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="43f91-133">[Zasoby do tworzenia bezpiecznych aplikacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="43f91-133">[Resources for Creating Secure Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="43f91-134">Zawiera łącza do tematów dotyczących tworzenia bezpiecznych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="43f91-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="43f91-135">Bibliografia dotycząca zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="43f91-135">Security Bibliography</span></span>](/visualstudio/ide/security-bibliography)  
 <span data-ttu-id="43f91-136">Oferuje linki do zasobów zewnętrznych dostępnych w trybie online i drukowania.</span><span class="sxs-lookup"><span data-stu-id="43f91-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f91-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43f91-137">See also</span></span>

- [<span data-ttu-id="43f91-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="43f91-138">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="43f91-139">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="43f91-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
