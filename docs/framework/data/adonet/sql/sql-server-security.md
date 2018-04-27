---
title: Zabezpieczenia serwera SQL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: eb9eb073eb2227ce98d4adb93b8f4b60575cf1b7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="sql-server-security"></a><span data-ttu-id="cc691-102">Zabezpieczenia serwera SQL</span><span class="sxs-lookup"><span data-stu-id="cc691-102">SQL Server Security</span></span>
<span data-ttu-id="cc691-103">Program SQL Server ma wiele funkcji, które obsługują tworzenie bezpiecznej bazie danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cc691-103">SQL Server has many features that support creating secure database applications.</span></span>  
  
 <span data-ttu-id="cc691-104">Typowe kwestie dotyczące zabezpieczeń, takich jak dane przed kradzieżą lub vandalism, zastosuj niezależnie od wersji programu SQL Server są używane.</span><span class="sxs-lookup"><span data-stu-id="cc691-104">Common security considerations, such as data theft or vandalism, apply regardless of the version of SQL Server you are using.</span></span> <span data-ttu-id="cc691-105">Integralność danych, należy również uwzględnić jako problem z zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="cc691-105">Data integrity should also be considered as a security issue.</span></span> <span data-ttu-id="cc691-106">Jeśli dane nie są chronione, istnieje możliwość, że może stać się Optymalizacja manipulowania danymi ad hoc jest dozwolone, a dane są przypadkowego lub umyślnego modyfikacji z nieprawidłowymi wartościami lub całkowicie usunięte.</span><span class="sxs-lookup"><span data-stu-id="cc691-106">If data is not protected, it is possible that it could become worthless if ad hoc data manipulation is permitted and the data is inadvertently or maliciously modified with incorrect values or deleted entirely.</span></span> <span data-ttu-id="cc691-107">Ponadto istnieją często wymagań prawnych, które należy przestrzegać, takie jak poprawny magazyn informacji poufnych.</span><span class="sxs-lookup"><span data-stu-id="cc691-107">In addition, there are often legal requirements that must be adhered to, such as the correct storage of confidential information.</span></span> <span data-ttu-id="cc691-108">Przechowywanie niektóre rodzaje danych osobowych jest proscribed całkowicie, w zależności od prawa, które są stosowane w określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="cc691-108">Storing some kinds of personal data is proscribed entirely, depending on the laws that apply in a particular jurisdiction.</span></span>  
  
 <span data-ttu-id="cc691-109">Każda wersja programu SQL Server ma funkcje zabezpieczeń, tak jak w przypadku każdej wersji systemu Windows, w nowszych wersjach o rozszerzoną funkcjonalność przez wcześniejsze.</span><span class="sxs-lookup"><span data-stu-id="cc691-109">Each version of SQL Server has different security features, as does each version of Windows, with later versions having enhanced functionality over earlier ones.</span></span> <span data-ttu-id="cc691-110">Należy zrozumieć, że tylko funkcje zabezpieczeń nie może zagwarantować aplikacji bezpiecznej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="cc691-110">It is important to understand that security features alone cannot guarantee a secure database application.</span></span> <span data-ttu-id="cc691-111">Każda aplikacja bazy danych jest unikatowa w wymagania, środowiska wykonawczego, model wdrażania, lokalizacji fizycznej i użytkowników.</span><span class="sxs-lookup"><span data-stu-id="cc691-111">Each database application is unique in its requirements, execution environment, deployment model, physical location, and user population.</span></span> <span data-ttu-id="cc691-112">Niektóre aplikacje, które znajdują się lokalnie w zakresie może być konieczne jedynie minimalne zabezpieczenia inne aplikacje lokalne lub aplikacje wdrożone za pośrednictwem Internetu, mogą wymagać środków bezpieczeństwa oraz ciągłego monitorowania i oceny.</span><span class="sxs-lookup"><span data-stu-id="cc691-112">Some applications that are local in scope may need only minimal security whereas other local applications or applications deployed over the Internet may require stringent security measures and ongoing monitoring and evaluation.</span></span>  
  
 <span data-ttu-id="cc691-113">W czasie projektowania, a nie jako zbagatelizowane należy rozważyć wymagania dotyczące zabezpieczeń aplikacji bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cc691-113">The security requirements of a SQL Server database application should be considered at design time, not as an afterthought.</span></span> <span data-ttu-id="cc691-114">Oceny zagrożeń wczesnym etapie cyklu programowanie daje możliwość ograniczyć potencjalne szkody wszędzie tam, gdzie zostanie wykryte zagrożenie.</span><span class="sxs-lookup"><span data-stu-id="cc691-114">Evaluating threats early in the development cycle gives you the opportunity to mitigate potential damage wherever a vulnerability is detected.</span></span>  
  
 <span data-ttu-id="cc691-115">Nawet w przypadku początkowego projektu aplikacji dźwięku, w miarę rozwoju środowisko systemu mogą pojawić się nowych zagrożeń.</span><span class="sxs-lookup"><span data-stu-id="cc691-115">Even if the initial design of an application is sound, new threats may emerge as the system evolves.</span></span> <span data-ttu-id="cc691-116">Dzięki tworzeniu wielu linii obrony wokół bazy danych, można zminimalizować szkody spowodowane naruszenia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="cc691-116">By creating multiple lines of defense around your database, you can minimize the damage inflicted by a security breach.</span></span> <span data-ttu-id="cc691-117">Pierwszą linię obrony jest zmniejszenie powierzchni ataku przez nigdy, do udzielania więcej uprawnień niż jest to bezwzględnie konieczne.</span><span class="sxs-lookup"><span data-stu-id="cc691-117">Your first line of defense is to reduce the attack surface area by never to granting more permissions than are absolutely necessary.</span></span>  
  
 <span data-ttu-id="cc691-118">W tematach w tej sekcji opisano krótko funkcji zabezpieczeń w programie SQL Server, które są istotne dla deweloperów, linki do powiązanych tematów w dokumentacji SQL Server — książki Online i innych zasobów, które zapewniają szczegółowe pokrycie.</span><span class="sxs-lookup"><span data-stu-id="cc691-118">The topics in this section briefly describe the security features in SQL Server that are relevant for developers, with links to relevant topics in SQL Server Books Online and other resources that provide more detailed coverage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc691-119">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cc691-119">In This Section</span></span>  
 [<span data-ttu-id="cc691-120">Przegląd zabezpieczeń serwera SQL</span><span class="sxs-lookup"><span data-stu-id="cc691-120">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 <span data-ttu-id="cc691-121">Zawiera opis funkcji architekturze i zabezpieczeniach programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cc691-121">Describes the architecture and security features of SQL Server.</span></span>  
  
 [<span data-ttu-id="cc691-122">Scenariusze zabezpieczeń aplikacji w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="cc691-122">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 <span data-ttu-id="cc691-123">Zawiera tematy dyskutować różne scenariusze zabezpieczeń aplikacji dla aplikacji ADO.NET i SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cc691-123">Contains topics discussing various application security scenarios for ADO.NET and SQL Server applications.</span></span>  
  
 [<span data-ttu-id="cc691-124">Bezpieczeństwo programu SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="cc691-124">SQL Server Express Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-express-security.md)  
 <span data-ttu-id="cc691-125">W tym artykule opisano zagadnienia dotyczące zabezpieczeń programu SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="cc691-125">Describes security considerations for SQL Server Express.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cc691-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="cc691-126">Related Sections</span></span>  
[<span data-ttu-id="cc691-127">Centrum zabezpieczeń dla aparatu bazy danych programu SQL Server i bazy danych Azure SQL</span><span class="sxs-lookup"><span data-stu-id="cc691-127">Security Center for SQL Server Database Engine and Azure SQL Database</span></span>](/sql/relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database)  
<span data-ttu-id="cc691-128">W tym artykule opisano zagadnienia dotyczące zabezpieczeń programu SQL Server i bazy danych SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="cc691-128">Describes security considerations for SQL Server and Azure SQL Database.</span></span>

[<span data-ttu-id="cc691-129">Zagadnienia dotyczące zabezpieczeń dla instalacji serwera SQL</span><span class="sxs-lookup"><span data-stu-id="cc691-129">Security Considerations for a SQL Server Installation</span></span>](/sql/sql-server/install/security-considerations-for-a-sql-server-installation)  
<span data-ttu-id="cc691-130">W tym artykule opisano zagadnienia dotyczące zabezpieczeń, które należy uwzględnić przed zainstalowaniem programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cc691-130">Describes security concerns to consider before installing SQL Server.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc691-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc691-131">See Also</span></span>  
 [<span data-ttu-id="cc691-132">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cc691-132">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="cc691-133">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cc691-133">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
