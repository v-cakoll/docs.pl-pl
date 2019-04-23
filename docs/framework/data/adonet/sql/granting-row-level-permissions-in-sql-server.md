---
title: Udzielanie uprawnień na poziomie wiersza w programie SQL Server
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 891b5114551c5784b11504f2463525087125131f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973086"
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="e88a5-102">Udzielanie uprawnień na poziomie wiersza w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="e88a5-102">Granting Row-Level Permissions in SQL Server</span></span>

<span data-ttu-id="e88a5-103">W niektórych scenariuszach istnieje wymóg do kontrolowania dostępu do danych na bardziej szczegółowym poziomie niż zapewnia jakie po prostu udzielanie, odwoływanie lub odmawianie uprawnień.</span><span class="sxs-lookup"><span data-stu-id="e88a5-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="e88a5-104">Na przykład szpitali aplikacji bazy danych może wymagać poszczególnych lekarzy ograniczona do uzyskiwania dostępu do informacji dotyczących tylko pacjentów.</span><span class="sxs-lookup"><span data-stu-id="e88a5-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="e88a5-105">Istnieją podobne wymagania w wielu środowiskach, w tym Finanse, prawo, instytucji rządowych i wojskowe aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e88a5-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="e88a5-106">Aby ułatwić obsługę tych scenariuszy, programu SQL Server 2016 zapewnia [zabezpieczenia na poziomie wiersza](/sql/relational-databases/security/row-level-security) funkcja, która upraszcza i umożliwia scentralizowanie logiki dostępu na poziomie wiersza w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e88a5-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](/sql/relational-databases/security/row-level-security) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="e88a5-107">We wcześniejszych wersjach programu SQL Server podobne funkcje można osiągnąć przy użyciu widoków wprowadzenie filtrowanie na poziomie wiersza.</span><span class="sxs-lookup"><span data-stu-id="e88a5-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>

## <a name="implementing-row-level-filtering"></a><span data-ttu-id="e88a5-108">Implementowanie filtrowanie na poziomie wiersza</span><span class="sxs-lookup"><span data-stu-id="e88a5-108">Implementing Row-level Filtering</span></span>

<span data-ttu-id="e88a5-109">Filtrowanie na poziomie wiersza jest używana do przechowywania informacji w jednej tabeli podobnie jak w powyższym przykładzie szpitali aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e88a5-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="e88a5-110">Aby zaimplementować filtrowanie każdy wiersz na poziomie wiersza ma kolumny, która ma parametr różnicujący, takie jak nazwa użytkownika, etykietę lub inny identyfikator.</span><span class="sxs-lookup"><span data-stu-id="e88a5-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="e88a5-111">Można tworzyć zasady zabezpieczeń lub widoku w tabeli i filtrować wiersze, których użytkownik ma dostęp.</span><span class="sxs-lookup"><span data-stu-id="e88a5-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="e88a5-112">Następnie można utworzyć sparametryzowany procedur składowanych, które kontrolę typów zapytań, które użytkownik może uruchomić.</span><span class="sxs-lookup"><span data-stu-id="e88a5-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>

<span data-ttu-id="e88a5-113">Poniższy przykład zawiera opis sposobu konfigurowania, filtrowanie na podstawie nazwy użytkownika lub logowania na poziomie wiersza:</span><span class="sxs-lookup"><span data-stu-id="e88a5-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>

- <span data-ttu-id="e88a5-114">Utwórz tabelę, dodając kolumny do przechowywania nazwy.</span><span class="sxs-lookup"><span data-stu-id="e88a5-114">Create the table, adding a column to store the name.</span></span>

