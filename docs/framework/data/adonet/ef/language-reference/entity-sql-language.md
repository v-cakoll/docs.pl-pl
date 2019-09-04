---
title: Język Entity SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: a2e4b7245dbfccf7864481b52a0e868a85efbca6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251019"
---
# <a name="entity-sql-language"></a><span data-ttu-id="12b17-102">Język Entity SQL</span><span class="sxs-lookup"><span data-stu-id="12b17-102">Entity SQL Language</span></span>
<span data-ttu-id="12b17-103">Entity SQL to język zapytań niezależnych od magazynu, podobny do SQL.</span><span class="sxs-lookup"><span data-stu-id="12b17-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="12b17-104">Entity SQL umożliwia wykonywanie zapytań dotyczących danych jednostki jako obiektów lub w formie tabelarycznej.</span><span class="sxs-lookup"><span data-stu-id="12b17-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="12b17-105">Należy rozważyć użycie Entity SQL w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="12b17-105">You should consider using Entity SQL in the following cases:</span></span>  
  
- <span data-ttu-id="12b17-106">Gdy zapytanie musi być skonstruowane dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="12b17-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="12b17-107">W takim przypadku należy również rozważyć użycie metod <xref:System.Data.Objects.ObjectQuery%601> konstruktora zapytań zamiast konstruowania Entity SQL ciągu zapytania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="12b17-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
- <span data-ttu-id="12b17-108">Jeśli chcesz zdefiniować zapytanie jako część definicji modelu.</span><span class="sxs-lookup"><span data-stu-id="12b17-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="12b17-109">Tylko Entity SQL jest obsługiwane w modelu danych.</span><span class="sxs-lookup"><span data-stu-id="12b17-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="12b17-110">Aby uzyskać więcej informacji, zobacz [QueryView element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="12b17-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
- <span data-ttu-id="12b17-111">W przypadku używania EntityClient do zwracania danych jednostki tylko do odczytu jako zestawów wierszy przy <xref:System.Data.EntityClient.EntityDataReader>użyciu.</span><span class="sxs-lookup"><span data-stu-id="12b17-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="12b17-112">Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="12b17-112">For more information, see [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span></span>  
  
- <span data-ttu-id="12b17-113">Jeśli już jesteś ekspertem w językach zapytań opartych na języku SQL, Entity SQL mogą być najbardziej naturalne.</span><span class="sxs-lookup"><span data-stu-id="12b17-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="12b17-114">Używanie Entity SQL z dostawcą EntityClient</span><span class="sxs-lookup"><span data-stu-id="12b17-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="12b17-115">Jeśli chcesz użyć Entity SQL z dostawcą EntityClient, zobacz następujące tematy, aby uzyskać więcej informacji:</span><span class="sxs-lookup"><span data-stu-id="12b17-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="12b17-116">Dostawca EntityClient dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="12b17-116">EntityClient Provider for the Entity Framework</span></span>](../entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="12b17-117">Instrukcje: Tworzenie parametrów połączenia usługi EntityConnection</span><span class="sxs-lookup"><span data-stu-id="12b17-117">How to: Build an EntityConnection Connection String</span></span>](../how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="12b17-118">Instrukcje: Wykonywanie zapytania, które zwraca wyniki typu pierwotnego</span><span class="sxs-lookup"><span data-stu-id="12b17-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="12b17-119">Instrukcje: Wykonaj zapytanie zwracające wyniki StructuralType</span><span class="sxs-lookup"><span data-stu-id="12b17-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="12b17-120">Instrukcje: Wykonaj zapytanie zwracające wyniki RefType</span><span class="sxs-lookup"><span data-stu-id="12b17-120">How to: Execute a Query that Returns RefType Results</span></span>](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="12b17-121">Instrukcje: Wykonaj zapytanie zwracające typy złożone</span><span class="sxs-lookup"><span data-stu-id="12b17-121">How to: Execute a Query that Returns Complex Types</span></span>](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="12b17-122">Instrukcje: Wykonaj zapytanie zwracające kolekcje zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="12b17-122">How to: Execute a Query that Returns Nested Collections</span></span>](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="12b17-123">Instrukcje: Wykonywanie zapytania Entity SQL sparametryzowanego przy użyciu EntityCommand</span><span class="sxs-lookup"><span data-stu-id="12b17-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="12b17-124">Instrukcje: Wykonaj sparametryzowane procedury składowane za pomocą EntityCommand</span><span class="sxs-lookup"><span data-stu-id="12b17-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="12b17-125">Instrukcje: Wykonywanie zapytania polimorficznego</span><span class="sxs-lookup"><span data-stu-id="12b17-125">How to: Execute a Polymorphic Query</span></span>](../how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="12b17-126">Instrukcje: Nawigowanie po relacjach za pomocą operatora nawigacji</span><span class="sxs-lookup"><span data-stu-id="12b17-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="12b17-127">Używanie Entity SQL z kwerendami obiektów</span><span class="sxs-lookup"><span data-stu-id="12b17-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="12b17-128">Jeśli chcesz użyć Entity SQL z kwerendami obiektów, zobacz następujące tematy, aby uzyskać więcej informacji:</span><span class="sxs-lookup"><span data-stu-id="12b17-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 <span data-ttu-id="12b17-129">[Instrukcje: Wykonywanie zapytania, które zwraca obiekty typu Entity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12b17-129">[How to: Execute a Query that Returns Entity Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span></span>  
  
 <span data-ttu-id="12b17-130">[Instrukcje: Wykonaj zapytanie parametryczne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12b17-130">[How to: Execute a Parameterized Query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>  
  
 <span data-ttu-id="12b17-131">[Instrukcje: Nawigowanie po relacjach przy użyciu właściwości nawigacji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12b17-131">[How to: Navigate Relationships Using Navigation Properties](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span></span>  
  
 <span data-ttu-id="12b17-132">[Instrukcje: Wywoływanie funkcji zdefiniowanej przez użytkownika](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12b17-132">[How to: Call a User-Defined Function](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span></span>  
  
 <span data-ttu-id="12b17-133">[Instrukcje: Filtrowanie danych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12b17-133">[How to: Filter Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span></span>  
  
 <span data-ttu-id="12b17-134">[Instrukcje: Sortuj dane](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12b17-134">[How to: Sort Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span></span>  
  
 <span data-ttu-id="12b17-135">[Instrukcje: Grupuj dane](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12b17-135">[How to: Group Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span></span>  
  
 <span data-ttu-id="12b17-136">[Instrukcje: Agregowanie danych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12b17-136">[How to: Aggregate Data](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span></span>  
  
 <span data-ttu-id="12b17-137">[Instrukcje: Wykonaj zapytanie zwracające obiekty typu anonimowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12b17-137">[How to: Execute a Query that Returns Anonymous Type Objects](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>  
  
 <span data-ttu-id="12b17-138">[Instrukcje: Wykonaj zapytanie, które zwraca kolekcję typów pierwotnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12b17-138">[How to: Execute a Query that Returns a Collection of Primitive Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span></span>  
  
 <span data-ttu-id="12b17-139">[Instrukcje: Zapytanie dotyczące obiektów pokrewnych w obiekcie EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12b17-139">[How to: Query Related Objects in an EntityCollection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span></span>  
  
 <span data-ttu-id="12b17-140">[Instrukcje: Zamów Unię dwóch zapytań](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12b17-140">[How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span></span>  
  
 <span data-ttu-id="12b17-141">[Instrukcje: Strona za poorednictwem wyników zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="12b17-141">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="12b17-142">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="12b17-142">In This Section</span></span>  
 [<span data-ttu-id="12b17-143">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="12b17-143">Entity SQL Overview</span></span>](entity-sql-overview.md)  
  
 [<span data-ttu-id="12b17-144">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="12b17-144">Entity SQL Reference</span></span>](entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="12b17-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12b17-145">See also</span></span>

- [<span data-ttu-id="12b17-146">Program Entity Framework na platformie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="12b17-146">ADO.NET Entity Framework</span></span>](../index.md)
- [<span data-ttu-id="12b17-147">Dokumentacja języka</span><span class="sxs-lookup"><span data-stu-id="12b17-147">Language Reference</span></span>](index.md)
