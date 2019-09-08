---
title: Udzielanie uprawnień na poziomie wiersza w programie SQL Server
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: df5fcb4a6c73e12bec2ab17501fdfb02cf672324
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782355"
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="45e33-102">Udzielanie uprawnień na poziomie wiersza w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="45e33-102">Granting Row-Level Permissions in SQL Server</span></span>

<span data-ttu-id="45e33-103">W niektórych scenariuszach istnieje wymóg, aby kontrolować dostęp do danych na bardziej szczegółowym poziomie niż to, co po prostu przyznanie, odwoływanie lub odmowa uprawnień.</span><span class="sxs-lookup"><span data-stu-id="45e33-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="45e33-104">Na przykład aplikacja szpitalnej bazy danych może wymagać, aby indywidualni Lekarze mogli uzyskiwać dostęp do informacji związanych tylko z ich pacjentami.</span><span class="sxs-lookup"><span data-stu-id="45e33-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="45e33-105">Podobne wymagania istnieją w wielu środowiskach, takich jak aplikacje finansowe, prawne, rządowe i wojskowe.</span><span class="sxs-lookup"><span data-stu-id="45e33-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="45e33-106">Aby rozwiązać te scenariusze, SQL Server 2016 zapewnia funkcję [zabezpieczeń na poziomie wiersza](/sql/relational-databases/security/row-level-security) , która upraszcza i scentralizowana logiki dostępu na poziomie wiersza w zasadach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="45e33-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](/sql/relational-databases/security/row-level-security) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="45e33-107">W przypadku wcześniejszych wersji SQL Server można osiągnąć podobną funkcjonalność przy użyciu widoków, aby przyjąć filtrowanie na poziomie wiersza.</span><span class="sxs-lookup"><span data-stu-id="45e33-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>

## <a name="implementing-row-level-filtering"></a><span data-ttu-id="45e33-108">Implementowanie filtrowania na poziomie wierszy</span><span class="sxs-lookup"><span data-stu-id="45e33-108">Implementing Row-level Filtering</span></span>

<span data-ttu-id="45e33-109">Filtrowanie na poziomie wiersza jest używane w przypadku aplikacji przechowujących informacje w pojedynczej tabeli, jak w powyższym przykładzie szpital.</span><span class="sxs-lookup"><span data-stu-id="45e33-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="45e33-110">Aby zaimplementować filtrowanie na poziomie wierszy każdy wiersz ma kolumnę definiującą parametr odróżniający, taki jak nazwa użytkownika, etykieta lub inny identyfikator.</span><span class="sxs-lookup"><span data-stu-id="45e33-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="45e33-111">Tworzysz zasady zabezpieczeń lub widok w tabeli, który filtruje wiersze, do których użytkownik może uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="45e33-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="45e33-112">Następnie utworzysz sparametryzowane procedury składowane, które kontrolują typy zapytań, które użytkownik może wykonywać.</span><span class="sxs-lookup"><span data-stu-id="45e33-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>

<span data-ttu-id="45e33-113">W poniższym przykładzie opisano sposób konfigurowania filtrowania na poziomie wierszy na podstawie nazwy użytkownika lub logowania:</span><span class="sxs-lookup"><span data-stu-id="45e33-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>

- <span data-ttu-id="45e33-114">Utwórz tabelę, dodając do niej kolumnę.</span><span class="sxs-lookup"><span data-stu-id="45e33-114">Create the table, adding a column to store the name.</span></span>

- <span data-ttu-id="45e33-115">Włącz filtrowanie na poziomie wierszy:</span><span class="sxs-lookup"><span data-stu-id="45e33-115">Enable row-level filtering:</span></span>

  - <span data-ttu-id="45e33-116">Jeśli używasz SQL Server 2016 lub nowszej lub [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), Utwórz zasady zabezpieczeń, które dodają predykat w tabeli, ograniczając wiersze zwracane do tych, które pasują do bieżącego użytkownika bazy danych (za pomocą wbudowanej funkcji CURRENT_USER ()) lub Bieżąca nazwa logowania (przy użyciu wbudowanej funkcji SUSER_SNAME ()):</span><span class="sxs-lookup"><span data-stu-id="45e33-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>

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

  - <span data-ttu-id="45e33-117">Jeśli używasz wersji SQL Server wcześniejszej niż 2016, możesz uzyskać podobną funkcjonalność przy użyciu widoku:</span><span class="sxs-lookup"><span data-stu-id="45e33-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- <span data-ttu-id="45e33-118">Utwórz procedury składowane, aby wybierać, wstawiać, aktualizować i usuwać dane.</span><span class="sxs-lookup"><span data-stu-id="45e33-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="45e33-119">Jeśli filtrowanie zostało wprowadzone przez zasady zabezpieczeń, procedury składowane powinny wykonać te operacje bezpośrednio w tabeli podstawowej; w przeciwnym razie, jeśli Filtrowanie jest wykonywane przez widok, procedury składowane powinny w zamian działać względem widoku.</span><span class="sxs-lookup"><span data-stu-id="45e33-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="45e33-120">Zasady zabezpieczeń lub widok automatycznie filtrują wiersze zwrócone lub zmodyfikowane przez zapytania użytkowników, a procedura składowana zapewnia trudniejszą granicę zabezpieczeń, aby uniemożliwić użytkownikom bezpośredni dostęp do zapytań, które mogą wywnioskować istnienie filtrowanych danych.</span><span class="sxs-lookup"><span data-stu-id="45e33-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>

- <span data-ttu-id="45e33-121">W przypadku procedur składowanych, które wstawiają dane, Przechwyć nazwę użytkownika przy użyciu tej samej funkcji, która jest określona w zasadach zabezpieczeń lub widoku, i Wstaw tę wartość do kolumny UserName.</span><span class="sxs-lookup"><span data-stu-id="45e33-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>

- <span data-ttu-id="45e33-122">Odrzuć wszystkie uprawnienia w tabelach (i widokach, jeśli ma to zastosowanie `public` ) do roli.</span><span class="sxs-lookup"><span data-stu-id="45e33-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="45e33-123">Użytkownicy nie będą mogli dziedziczyć uprawnień z innych ról bazy danych, ponieważ predykat filtru jest oparty na nazwach użytkowników lub nazw logowania, a nie na rolach.</span><span class="sxs-lookup"><span data-stu-id="45e33-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>

- <span data-ttu-id="45e33-124">Przyznaj wykonywanie na procedurach składowanych do ról bazy danych.</span><span class="sxs-lookup"><span data-stu-id="45e33-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="45e33-125">Użytkownicy mogą uzyskiwać dostęp tylko do danych za pomocą dostarczonych procedur składowanych.</span><span class="sxs-lookup"><span data-stu-id="45e33-125">Users can only access data through the stored procedures provided.</span></span>

## <a name="see-also"></a><span data-ttu-id="45e33-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45e33-126">See also</span></span>

- [<span data-ttu-id="45e33-127">Zabezpieczenia na poziomie wiersza</span><span class="sxs-lookup"><span data-stu-id="45e33-127">Row-Level Security</span></span>](/sql/relational-databases/security/row-level-security)
- [<span data-ttu-id="45e33-128">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="45e33-128">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="45e33-129">Przegląd zabezpieczeń serwera SQL</span><span class="sxs-lookup"><span data-stu-id="45e33-129">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="45e33-130">Scenariusze zabezpieczeń aplikacji w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="45e33-130">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="45e33-131">Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="45e33-131">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="45e33-132">Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="45e33-132">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="45e33-133">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="45e33-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
