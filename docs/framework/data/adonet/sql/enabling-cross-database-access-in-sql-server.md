---
title: "Włączanie dostępu między bazami danych w programie SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
caps.latest.revision: "10"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2a31bddfec44ad4b33f1b595c2746d1a0e841b82
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="58821-102">Włączanie dostępu między bazami danych w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="58821-102">Enabling Cross-Database Access in SQL Server</span></span>
<span data-ttu-id="58821-103">Łańcucha między bazami danych własność występuje, gdy procedura w jednej bazie danych jest zależna od obiektów w innej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="58821-103">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="58821-104">Łańcuch własności między bazami danych działa w taki sam sposób jak własność łańcucha w ramach pojedynczej bazy danych, z tą różnicą, że łańcucha własności nieprzerwany wymaga, aby wszystkich właścicieli obiektów są mapowane do tego samego konta logowania.</span><span class="sxs-lookup"><span data-stu-id="58821-104">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="58821-105">Jeśli obiekt źródłowy w źródłowej bazy danych i obiektów docelowych w z docelowymi bazami danych są własnością tego samego konta logowania, programu SQL Server nie sprawdza uprawnienia do obiektów docelowych.</span><span class="sxs-lookup"><span data-stu-id="58821-105">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="58821-106">Domyślnie wyłączone</span><span class="sxs-lookup"><span data-stu-id="58821-106">Off By Default</span></span>  
 <span data-ttu-id="58821-107">Własność łańcucha między bazami danych jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="58821-107">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="58821-108">Firma Microsoft zaleca wyłączenie łańcucha własności między bazami danych, ponieważ ujawnia on należy do następujących zagrożenia bezpieczeństwa:</span><span class="sxs-lookup"><span data-stu-id="58821-108">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
-   <span data-ttu-id="58821-109">Bazy danych właścicieli i członkowie `db_ddladmin` lub `db_owners` ról bazy danych można tworzyć obiektów, które są własnością innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="58821-109">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="58821-110">Te obiekty potencjalnie może kierować obiektów w innych bazach danych.</span><span class="sxs-lookup"><span data-stu-id="58821-110">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="58821-111">Oznacza to, że po włączeniu procesu tworzenia łańcucha między bazami danych własności musi pełnego zaufania, tych użytkowników z danymi w wszystkie bazy danych.</span><span class="sxs-lookup"><span data-stu-id="58821-111">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
-   <span data-ttu-id="58821-112">Użytkownicy mający uprawnienie CREATE DATABASE można tworzyć nowych baz danych i dołączać istniejącej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="58821-112">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="58821-113">Jeśli włączono tworzenie łańcucha między bazami danych własność tych użytkowników są dostępne obiektów w innych bazach danych, które mogą nie mieć uprawnień nowo utworzony lub dołączone baz danych, które tworzą.</span><span class="sxs-lookup"><span data-stu-id="58821-113">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="58821-114">Włączanie łańcucha własności między bazami danych</span><span class="sxs-lookup"><span data-stu-id="58821-114">Enabling Cross-database Ownership Chaining</span></span>  
 <span data-ttu-id="58821-115">Tworzenie łańcucha między bazami danych własność powinna być włączona tylko w środowiskach, w którym można w pełni zaufane uprawnieniach użytkowników.</span><span class="sxs-lookup"><span data-stu-id="58821-115">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="58821-116">Można skonfigurować podczas instalacji dla wszystkich baz danych lub selektywnie dla baz danych przy użyciu [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] polecenia `sp_configure` i `ALTER DATABASE`.</span><span class="sxs-lookup"><span data-stu-id="58821-116">It can be configured during setup for all databases, or selectively for specific databases using the [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="58821-117">Aby selektywnie skonfigurować tworzenie łańcucha własności między bazami danych, użyj `sp_configure` jej wyłączenia serwera.</span><span class="sxs-lookup"><span data-stu-id="58821-117">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="58821-118">Następnie za pomocą polecenia ALTER DATABASE USTAWIĆ ON DB_CHAINING skonfigurować tworzenie łańcucha tylko baz danych, które tego wymagają własności między bazami danych.</span><span class="sxs-lookup"><span data-stu-id="58821-118">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="58821-119">Poniższy przykład powoduje włączenie łańcucha między bazami danych własności dla wszystkich baz danych:</span><span class="sxs-lookup"><span data-stu-id="58821-119">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```  
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="58821-120">Poniższy przykład powoduje włączenie łańcucha między bazami danych własności dla baz danych:</span><span class="sxs-lookup"><span data-stu-id="58821-120">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```  
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="58821-121">Dynamiczne SQL</span><span class="sxs-lookup"><span data-stu-id="58821-121">Dynamic SQL</span></span>  
 <span data-ttu-id="58821-122">Tworzenie łańcucha własności między bazami danych nie działa w przypadku, gdy utworzony dynamicznie instrukcji SQL są wykonywane, chyba że ten sam użytkownik istnieje w obu bazach danych.</span><span class="sxs-lookup"><span data-stu-id="58821-122">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="58821-123">Można obejść to w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] , tworząc procedury przechowywanej, która uzyskuje dostęp do danych w innej bazie danych i podpisywania procedury przy użyciu certyfikatu, który istnieje w obu bazach danych.</span><span class="sxs-lookup"><span data-stu-id="58821-123">You can work around this in [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="58821-124">To umożliwia użytkownikom dostęp do zasobów bazy danych używane przez procedurę bez przyznawania im dostępu do bazy danych lub uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="58821-124">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="58821-125">Zasoby zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="58821-125">External Resources</span></span>  
 <span data-ttu-id="58821-126">Aby uzyskać więcej informacji zobacz następujące zasoby.</span><span class="sxs-lookup"><span data-stu-id="58821-126">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="58821-127">Zasób</span><span class="sxs-lookup"><span data-stu-id="58821-127">Resource</span></span>|<span data-ttu-id="58821-128">Opis</span><span class="sxs-lookup"><span data-stu-id="58821-128">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="58821-129">[Rozszerzanie personifikacji bazy danych przy użyciu EXECUTE AS](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) i [Cross własność DB łańcucha opcja](http://msdn.microsoft.com/library/ms188694.aspx) [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] książki Online.</span><span class="sxs-lookup"><span data-stu-id="58821-129">[Extending Database Impersonation by Using EXECUTE AS](http://msdn.microsoft.com/library/ms188304\(SQL.105\).aspx) and [Cross DB Ownership Chaining Option](http://msdn.microsoft.com/library/ms188694.aspx)[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online.</span></span>|<span data-ttu-id="58821-130">Tematach opisano, jak skonfigurować tworzenie łańcucha między bazami danych własność wystąpienia [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58821-130">Topics describe how to configure cross-database ownership chaining for an instance of [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58821-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58821-131">See Also</span></span>  
 [<span data-ttu-id="58821-132">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="58821-132">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="58821-133">Przegląd zabezpieczeń serwera SQL</span><span class="sxs-lookup"><span data-stu-id="58821-133">Overview of SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [<span data-ttu-id="58821-134">Zarządzanie uprawnieniami za pomocą procedur składowanych w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="58821-134">Managing Permissions with Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="58821-135">Pisanie bezpiecznego dynamicznego kodu SQL w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="58821-135">Writing Secure Dynamic SQL in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [<span data-ttu-id="58821-136">Rejestrowanie procedur składowanych w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="58821-136">Signing Stored Procedures in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [<span data-ttu-id="58821-137">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="58821-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
