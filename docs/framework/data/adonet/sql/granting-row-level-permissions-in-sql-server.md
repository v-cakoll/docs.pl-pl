---
title: "Udzielanie uprawnień na poziomie wiersza w programie SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c086ad08e4170d0033ae32bd730b239d5541d541
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="ca37e-102">Udzielanie uprawnień na poziomie wiersza w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="ca37e-102">Granting Row-Level Permissions in SQL Server</span></span>
<span data-ttu-id="ca37e-103">W niektórych scenariuszach jest wymagane do kontrolowania dostępu do danych na bardziej szczegółowym poziomie niż zapewnia jakie po prostu udzielanie, odwoływanie lub odmawianie uprawnień.</span><span class="sxs-lookup"><span data-stu-id="ca37e-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="ca37e-104">Na przykład szpital Twoich aplikacji bazy danych mogą wymagać poszczególnych lekarzy ograniczona do uzyskiwania dostępu do informacji dotyczących tylko ich pacjentów.</span><span class="sxs-lookup"><span data-stu-id="ca37e-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="ca37e-105">Podobne wymagania istnieje w wielu środowiskach, w tym finance, prawa dla instytucji rządowych i godzina aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ca37e-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="ca37e-106">Aby pomóc w pokonywaniu tych scenariuszy, SQL Server 2016 zapewnia [zabezpieczenia na poziomie wiersza](https://msdn.microsoft.com/library/dn765131.aspx) funkcja, która upraszcza i centralizuje logiki dostęp na poziomie wiersza w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ca37e-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](https://msdn.microsoft.com/library/dn765131.aspx) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="ca37e-107">W przypadku wcześniejszych wersji programu SQL Server podobne funkcje można osiągnąć za pomocą widoków wprowadzenie filtrowanie na poziomie wiersza.</span><span class="sxs-lookup"><span data-stu-id="ca37e-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>  
  
## <a name="implementing-row-level-filtering"></a><span data-ttu-id="ca37e-108">Implementowanie filtrowanie na poziomie wiersza</span><span class="sxs-lookup"><span data-stu-id="ca37e-108">Implementing Row-level Filtering</span></span>  
 <span data-ttu-id="ca37e-109">Filtrowanie na poziomie wiersza jest używany do przechowywania informacji w jednej tabeli podobnie jak w powyższym przykładzie szpital Twoich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ca37e-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="ca37e-110">Aby zaimplementować filtrowania każdy wiersz na poziomie wiersza ma kolumny, która definiuje różnego parametrów, takich jak nazwa użytkownika, etykiety lub innego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="ca37e-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="ca37e-111">Można tworzyć zasady zabezpieczeń lub widok w tabeli, które filtry wierszy, na które użytkownik ma dostęp.</span><span class="sxs-lookup"><span data-stu-id="ca37e-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="ca37e-112">Następnie można utworzyć sparametryzowany procedur składowanych, które kontrolują typy zapytań, które użytkownik może uruchomić.</span><span class="sxs-lookup"><span data-stu-id="ca37e-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>  
  
 <span data-ttu-id="ca37e-113">Na poniższym przykładzie opisano, jak skonfigurować filtrowanie na podstawie nazwy użytkownika lub nazwy logowania na poziomie wiersza:</span><span class="sxs-lookup"><span data-stu-id="ca37e-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>  
  
-   <span data-ttu-id="ca37e-114">Utwórz tabelę, dodać kolumnę do przechowywania nazwy.</span><span class="sxs-lookup"><span data-stu-id="ca37e-114">Create the table, adding a column to store the name.</span></span>  
  
-   <span data-ttu-id="ca37e-115">Włącz filtrowanie na poziomie wiersza:</span><span class="sxs-lookup"><span data-stu-id="ca37e-115">Enable row-level filtering:</span></span>  
  
    -   <span data-ttu-id="ca37e-116">Jeśli używasz programu SQL Server 2016 lub nowszego, lub [bazy danych SQL Azure](https://docs.microsoft.com/azure/sql-database/), tworzenie zasad zabezpieczeń, który dodaje predykatu w tabeli wiersze ograniczenie zwrócone do tych, które pasuje do żadnej bieżącego użytkownika bazy danych (przy użyciu CURRENT_USER() wbudowana funkcja) lub bieżąca nazwa logowania (przy użyciu wbudowanych funkcji SUSER_SNAME()):</span><span class="sxs-lookup"><span data-stu-id="ca37e-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>  
  
        ```tsql  
        CREATE SCHEMA Security  
        GO  
  
        CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)  
            RETURNS TABLE  
            WITH SCHEMABINDING  
        AS  
            RETURN SELECT 1 AS accessResult  
            WHERE @UserName = SUSER_SNAME()  
        GO  
  
        CREATE SECURITY POLICY Security.userAccessPolicy  
            ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,  
            ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable  
        GO  
        ```  
  
    -   <span data-ttu-id="ca37e-117">Jeśli używasz wersji programu SQL Server przed 2016, można uzyskać podobne funkcje przy użyciu widoku:</span><span class="sxs-lookup"><span data-stu-id="ca37e-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>  
  
        ```tsql  
        CREATE VIEW vw_MyTable  
        AS  
            RETURN SELECT * FROM MyTable  
            WHERE UserName = SUSER_SNAME()  
        GO  
        ```  
  
-   <span data-ttu-id="ca37e-118">Utwórz procedury składowane można wybrać, wstawiania, aktualizowania i usuwania danych.</span><span class="sxs-lookup"><span data-stu-id="ca37e-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="ca37e-119">Jeśli filtrowanie jest wprowadzany przy użyciu zasad zabezpieczeń, procedur składowanych należy wykonać te operacje w tabeli podstawowej bezpośrednio; w przeciwnym razie Jeśli filtrowanie jest wdrożonych przez widok, procedur składowanych zamiast tego powinien działać w widoku.</span><span class="sxs-lookup"><span data-stu-id="ca37e-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="ca37e-120">Zasady zabezpieczeń lub widok automatycznie filtrów wierszy zwrócony lub zmodyfikowane przez użytkownika zapytania i procedury składowanej zapewni przeszkodę granicy zabezpieczeń, aby uniemożliwić użytkownikom z dostępem do zapytania bezpośredniego pomyślnie uruchamiania zapytań, które można wywnioskować istnienie odfiltrowane dane.</span><span class="sxs-lookup"><span data-stu-id="ca37e-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>  
  
-   <span data-ttu-id="ca37e-121">Procedury składowanej wstawiania danych nazwę użytkownika przy użyciu tej samej funkcji określonej w zasadach zabezpieczeń lub Widok przechwytywania i Wstaw tę wartość w kolumnie nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ca37e-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>  
  
-   <span data-ttu-id="ca37e-122">Odmów wszystkie uprawnienia w tabelach (i widoków, jeśli ma to zastosowanie) do `public` roli.</span><span class="sxs-lookup"><span data-stu-id="ca37e-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="ca37e-123">Użytkownicy nie będą mogli dziedziczą uprawnienia z innych ról bazy danych, ponieważ predykatu filtru opartego na użytkownika lub nazwy logowania, a nie w odniesieniu do ról.</span><span class="sxs-lookup"><span data-stu-id="ca37e-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>  
  
-   <span data-ttu-id="ca37e-124">Udziel wykonać na procedury składowane do ról bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ca37e-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="ca37e-125">Użytkownicy mogą tylko uzyskiwać dostęp do danych przechowywanych procedur.</span><span class="sxs-lookup"><span data-stu-id="ca37e-125">Users can only access data through the stored procedures provided.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="ca37e-126">Zasoby zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="ca37e-126">External Resources</span></span>  
 <span data-ttu-id="ca37e-127">Aby uzyskać więcej informacji zobacz następujące zasoby.</span><span class="sxs-lookup"><span data-stu-id="ca37e-127">For more information, see the following resource.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ca37e-128">[Implementowanie zabezpieczeń na poziomie wierszy i komórek w niejawnych baz danych przy użyciu programu SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=98227) w witrynie TechCenter programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ca37e-128">[Implementing Row- and Cell-Level Security in Classified Databases Using SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=98227) on the SQL Server TechCenter site.</span></span>|<span data-ttu-id="ca37e-129">Informacje dotyczące używania zabezpieczeń na poziomie wierszy i komórek, aby spełnić wymagania dotyczące zabezpieczeń niejawnych bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ca37e-129">Describes how to use row- and cell-level security to meet classified database security requirements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca37e-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca37e-130">See Also</span></span>  
 [<span data-ttu-id="ca37e-131">Zabezpieczenia na poziomie wiersza</span><span class="sxs-lookup"><span data-stu-id="ca37e-131">Row-Level Security</span></span>](https://msdn.microsoft.com/library/dn765131.aspx)  
 [<span data-ttu-id="ca37e-132">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ca37e-132">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="ca37e-133">Przegląd zabezpieczeń serwera SQL</span><span class="sxs-lookup"><span data-stu-id="ca37e-133">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="ca37e-134">Scenariusze zabezpieczeń aplikacji w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="ca37e-134">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="ca37e-135">Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="ca37e-135">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="ca37e-136">Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="ca37e-136">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="ca37e-137">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="ca37e-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
