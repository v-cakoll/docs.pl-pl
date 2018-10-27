---
title: Jednostki języka SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: f12a20f85a0449778614d3098f69d3da90902c95
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50048446"
---
# <a name="entity-sql-language"></a><span data-ttu-id="5b263-102">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="5b263-102">Entity SQL Language</span></span>
<span data-ttu-id="5b263-103">Jednostka SQL jest język zapytania niezależnie od magazynu, który jest podobny do bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="5b263-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="5b263-104">Jednostka SQL pozwala przesyłać zapytania dotyczące danych jednostki, jako obiekty lub w formie tabelarycznej.</span><span class="sxs-lookup"><span data-stu-id="5b263-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="5b263-105">Należy rozważyć użycie jednostki SQL w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="5b263-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="5b263-106">Gdy zapytania muszą być dynamicznie skonstruowane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5b263-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="5b263-107">W takim przypadku warto także za pomocą metody konstruktora zapytań z <xref:System.Data.Objects.ObjectQuery%601> zamiast tworzenia SQL jednostki ciągu w czasie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="5b263-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="5b263-108">Jeśli chcesz zdefiniować zapytanie jako część definicji modelu.</span><span class="sxs-lookup"><span data-stu-id="5b263-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="5b263-109">Tylko jednostki SQL jest obsługiwana w modelu danych.</span><span class="sxs-lookup"><span data-stu-id="5b263-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="5b263-110">Aby uzyskać więcej informacji, zobacz [QueryView — Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="5b263-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
-   <span data-ttu-id="5b263-111">W przypadku używania EntityClient do zwracania danych tylko do odczytu jednostki jako za pomocą zestawów wierszy <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="5b263-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="5b263-112">Aby uzyskać więcej informacji, zobacz [dostawca EntityClient dla programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="5b263-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="5b263-113">Jeśli jesteś już ekspertem w językach zapytań SQL, SQL jednostki może wydawać się najbardziej fizycznych dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="5b263-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="5b263-114">Z dostawcą EntityClient przy użyciu jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5b263-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="5b263-115">Jeśli chcesz użyć jednostki SQL z dostawcą EntityClient, zobacz następujące tematy, aby uzyskać więcej informacji:</span><span class="sxs-lookup"><span data-stu-id="5b263-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="5b263-116">Dostawca EntityClient dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5b263-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="5b263-117">Instrukcje: Tworzenie ciągu połączenia EntityConnection</span><span class="sxs-lookup"><span data-stu-id="5b263-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="5b263-118">Instrukcje: Wykonywanie zapytania, które zwraca wyniki PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="5b263-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="5b263-119">Instrukcje: Wykonywanie zapytania, które zwraca wyniki StructuralType</span><span class="sxs-lookup"><span data-stu-id="5b263-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="5b263-120">Instrukcje: Wykonywanie zapytania, które zwraca wyniki RefType</span><span class="sxs-lookup"><span data-stu-id="5b263-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="5b263-121">Instrukcje: Wykonywanie zapytania, które zwraca typy złożone</span><span class="sxs-lookup"><span data-stu-id="5b263-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="5b263-122">Instrukcje: Wykonywanie zapytania, które zwraca kolekcje zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="5b263-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="5b263-123">Instrukcje: Wykonywanie zapytania SQL do sparametryzowanej jednostki przy użyciu EntityCommand</span><span class="sxs-lookup"><span data-stu-id="5b263-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="5b263-124">Instrukcje: Wykonywanie zapytania SQL do sparametryzowanej procedury składowanej przy użyciu EntityCommand</span><span class="sxs-lookup"><span data-stu-id="5b263-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="5b263-125">Instrukcje: Wykonywanie zapytania polimorficznego</span><span class="sxs-lookup"><span data-stu-id="5b263-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="5b263-126">Instrukcje: Nawigowanie po relacjach za pomocą operatora nawigowania</span><span class="sxs-lookup"><span data-stu-id="5b263-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="5b263-127">Za pomocą obiektu zapytań przy użyciu jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5b263-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="5b263-128">Jeśli chcesz jednostki SQL za pomocą zapytań dotyczących obiektów, zobacz następujące tematy, aby uzyskać więcej informacji:</span><span class="sxs-lookup"><span data-stu-id="5b263-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="5b263-129">Porady: wykonywanie zapytania, które zwraca obiekty typu jednostki</span><span class="sxs-lookup"><span data-stu-id="5b263-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](https://msdn.microsoft.com/library/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [<span data-ttu-id="5b263-130">Porady: wykonywanie zapytania parametrycznego</span><span class="sxs-lookup"><span data-stu-id="5b263-130">How to: Execute a Parameterized Query</span></span>](https://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [<span data-ttu-id="5b263-131">Porady: nawigowanie po relacjach za pomocą właściwości nawigacji</span><span class="sxs-lookup"><span data-stu-id="5b263-131">How to: Navigate Relationships Using Navigation Properties</span></span>](https://msdn.microsoft.com/library/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [<span data-ttu-id="5b263-132">Porady: wywoływanie funkcji zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="5b263-132">How to: Call a User-Defined Function</span></span>](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [<span data-ttu-id="5b263-133">Porady: filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="5b263-133">How to: Filter Data</span></span>](https://msdn.microsoft.com/library/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [<span data-ttu-id="5b263-134">Porady: sortowanie danych</span><span class="sxs-lookup"><span data-stu-id="5b263-134">How to: Sort Data</span></span>](https://msdn.microsoft.com/library/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [<span data-ttu-id="5b263-135">Porady: grupowanie danych</span><span class="sxs-lookup"><span data-stu-id="5b263-135">How to: Group Data</span></span>](https://msdn.microsoft.com/library/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [<span data-ttu-id="5b263-136">Porady: agregować dane</span><span class="sxs-lookup"><span data-stu-id="5b263-136">How to: Aggregate Data</span></span>](https://msdn.microsoft.com/library/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [<span data-ttu-id="5b263-137">Porady: wykonywanie zapytania, które zwraca obiekty typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="5b263-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](https://msdn.microsoft.com/library/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [<span data-ttu-id="5b263-138">Porady: wykonywanie zapytania, które zwraca kolekcję typów pierwotnych</span><span class="sxs-lookup"><span data-stu-id="5b263-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](https://msdn.microsoft.com/library/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [<span data-ttu-id="5b263-139">Porady: zapytanie powiązane obiekty w obiekt EntityCollection</span><span class="sxs-lookup"><span data-stu-id="5b263-139">How to: Query Related Objects in an EntityCollection</span></span>](https://msdn.microsoft.com/library/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [<span data-ttu-id="5b263-140">Porady: kolejność sumę dwóch zapytań</span><span class="sxs-lookup"><span data-stu-id="5b263-140">How to: Order the Union of Two Queries</span></span>](https://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313)  
  
 [<span data-ttu-id="5b263-141">Porady: wyniki strony za pomocą kwerendy</span><span class="sxs-lookup"><span data-stu-id="5b263-141">How to: Page Through Query Results</span></span>](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a><span data-ttu-id="5b263-142">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5b263-142">In This Section</span></span>  
 [<span data-ttu-id="5b263-143">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5b263-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="5b263-144">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5b263-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="5b263-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b263-145">See Also</span></span>  
 [<span data-ttu-id="5b263-146">Program Entity Framework na platformie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5b263-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [<span data-ttu-id="5b263-147">Dokumentacja języka</span><span class="sxs-lookup"><span data-stu-id="5b263-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
