---
title: "Własność i oddzielenie użytkowników schematu w programie SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 168eaf9bc0bbac80cbd1e2bb0538aab89d262a49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a><span data-ttu-id="5d517-102">Własność i oddzielenie użytkowników schematu w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="5d517-102">Ownership and User-Schema Separation in SQL Server</span></span>
<span data-ttu-id="5d517-103">Kluczową ideą zabezpieczeń programu SQL Server jest właściciele obiektów uprawnień do administrowania nimi.</span><span class="sxs-lookup"><span data-stu-id="5d517-103">A core concept of SQL Server security is that owners of objects have irrevocable permissions to administer them.</span></span> <span data-ttu-id="5d517-104">Nie można usunąć uprawnień od właściciela obiektu i nie można usunąć użytkowników z bazy danych, jeśli są właścicielami obiektów w nim.</span><span class="sxs-lookup"><span data-stu-id="5d517-104">You cannot remove privileges from an object owner, and you cannot drop users from a database if they own objects in it.</span></span>  
  
## <a name="user-schema-separation"></a><span data-ttu-id="5d517-105">Oddzielanie schematów użytkownika</span><span class="sxs-lookup"><span data-stu-id="5d517-105">User-Schema Separation</span></span>  
 <span data-ttu-id="5d517-106">Oddzielanie schematów użytkownika pozwala na większą elastyczność w zarządzaniu uprawnienia obiektu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="5d517-106">User-schema separation allows for more flexibility in managing database object permissions.</span></span> <span data-ttu-id="5d517-107">A *schematu* jest nazwane kontener dla obiektów bazy danych, dzięki czemu można do obiektów grup w oddzielnych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5d517-107">A *schema* is a named container for database objects, which allows you to group objects into separate namespaces.</span></span> <span data-ttu-id="5d517-108">Na przykład przykładową bazę danych AdventureWorks zawiera schematów produkcji, sprzedaży i brzmi HumanResources.</span><span class="sxs-lookup"><span data-stu-id="5d517-108">For example, the AdventureWorks sample database contains schemas for Production, Sales, and HumanResources.</span></span>  
  
 <span data-ttu-id="5d517-109">Czteroczęściową nazewnictwa składnia odwoływania się do obiektów Określa nazwę schematu.</span><span class="sxs-lookup"><span data-stu-id="5d517-109">The four-part naming syntax for referring to objects specifies the schema name.</span></span>  
  
