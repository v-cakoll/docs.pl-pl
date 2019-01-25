---
title: Jednostki języka SQL
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 0c698f04c3b95ffb204a20d41e91ef3f6210c5d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494103"
---
# <a name="entity-sql-language"></a><span data-ttu-id="1f323-102">Jednostki języka SQL</span><span class="sxs-lookup"><span data-stu-id="1f323-102">Entity SQL Language</span></span>
<span data-ttu-id="1f323-103">Jednostka SQL jest język zapytania niezależnie od magazynu, który jest podobny do bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="1f323-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="1f323-104">Jednostka SQL pozwala przesyłać zapytania dotyczące danych jednostki, jako obiekty lub w formie tabelarycznej.</span><span class="sxs-lookup"><span data-stu-id="1f323-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="1f323-105">Należy rozważyć użycie jednostki SQL w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="1f323-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="1f323-106">Gdy zapytania muszą być dynamicznie skonstruowane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1f323-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="1f323-107">W takim przypadku warto także za pomocą metody konstruktora zapytań z <xref:System.Data.Objects.ObjectQuery%601> zamiast tworzenia SQL jednostki ciągu w czasie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="1f323-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="1f323-108">Jeśli chcesz zdefiniować zapytanie jako część definicji modelu.</span><span class="sxs-lookup"><span data-stu-id="1f323-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="1f323-109">Tylko jednostki SQL jest obsługiwana w modelu danych.</span><span class="sxs-lookup"><span data-stu-id="1f323-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="1f323-110">Aby uzyskać więcej informacji, zobacz [QueryView — Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="1f323-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
-   <span data-ttu-id="1f323-111">W przypadku używania EntityClient do zwracania danych tylko do odczytu jednostki jako za pomocą zestawów wierszy <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="1f323-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="1f323-112">Aby uzyskać więcej informacji, zobacz [dostawca EntityClient dla programu Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="1f323-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="1f323-113">Jeśli jesteś już ekspertem w językach zapytań SQL, SQL jednostki może wydawać się najbardziej fizycznych dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="1f323-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="1f323-114">Z dostawcą EntityClient przy użyciu jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="1f323-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="1f323-115">Jeśli chcesz użyć jednostki SQL z dostawcą EntityClient, zobacz następujące tematy, aby uzyskać więcej informacji:</span><span class="sxs-lookup"><span data-stu-id="1f323-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="1f323-116">Dostawca EntityClient dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="1f323-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="1f323-117">Instrukcje: Tworzenie ciągu połączenia EntityConnection</span><span class="sxs-lookup"><span data-stu-id="1f323-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="1f323-118">Instrukcje: Wykonywanie zapytania, które zwraca wyniki PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="1f323-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="1f323-119">Instrukcje: Wykonywanie zapytania, które zwraca wyniki StructuralType</span><span class="sxs-lookup"><span data-stu-id="1f323-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="1f323-120">Instrukcje: Wykonywanie zapytania, które zwraca wyniki RefType</span><span class="sxs-lookup"><span data-stu-id="1f323-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="1f323-121">Instrukcje: Wykonywanie zapytania, które zwraca typy złożone</span><span class="sxs-lookup"><span data-stu-id="1f323-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="1f323-122">Instrukcje: Wykonywanie zapytania, które zwraca kolekcje zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="1f323-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="1f323-123">Instrukcje: Wykonywanie zapytania SQL sparametryzowanej jednostki przy użyciu EntityCommand</span><span class="sxs-lookup"><span data-stu-id="1f323-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="1f323-124">Instrukcje: Wykonaj procedurę składowaną z parametrami przy użyciu EntityCommand</span><span class="sxs-lookup"><span data-stu-id="1f323-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="1f323-125">Instrukcje: Wykonywanie zapytania Polimorficznego</span><span class="sxs-lookup"><span data-stu-id="1f323-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="1f323-126">Instrukcje: Nawigowanie po relacjach za pomocą operatora nawigowania</span><span class="sxs-lookup"><span data-stu-id="1f323-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="1f323-127">Za pomocą obiektu zapytań przy użyciu jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="1f323-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="1f323-128">Jeśli chcesz jednostki SQL za pomocą zapytań dotyczących obiektów, zobacz następujące tematy, aby uzyskać więcej informacji:</span><span class="sxs-lookup"><span data-stu-id="1f323-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="1f323-129">Instrukcje: Wykonywanie zapytania, które zwraca obiekty typu jednostki</span><span class="sxs-lookup"><span data-stu-id="1f323-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](https://msdn.microsoft.com/library/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [<span data-ttu-id="1f323-130">Instrukcje: Wykonaj zapytanie parametryczne</span><span class="sxs-lookup"><span data-stu-id="1f323-130">How to: Execute a Parameterized Query</span></span>](https://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [<span data-ttu-id="1f323-131">Instrukcje: Nawigowanie po relacjach za pomocą właściwości nawigacji</span><span class="sxs-lookup"><span data-stu-id="1f323-131">How to: Navigate Relationships Using Navigation Properties</span></span>](https://msdn.microsoft.com/library/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [<span data-ttu-id="1f323-132">Instrukcje: Wywoływanie funkcji zdefiniowanej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="1f323-132">How to: Call a User-Defined Function</span></span>](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [<span data-ttu-id="1f323-133">Instrukcje: Filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="1f323-133">How to: Filter Data</span></span>](https://msdn.microsoft.com/library/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [<span data-ttu-id="1f323-134">Instrukcje: Sortowanie danych</span><span class="sxs-lookup"><span data-stu-id="1f323-134">How to: Sort Data</span></span>](https://msdn.microsoft.com/library/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [<span data-ttu-id="1f323-135">Instrukcje: Grupowanie danych</span><span class="sxs-lookup"><span data-stu-id="1f323-135">How to: Group Data</span></span>](https://msdn.microsoft.com/library/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [<span data-ttu-id="1f323-136">Instrukcje: Zagregowane dane</span><span class="sxs-lookup"><span data-stu-id="1f323-136">How to: Aggregate Data</span></span>](https://msdn.microsoft.com/library/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [<span data-ttu-id="1f323-137">Instrukcje: Wykonywanie zapytania, które zwraca obiekty typu anonimowego</span><span class="sxs-lookup"><span data-stu-id="1f323-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](https://msdn.microsoft.com/library/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [<span data-ttu-id="1f323-138">Instrukcje: Wykonywanie zapytania, które zwraca kolekcję typów pierwotnych</span><span class="sxs-lookup"><span data-stu-id="1f323-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](https://msdn.microsoft.com/library/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [<span data-ttu-id="1f323-139">Instrukcje: Zapytanie powiązane obiekty w obiekt EntityCollection</span><span class="sxs-lookup"><span data-stu-id="1f323-139">How to: Query Related Objects in an EntityCollection</span></span>](https://msdn.microsoft.com/library/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [<span data-ttu-id="1f323-140">Instrukcje: Kolejność sumę dwóch zapytań</span><span class="sxs-lookup"><span data-stu-id="1f323-140">How to: Order the Union of Two Queries</span></span>](https://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313)  
  
 [<span data-ttu-id="1f323-141">Instrukcje: Przejrzyj wyniki zapytania</span><span class="sxs-lookup"><span data-stu-id="1f323-141">How to: Page Through Query Results</span></span>](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a><span data-ttu-id="1f323-142">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="1f323-142">In This Section</span></span>  
 [<span data-ttu-id="1f323-143">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="1f323-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="1f323-144">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="1f323-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="1f323-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f323-145">See also</span></span>
- [<span data-ttu-id="1f323-146">Program Entity Framework na platformie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1f323-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)
- [<span data-ttu-id="1f323-147">Dokumentacja języka</span><span class="sxs-lookup"><span data-stu-id="1f323-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
