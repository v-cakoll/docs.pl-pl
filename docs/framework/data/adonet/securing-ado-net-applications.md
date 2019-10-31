---
title: Zabezpieczanie aplikacji ADO.NET
ms.date: 03/30/2017
ms.assetid: 005a1d43-6ee5-471e-ad98-1d30a44d49d5
ms.openlocfilehash: c99c56afca475caafe32cca3f50d074fb82e0e00
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196728"
---
# <a name="securing-adonet-applications"></a><span data-ttu-id="e382f-102">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e382f-102">Securing ADO.NET Applications</span></span>
<span data-ttu-id="e382f-103">Pisanie zabezpieczonej aplikacji ADO.NET obejmuje więcej niż uniknięcie wspólnego kodowania pułapek, takie jak nieweryfikowanie danych wejściowych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e382f-103">Writing a secure ADO.NET application involves more than avoiding common coding pitfalls such as not validating user input.</span></span> <span data-ttu-id="e382f-104">Aplikacja, która uzyskuje dostęp do danych, ma wiele potencjalnych punktów awarii, których atakujący może wykorzystać do pobierania, manipulowania lub niszczenia poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="e382f-104">An application that accesses data has many potential points of failure that an attacker can exploit to retrieve, manipulate, or destroy sensitive data.</span></span> <span data-ttu-id="e382f-105">W związku z tym ważne jest, aby zrozumieć wszystkie aspekty zabezpieczeń, od procesu modelowania zagrożeń podczas fazy projektowania aplikacji, do ostatecznego wdrożenia i trwającej konserwacji.</span><span class="sxs-lookup"><span data-stu-id="e382f-105">It is therefore important to understand all aspects of security, from the process of threat modeling during the design phase of your application, to its eventual deployment and ongoing maintenance.</span></span>  
  
 <span data-ttu-id="e382f-106">.NET Framework zawiera wiele przydatnych klas, usług i narzędzi do zabezpieczania i administrowania aplikacjami baz danych.</span><span class="sxs-lookup"><span data-stu-id="e382f-106">The .NET Framework provides many useful classes, services, and tools for securing and administering database applications.</span></span> <span data-ttu-id="e382f-107">Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia bezpieczne dla typów środowisko kodu do uruchamiania w programie, a zabezpieczenia dostępu kodu (CAS) ograniczają dalsze uprawnienia do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e382f-107">The common language runtime (CLR) provides a type-safe environment for code to run in, with code access security (CAS) to restrict further the permissions of managed code.</span></span> <span data-ttu-id="e382f-108">Zgodnie z bezpiecznymi praktykami kodowania dostępu do danych ograniczają szkody, które mogą zostać spowodowane przez potencjalną osobę atakującą.</span><span class="sxs-lookup"><span data-stu-id="e382f-108">Following secure data access coding practices limits the damage that can be inflicted by a potential attacker.</span></span>  
  
 <span data-ttu-id="e382f-109">Pisanie bezpiecznego kodu nie chroni przed atakami z użyciem niezarządzanych zasobów, takich jak bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e382f-109">Writing secure code does not guard against self-inflicted security holes when working with unmanaged resources such as databases.</span></span> <span data-ttu-id="e382f-110">Większość baz danych serwera, takich jak SQL Server, ma własne systemy zabezpieczeń, które zwiększają bezpieczeństwo po poprawnym wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="e382f-110">Most server databases, such as SQL Server, have their own security systems, which enhance security when implemented correctly.</span></span> <span data-ttu-id="e382f-111">Jednak nawet źródło danych z niezawodnym systemem zabezpieczeń może być ofiarą ataku, jeśli nie jest odpowiednio skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="e382f-111">However, even a data source with a robust security system can be victimized in an attack if it is not configured appropriately.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e382f-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e382f-112">In This Section</span></span>  
 [<span data-ttu-id="e382f-113">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e382f-113">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="e382f-114">Zawiera zalecenia dotyczące projektowania bezpiecznych aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="e382f-114">Provides recommendations for designing secure ADO.NET applications.</span></span>  
  
 [<span data-ttu-id="e382f-115">Bezpieczny dostęp do danych</span><span class="sxs-lookup"><span data-stu-id="e382f-115">Secure Data Access</span></span>](secure-data-access.md)  
 <span data-ttu-id="e382f-116">Opisuje sposób pracy z danymi z zabezpieczonego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="e382f-116">Describes how to work with data from a secured data source.</span></span>  
  
 [<span data-ttu-id="e382f-117">Zabezpieczanie aplikacje klienckich</span><span class="sxs-lookup"><span data-stu-id="e382f-117">Secure Client Applications</span></span>](secure-client-applications.md)  
 <span data-ttu-id="e382f-118">Opisuje zagadnienia dotyczące zabezpieczeń aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="e382f-118">Describes security considerations for client applications.</span></span>  
  
 [<span data-ttu-id="e382f-119">Zabezpieczenia dostępu kodu i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e382f-119">Code Access Security and ADO.NET</span></span>](code-access-security.md)  
 <span data-ttu-id="e382f-120">Opisuje, jak urzędy certyfikacji mogą chronić kod ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="e382f-120">Describes how CAS can help protect ADO.NET code.</span></span> <span data-ttu-id="e382f-121">Omówiono również sposób pracy z częściowym zaufaniem.</span><span class="sxs-lookup"><span data-stu-id="e382f-121">Also discusses how to work with partial trust.</span></span>  
  
 [<span data-ttu-id="e382f-122">Bezpieczeństwo danych i poufności informacji</span><span class="sxs-lookup"><span data-stu-id="e382f-122">Privacy and Data Security</span></span>](privacy-and-data-security.md)  
 <span data-ttu-id="e382f-123">Opisuje opcje szyfrowania dla aplikacji ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="e382f-123">Describes encryption options for ADO.NET applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e382f-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e382f-124">Related Sections</span></span>  
 [<span data-ttu-id="e382f-125">Zabezpieczenia serwera SQL</span><span class="sxs-lookup"><span data-stu-id="e382f-125">SQL Server Security</span></span>](./sql/sql-server-security.md)  
 <span data-ttu-id="e382f-126">Opisuje funkcje zabezpieczeń SQL Server z perspektywy dewelopera.</span><span class="sxs-lookup"><span data-stu-id="e382f-126">Describes SQL Server security features from a developer's perspective.</span></span>  
  
 [<span data-ttu-id="e382f-127">Zagadnienia dotyczące bezpieczeństwa</span><span class="sxs-lookup"><span data-stu-id="e382f-127">Security Considerations</span></span>](./ef/security-considerations.md)  
 <span data-ttu-id="e382f-128">Opisuje zabezpieczenia Entity Framework aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e382f-128">Describes security for Entity Framework applications.</span></span>  
  
 [<span data-ttu-id="e382f-129">Security</span><span class="sxs-lookup"><span data-stu-id="e382f-129">Security</span></span>](../../../standard/security/index.md)  
 <span data-ttu-id="e382f-130">Zawiera łącza do tematów opisujących wszystkie aspekty zabezpieczeń w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="e382f-130">Contains links to topics describing all aspects of security in .NET.</span></span>  
  
 <span data-ttu-id="e382f-131">[Narzędzia zabezpieczeń](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e382f-131">[Security Tools](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/7w3fd0wb(v=vs.90))</span></span>  
 <span data-ttu-id="e382f-132">.NET Framework narzędzia do zabezpieczania zasad zabezpieczeń i administrowania nimi.</span><span class="sxs-lookup"><span data-stu-id="e382f-132">.NET Framework tools for securing and administering security policy.</span></span>  
  
 <span data-ttu-id="e382f-133">[Zasoby do tworzenia bezpiecznych aplikacji](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e382f-133">[Resources for Creating Secure Applications](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165101(v=vs.100))</span></span>  
 <span data-ttu-id="e382f-134">Zawiera łącza do tematów dotyczących tworzenia bezpiecznych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e382f-134">Provides links to topics for creating secure applications.</span></span>  
  
 [<span data-ttu-id="e382f-135">Bibliografia dotycząca zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e382f-135">Security Bibliography</span></span>](/visualstudio/ide/securing-applications)  
 <span data-ttu-id="e382f-136">Oferuje linki do zasobów zewnętrznych dostępnych w trybie online i drukowania.</span><span class="sxs-lookup"><span data-stu-id="e382f-136">Provides links to external resources available online and in print.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e382f-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e382f-137">See also</span></span>

- [<span data-ttu-id="e382f-138">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e382f-138">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="e382f-139">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e382f-139">ADO.NET Overview</span></span>](ado-net-overview.md)