```  
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a><span data-ttu-id="5d517-110">Właściciele schematu i uprawnień</span><span class="sxs-lookup"><span data-stu-id="5d517-110">Schema Owners and Permissions</span></span>  
 <span data-ttu-id="5d517-111">Schematy może należeć do dowolnej podmiotem zabezpieczeń bazy danych, a jeden podmiot zabezpieczeń może mieć wiele schematów.</span><span class="sxs-lookup"><span data-stu-id="5d517-111">Schemas can be owned by any database principal, and a single principal can own multiple schemas.</span></span> <span data-ttu-id="5d517-112">Reguły zabezpieczeń można stosować do schematu, które są dziedziczone przez wszystkie obiekty w schemacie.</span><span class="sxs-lookup"><span data-stu-id="5d517-112">You can apply security rules to a schema, which are inherited by all objects in the schema.</span></span> <span data-ttu-id="5d517-113">Po skonfigurowaniu uprawnień dostępu do schematu te uprawnienia są automatycznie stosowane jako nowe obiekty zostaną dodane do schematu.</span><span class="sxs-lookup"><span data-stu-id="5d517-113">Once you set up access permissions for a schema, those permissions are automatically applied as new objects are added to the schema.</span></span> <span data-ttu-id="5d517-114">Użytkownicy mogą być przypisani schemat domyślny i wielu użytkowników bazy danych może współużytkować ten sam schemat.</span><span class="sxs-lookup"><span data-stu-id="5d517-114">Users can be assigned a default schema, and multiple database users can share the same schema.</span></span>  
  
 <span data-ttu-id="5d517-115">Domyślnie gdy deweloperom tworzenie obiektów w schemacie, obiekty są własnością podmiotu zabezpieczeń, który jest właścicielem schematu nie dewelopera.</span><span class="sxs-lookup"><span data-stu-id="5d517-115">By default, when developers create objects in a schema, the objects are owned by the security principal that owns the schema, not the developer.</span></span> <span data-ttu-id="5d517-116">Można przenieść własności obiektu z autoryzacji języka Transact-SQL ALTER.</span><span class="sxs-lookup"><span data-stu-id="5d517-116">Object ownership can be transferred with ALTER AUTHORIZATION Transact-SQL statement.</span></span> <span data-ttu-id="5d517-117">Schemat może również zawierać obiekty, które należą do różnych użytkowników i bardziej szczegółowego uprawnień niż te, które są przypisane do schematu, chociaż nie jest to zalecane, ponieważ do zarządzania uprawnieniami jest dodawany złożoności.</span><span class="sxs-lookup"><span data-stu-id="5d517-117">A schema can also contain objects that are owned by different users and have more granular permissions than those assigned to the schema, although this is not recommended because it adds complexity to managing permissions.</span></span> <span data-ttu-id="5d517-118">Obiekty można przenosić między schematów i własność schematu mogą być przekazywane między podmiotów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5d517-118">Objects can be moved between schemas, and schema ownership can be transferred between principals.</span></span> <span data-ttu-id="5d517-119">Bazy danych użytkowników można było porzucić bez wpływu na schematów.</span><span class="sxs-lookup"><span data-stu-id="5d517-119">Database users can be dropped without affecting schemas.</span></span>  
  
### <a name="built-in-schemas"></a><span data-ttu-id="5d517-120">Schematy wbudowane</span><span class="sxs-lookup"><span data-stu-id="5d517-120">Built-In Schemas</span></span>  
 <span data-ttu-id="5d517-121">Program SQL Server jest dostarczany z dziesięć wstępnie zdefiniowanych schematów, takich samych nazwach wbudowaną bazą danych użytkowników i ról.</span><span class="sxs-lookup"><span data-stu-id="5d517-121">SQL Server ships with ten pre-defined schemas that have the same names as the built-in database users and roles.</span></span> <span data-ttu-id="5d517-122">Istnieją one głównie dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="5d517-122">These exist mainly for backward compatibility.</span></span> <span data-ttu-id="5d517-123">Można usunąć schematów, które mają takie same nazwy co w przypadku ról stałej bazy danych, jeśli nie ma potrzeby.</span><span class="sxs-lookup"><span data-stu-id="5d517-123">You can drop the schemas that have the same names as the fixed database roles if you do not need them.</span></span> <span data-ttu-id="5d517-124">Nie można usunąć następujących schematów:</span><span class="sxs-lookup"><span data-stu-id="5d517-124">You cannot drop the following schemas:</span></span>  
  
-   `dbo`  
  
-   `guest`  
  
-   `sys`  
  
-   `INFORMATION_SCHEMA`  
  
 <span data-ttu-id="5d517-125">Jeśli upuść je z modelu bazy danych zostanie nie pojawią się one w nowych baz danych.</span><span class="sxs-lookup"><span data-stu-id="5d517-125">If you drop them from the model database, they will not appear in new databases.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d517-126">`sys` i `INFORMATION_SCHEMA` schematy są zastrzeżone dla obiektów systemowych.</span><span class="sxs-lookup"><span data-stu-id="5d517-126">The `sys` and `INFORMATION_SCHEMA` schemas are reserved for system objects.</span></span> <span data-ttu-id="5d517-127">Nie można utworzyć obiektów w tych schematów i nie można porzucić.</span><span class="sxs-lookup"><span data-stu-id="5d517-127">You cannot create objects in these schemas and you cannot drop them.</span></span>  
  
#### <a name="the-dbo-schema"></a><span data-ttu-id="5d517-128">Dbo schematu</span><span class="sxs-lookup"><span data-stu-id="5d517-128">The dbo Schema</span></span>  
 <span data-ttu-id="5d517-129">`dbo` Schemat jest domyślny schemat dla nowo utworzonej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="5d517-129">The `dbo` schema is the default schema for a newly created database.</span></span> <span data-ttu-id="5d517-130">`dbo` Schematu jest własnością `dbo` konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d517-130">The `dbo` schema is owned by the `dbo` user account.</span></span> <span data-ttu-id="5d517-131">Domyślnie użytkownicy utworzone za pomocą polecenia Utwórz użytkownika języka Transact-SQL mają `dbo` jako ich schemat domyślny.</span><span class="sxs-lookup"><span data-stu-id="5d517-131">By default, users created with the CREATE USER Transact-SQL command have `dbo` as their default schema.</span></span>  
  
 <span data-ttu-id="5d517-132">Użytkownicy, którzy mają przypisaną `dbo` schematu nie dziedziczy uprawnień z `dbo` konta użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d517-132">Users who are assigned the `dbo` schema do not inherit the permissions of the `dbo` user account.</span></span> <span data-ttu-id="5d517-133">Brak uprawnień są dziedziczone z schematu przez użytkowników. Schemat uprawnienia są dziedziczone przez obiekty bazy danych zawartych w schemacie.</span><span class="sxs-lookup"><span data-stu-id="5d517-133">No permissions are inherited from a schema by users; schema permissions are inherited by the database objects contained in the schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d517-134">Po obiektów bazy danych odwołuje się przy użyciu nazwy jednej części, domyślny schemat użytkownika najpierw sprawdza, programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5d517-134">When database objects are referenced by using a one-part name, SQL Server first looks in the user's default schema.</span></span> <span data-ttu-id="5d517-135">Jeśli obiekt nie zostaną znalezione, SQL Server wygląda dalej w `dbo` schematu.</span><span class="sxs-lookup"><span data-stu-id="5d517-135">If the object is not found there, SQL Server looks next in the `dbo` schema.</span></span> <span data-ttu-id="5d517-136">Jeśli obiekt nie znajduje się w `dbo` schematu, zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="5d517-136">If the object is not in the `dbo` schema, an error is returned.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="5d517-137">Zasoby zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="5d517-137">External Resources</span></span>  
 <span data-ttu-id="5d517-138">Aby uzyskać więcej informacji na własność obiektu i schematów zobacz następujące zasoby.</span><span class="sxs-lookup"><span data-stu-id="5d517-138">For more information on object ownership and schemas, see the following resources.</span></span>  
  
|<span data-ttu-id="5d517-139">Zasób</span><span class="sxs-lookup"><span data-stu-id="5d517-139">Resource</span></span>|<span data-ttu-id="5d517-140">Opis</span><span class="sxs-lookup"><span data-stu-id="5d517-140">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="5d517-141">[Schemat użytkownika separacji](http://msdn.microsoft.com/library/ms190387.aspx) w dokumentacji SQL Server Books Online</span><span class="sxs-lookup"><span data-stu-id="5d517-141">[User-Schema Separation](http://msdn.microsoft.com/library/ms190387.aspx) in SQL Server Books Online</span></span>|<span data-ttu-id="5d517-142">Opisuje zmiany wprowadzone przez oddzielenie schemat użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5d517-142">Describes the changes introduced by user-schema separation.</span></span> <span data-ttu-id="5d517-143">Obejmuje nowe zachowanie, jego wpływ na własność, widoków wykazu i uprawnień.</span><span class="sxs-lookup"><span data-stu-id="5d517-143">Includes new behavior, its impact on ownership, catalog views, and permissions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d517-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d517-144">See Also</span></span>  
 [<span data-ttu-id="5d517-145">Zabezpieczanie aplikacji ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5d517-145">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="5d517-146">Scenariusze zabezpieczeń aplikacji w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="5d517-146">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [<span data-ttu-id="5d517-147">Uwierzytelnianie programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="5d517-147">Authentication in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 [<span data-ttu-id="5d517-148">Serwer i ról bazy danych w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="5d517-148">Server and Database Roles in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 [<span data-ttu-id="5d517-149">Autoryzacja i uprawnienia w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="5d517-149">Authorization and Permissions in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 [<span data-ttu-id="5d517-150">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="5d517-150">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
