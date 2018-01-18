---
title: "Przegląd zabezpieczeń serwera SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a8f44b69f177584bb3680f68c50ff054c6b805ed
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="overview-of-sql-server-security"></a><span data-ttu-id="f67eb-102">Przegląd zabezpieczeń serwera SQL</span><span class="sxs-lookup"><span data-stu-id="f67eb-102">Overview of SQL Server Security</span></span>
<span data-ttu-id="f67eb-103">Strategii zabezpieczeń obrony z nakładającymi się warstwy zabezpieczeń, to najlepszy sposób na zagrożenia bezpieczeństwa licznika.</span><span class="sxs-lookup"><span data-stu-id="f67eb-103">A defense-in-depth strategy, with overlapping layers of security, is the best way to counter security threats.</span></span> <span data-ttu-id="f67eb-104">Program SQL Server stanowi architekturę zabezpieczeń, która umożliwia administratorów bazy danych i deweloperom tworzenie aplikacji w bezpiecznej bazie danych i licznik zagrożeń.</span><span class="sxs-lookup"><span data-stu-id="f67eb-104">SQL Server provides a security architecture that is designed to allow database administrators and developers to create secure database applications and counter threats.</span></span> <span data-ttu-id="f67eb-105">Każda wersja programu SQL Server została ulepszona w poprzednich wersjach programu SQL Server wraz z wprowadzeniem nowych funkcji i funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="f67eb-105">Each version of SQL Server has improved on previous versions of SQL Server with the introduction of new features and functionality.</span></span> <span data-ttu-id="f67eb-106">Zabezpieczeń nie jest dostarczany w polu.</span><span class="sxs-lookup"><span data-stu-id="f67eb-106">However, security does not ship in the box.</span></span> <span data-ttu-id="f67eb-107">Każda aplikacja jest unikatowa w jej wymagania dotyczące zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f67eb-107">Each application is unique in its security requirements.</span></span> <span data-ttu-id="f67eb-108">Deweloperzy muszą zrozumieć, która kombinacja funkcji i funkcji są najbardziej odpowiednie dla licznika znane zagrożenia i przewidywanie zagrożenia, które mogą pojawić się w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="f67eb-108">Developers need to understand which combination of features and functionality are most appropriate to counter known threats, and to anticipate threats that may arise in the future.</span></span>  
  
 <span data-ttu-id="f67eb-109">Wystąpienie programu SQL Server zawiera hierarchiczną kolekcję jednostek, począwszy od serwera.</span><span class="sxs-lookup"><span data-stu-id="f67eb-109">A SQL Server instance contains a hierarchical collection of entities, starting with the server.</span></span> <span data-ttu-id="f67eb-110">Każdy serwer zawiera wiele baz danych, a każda baza danych zawiera kolekcję obiektów możliwych do zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="f67eb-110">Each server contains multiple databases, and each database contains a collection of securable objects.</span></span> <span data-ttu-id="f67eb-111">Każdy serwer SQL zabezpieczanego jest skojarzony *uprawnienia* może zostać przydzielony do *główna*, która jest pojedyncza, grupa lub proces udzielony dostęp do programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f67eb-111">Every SQL Server securable has associated *permissions* that can be granted to a *principal*, which is an individual, group or process granted access to SQL Server.</span></span> <span data-ttu-id="f67eb-112">Mechanizm zabezpieczeń programu SQL Server zarządza dostępem do zabezpieczanych obiektów za pomocą *uwierzytelniania* i *autoryzacji*.</span><span class="sxs-lookup"><span data-stu-id="f67eb-112">The SQL Server security framework manages access to securable entities through *authentication* and *authorization*.</span></span>  
  
-   <span data-ttu-id="f67eb-113">Uwierzytelnianie to proces logowania do programu SQL Server za pomocą którego podmiot zabezpieczeń żąda dostępu poprzez przesłanie poświadczenia, które ocenia serwera.</span><span class="sxs-lookup"><span data-stu-id="f67eb-113">Authentication is the process of logging on to SQL Server by which a principal requests access by submitting credentials that the server evaluates.</span></span> <span data-ttu-id="f67eb-114">Uwierzytelniania ustalana jest tożsamość użytkownika lub inny proces jest uwierzytelniane.</span><span class="sxs-lookup"><span data-stu-id="f67eb-114">Authentication establishes the identity of the user or process being authenticated.</span></span>  
  
-   <span data-ttu-id="f67eb-115">Autoryzacja jest proces określania zabezpieczanego podmiot zabezpieczeń mogą uzyskiwać dostęp do zasobów i jakie operacje są dozwolone dla tych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f67eb-115">Authorization is the process of determining which securable resources a principal can access, and which operations are allowed for those resources.</span></span>  
  
 <span data-ttu-id="f67eb-116">Tematy w tej sekcji opisano podstawy zabezpieczeń programu SQL Server, tworzenia łączy do pełną dokumentację w odpowiednich wersji programu SQL Server — książki Online.</span><span class="sxs-lookup"><span data-stu-id="f67eb-116">The topics in this section cover SQL Server security fundamentals, providing links to the complete documentation in the relevant version of SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f67eb-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f67eb-117">In This Section</span></span>  
 [<span data-ttu-id="f67eb-118">Uwierzytelnianie w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="f67eb-118">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 <span data-ttu-id="f67eb-119">W tym artykule opisano logowania i uwierzytelniania programu SQL Server i zawiera łącza do dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f67eb-119">Describes logins and authentication in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="f67eb-120">Serwer i role bazy danych w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="f67eb-120">Server and Database Roles in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 <span data-ttu-id="f67eb-121">Przedstawiono stałe role serwera i bazy danych, role bazy danych niestandardowych i wbudowanych kont oraz zawiera łącza do dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f67eb-121">Describes fixed server and database roles, custom database roles, and built-in accounts and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="f67eb-122">Własność i oddzielenie schematu użytkownika w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="f67eb-122">Ownership and User-Schema Separation in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 <span data-ttu-id="f67eb-123">Zawiera opis separacji własności i użytkowników schematu obiektu i zawiera łącza do dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f67eb-123">Describes object ownership and  user-schema separation and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="f67eb-124">Autoryzacja i uprawnienia w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="f67eb-124">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 <span data-ttu-id="f67eb-125">Zawiera opis przyznawania uprawnień przy użyciu zasadą najniższych uprawnień i łącza do dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f67eb-125">Describes granting permissions using the principle of least privilege and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="f67eb-126">Szyfrowanie danych w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="f67eb-126">Data Encryption in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 <span data-ttu-id="f67eb-127">Zawiera opis opcji szyfrowania danych w programie SQL Server i zawiera łącza do dodatkowych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f67eb-127">Describes data encryption options in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="f67eb-128">Zabezpieczenia integracji CLR w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="f67eb-128">CLR Integration Security in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 <span data-ttu-id="f67eb-129">Zawiera linki do zasobów zabezpieczeń integracji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="f67eb-129">Provides links to CLR integration security resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f67eb-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f67eb-130">See Also</span></span>  
 [<span data-ttu-id="f67eb-131">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f67eb-131">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="f67eb-132">Zabezpieczenia serwera SQL</span><span class="sxs-lookup"><span data-stu-id="f67eb-132">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [<span data-ttu-id="f67eb-133">Scenariusze zabezpieczeń aplikacji w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="f67eb-133">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="f67eb-134">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="f67eb-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