- <span data-ttu-id="e88a5-115">Włącz filtrowanie na poziomie wiersza:</span><span class="sxs-lookup"><span data-stu-id="e88a5-115">Enable row-level filtering:</span></span>

  - <span data-ttu-id="e88a5-116">Jeśli używasz programu SQL Server 2016 lub nowszym, lub [usługi Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), utworzyć zasady zabezpieczeń, który dodaje predykatu w tabeli wiersze ograniczenie zwrócone do tych, które pasują do jednego bieżącego użytkownika bazy danych (za pomocą CURRENT_USER() wbudowana funkcja) lub bieżąca nazwa logowania (przy użyciu wbudowanej funkcji SUSER_SNAME()):</span><span class="sxs-lookup"><span data-stu-id="e88a5-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>

      ```sql
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

  - <span data-ttu-id="e88a5-117">Jeśli używasz wersji programu SQL Server przed 2016, można osiągnąć podobne funkcje przy użyciu widoku:</span><span class="sxs-lookup"><span data-stu-id="e88a5-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- <span data-ttu-id="e88a5-118">Tworzenie procedur składowanych, aby wybrać, wstawianie, aktualizowanie i usuwanie danych.</span><span class="sxs-lookup"><span data-stu-id="e88a5-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="e88a5-119">Jeśli filtrowanie jest wprowadzany przez zasady zabezpieczeń, procedur składowanych powinien wykonywać te operacje, w tabeli podstawowej bezpośrednio; w przeciwnym razie Jeśli filtrowanie jest wprowadzany przez widok, procedur składowanych należy zamiast tego działać widoku.</span><span class="sxs-lookup"><span data-stu-id="e88a5-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="e88a5-120">Zasady zabezpieczeń lub widoku automatycznie spowoduje odfiltrowanie wierszy zwrócony lub modyfikowane przez zapytania użytkowników i procedury składowanej zapewni trudniejsze granicy zabezpieczeń uniemożliwić użytkownikom przy użyciu zapytania bezpośredniego dostępu do poprawnego działania zapytania, które może wywnioskować istnienie odfiltrowane dane.</span><span class="sxs-lookup"><span data-stu-id="e88a5-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>

- <span data-ttu-id="e88a5-121">Dla procedur składowanych, które wstawiają dane przechwytywania nazwę użytkownika przy użyciu tej samej funkcji, które są określone w zasadach zabezpieczeń lub w widoku, a następnie wstaw tę wartość w kolumnie Nazwa użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e88a5-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>

- <span data-ttu-id="e88a5-122">Odmowa uprawnień wszystkie tabele (i widoki, jeśli ma to zastosowanie) do `public` roli.</span><span class="sxs-lookup"><span data-stu-id="e88a5-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="e88a5-123">Użytkownicy nie będą mogli dziedziczą uprawnienia z innych ról bazy danych, ponieważ predykatu filtru opartego na użytkownika lub nazwy logowania, nie na rolach.</span><span class="sxs-lookup"><span data-stu-id="e88a5-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>

- <span data-ttu-id="e88a5-124">Udziel wykonać na procedurach przechowywanych do ról bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e88a5-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="e88a5-125">Użytkownicy mogą tylko dostęp do danych przy użyciu przechowywanych procedur.</span><span class="sxs-lookup"><span data-stu-id="e88a5-125">Users can only access data through the stored procedures provided.</span></span>

## <a name="see-also"></a><span data-ttu-id="e88a5-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e88a5-126">See also</span></span>

- [<span data-ttu-id="e88a5-127">Zabezpieczenia na poziomie wiersza</span><span class="sxs-lookup"><span data-stu-id="e88a5-127">Row-Level Security</span></span>](/sql/relational-databases/security/row-level-security)
- [<span data-ttu-id="e88a5-128">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e88a5-128">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="e88a5-129">Przegląd zabezpieczeń serwera SQL</span><span class="sxs-lookup"><span data-stu-id="e88a5-129">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [<span data-ttu-id="e88a5-130">Scenariusze zabezpieczeń aplikacji w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="e88a5-130">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="e88a5-131">Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="e88a5-131">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="e88a5-132">Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="e88a5-132">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="e88a5-133">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="e88a5-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
