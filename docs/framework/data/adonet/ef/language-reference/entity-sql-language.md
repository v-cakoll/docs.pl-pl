---
title: Jednostki języka SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: b26d9a88130e0449d437ae9dd88e5e818f29f54d
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826229"
---
# <a name="entity-sql-language"></a><span data-ttu-id="e18e7-102">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="e18e7-102">Entity SQL Language</span></span>
<span data-ttu-id="e18e7-103">Jednostka SQL jest język zapytania niezależnie od magazynu, który jest podobny do bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="e18e7-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="e18e7-104">Jednostka SQL pozwala przesyłać zapytania dotyczące danych jednostki, jako obiekty lub w formie tabelarycznej.</span><span class="sxs-lookup"><span data-stu-id="e18e7-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="e18e7-105">Należy rozważyć użycie jednostki SQL w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="e18e7-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="e18e7-106">Gdy zapytania muszą być dynamicznie skonstruowane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e18e7-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="e18e7-107">W takim przypadku warto także za pomocą metody konstruktora zapytań z <xref:System.Data.Objects.ObjectQuery%601> zamiast tworzenia SQL jednostki ciągu w czasie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="e18e7-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="e18e7-108">Jeśli chcesz zdefiniować zapytanie jako część definicji modelu.</span><span class="sxs-lookup"><span data-stu-id="e18e7-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="e18e7-109">Tylko jednostki SQL jest obsługiwana w modelu danych.</span><span class="sxs-lookup"><span data-stu-id="e18e7-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="e18e7-110">Aby uzyskać więcej informacji, zobacz [QueryView — Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="e18e7-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
-   <span data-ttu-id="e18e7-111">W przypadku używania EntityClient do zwracania danych tylko do odczytu jednostki jako za pomocą zestawów wierszy <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="e18e7-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="e18e7-112">Aby uzyskać więcej informacji, zobacz [dostawca EntityClient dla programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="e18e7-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="e18e7-113">Jeśli jesteś już ekspertem w językach zapytań SQL, SQL jednostki może wydawać się najbardziej fizycznych dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="e18e7-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="e18e7-114">Z dostawcą EntityClient przy użyciu jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e18e7-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="e18e7-115">Jeśli chcesz użyć jednostki SQL z dostawcą EntityClient, zobacz następujące tematy, aby uzyskać więcej informacji:</span><span class="sxs-lookup"><span data-stu-id="e18e7-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="e18e7-116">Dostawca EntityClient dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="e18e7-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="e18e7-117">Instrukcje: Tworzenie ciągu połączenia EntityConnection</span><span class="sxs-lookup"><span data-stu-id="e18e7-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="e18e7-118">Instrukcje: Wykonywanie zapytania, które zwraca wyniki PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="e18e7-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="e18e7-119">Instrukcje: Wykonywanie zapytania, które zwraca wyniki StructuralType</span><span class="sxs-lookup"><span data-stu-id="e18e7-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="e18e7-120">Instrukcje: Wykonywanie zapytania, które zwraca wyniki RefType</span><span class="sxs-lookup"><span data-stu-id="e18e7-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="e18e7-121">Instrukcje: Wykonywanie zapytania, które zwraca typy złożone</span><span class="sxs-lookup"><span data-stu-id="e18e7-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="e18e7-122">Instrukcje: Wykonywanie zapytania, które zwraca kolekcje zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="e18e7-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="e18e7-123">Instrukcje: Wykonywanie zapytania SQL sparametryzowanej jednostki przy użyciu EntityCommand</span><span class="sxs-lookup"><span data-stu-id="e18e7-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="e18e7-124">Instrukcje: Wykonaj procedurę składowaną z parametrami przy użyciu EntityCommand</span><span class="sxs-lookup"><span data-stu-id="e18e7-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="e18e7-125">Instrukcje: Wykonywanie zapytania Polimorficznego</span><span class="sxs-lookup"><span data-stu-id="e18e7-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="e18e7-126">Instrukcje: Nawigowanie po relacjach za pomocą operatora nawigowania</span><span class="sxs-lookup"><span data-stu-id="e18e7-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="e18e7-127">Za pomocą obiektu zapytań przy użyciu jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e18e7-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="e18e7-128">Jeśli chcesz jednostki SQL za pomocą zapytań dotyczących obiektów, zobacz następujące tematy, aby uzyskać więcej informacji:</span><span class="sxs-lookup"><span data-stu-id="e18e7-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 <span data-ttu-id="e18e7-129">[Instrukcje: Wykonywanie zapytania, które zwraca obiekty typu jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e18e7-129">[How to: Execute a Query that Returns Entity Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span></span>  
  
 <span data-ttu-id="e18e7-130">[Instrukcje: Wykonaj zapytanie parametryczne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e18e7-130">[How to: Execute a Parameterized Query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>  
  
 <span data-ttu-id="e18e7-131">[Instrukcje: Nawigowanie po relacjach za pomocą właściwości nawigacji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e18e7-131">[How to: Navigate Relationships Using Navigation Properties](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span></span>  
  
 <span data-ttu-id="e18e7-132">[Instrukcje: Wywoływanie funkcji zdefiniowanej przez użytkownika](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e18e7-132">[How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span></span>  
  
 <span data-ttu-id="e18e7-133">[Instrukcje: Filtrowanie danych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e18e7-133">[How to: Filter Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span></span>  
  
 <span data-ttu-id="e18e7-134">[Instrukcje: Sortowanie danych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e18e7-134">[How to: Sort Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span></span>  
  
 <span data-ttu-id="e18e7-135">[Instrukcje: Grupowanie danych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e18e7-135">[How to: Group Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span></span>  
  
 <span data-ttu-id="e18e7-136">[Instrukcje: Zagregowane dane](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e18e7-136">[How to: Aggregate Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span></span>  
  
 <span data-ttu-id="e18e7-137">[Instrukcje: Wykonywanie zapytania, które zwraca obiekty typu anonimowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e18e7-137">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>  
  
 <span data-ttu-id="e18e7-138">[Instrukcje: Wykonywanie zapytania, które zwraca kolekcję typów pierwotnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e18e7-138">[How to: Execute a Query that Returns a Collection of Primitive Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span></span>  
  
 <span data-ttu-id="e18e7-139">[Instrukcje: Zapytanie powiązane obiekty w obiekt EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e18e7-139">[How to: Query Related Objects in an EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span></span>  
  
 <span data-ttu-id="e18e7-140">[Instrukcje: Kolejność sumę dwóch zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e18e7-140">[How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span></span>  
  
 <span data-ttu-id="e18e7-141">[Instrukcje: Przejrzyj wyniki zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e18e7-141">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e18e7-142">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e18e7-142">In This Section</span></span>  
 [<span data-ttu-id="e18e7-143">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e18e7-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="e18e7-144">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e18e7-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="e18e7-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e18e7-145">See also</span></span>
- [<span data-ttu-id="e18e7-146">Program Entity Framework na platformie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e18e7-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
- [<span data-ttu-id="e18e7-147">Dokumentacja języka</span><span class="sxs-lookup"><span data-stu-id="e18e7-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
