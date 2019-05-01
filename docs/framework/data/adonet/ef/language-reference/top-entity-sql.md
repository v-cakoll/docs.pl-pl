---
title: TOP (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: e7c6cf6b67dc3af29f7ca8fb22af419235a9b833
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879765"
---
# <a name="top-entity-sql"></a><span data-ttu-id="c5b62-102">TOP (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="c5b62-102">TOP (Entity SQL)</span></span>

<span data-ttu-id="c5b62-103">Klauzula SELECT może mieć opcjonalny Podklauzula TOP następujące opcjonalny modyfikator właściwy ALL/DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="c5b62-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="c5b62-104">Podklauzula TOP Określa, że tylko pierwszy zestaw wierszy zostaną zwrócone w wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="c5b62-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>

## <a name="syntax"></a><span data-ttu-id="c5b62-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5b62-105">Syntax</span></span>

```
[ TOP (n) ]
```

## <a name="arguments"></a><span data-ttu-id="c5b62-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c5b62-106">Arguments</span></span>

<span data-ttu-id="c5b62-107">`n` Wyrażenie liczbowe, która określa liczbę wierszy do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="c5b62-107">`n` The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="c5b62-108">`n` może to być literał liczbowy jednego lub jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="c5b62-108">`n` could be a single numeric literal or a single parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5b62-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5b62-109">Remarks</span></span>

<span data-ttu-id="c5b62-110">Najważniejsze wyrażenie musi być literał liczbowy jednego lub jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="c5b62-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="c5b62-111">Jeśli używany jest literałem stałej, typ literału musi być niejawnie Awansowanie do Edm.Int64 (byte, int16, int32 lub int64 lub dowolny typ dostawcy, który mapuje do typu, który jest Awansowanie do Edm.Int64), a jego wartość musi być większa lub równa zero.</span><span class="sxs-lookup"><span data-stu-id="c5b62-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="c5b62-112">W przeciwnym razie zostanie wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c5b62-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="c5b62-113">Jeśli parametr jest używany jako wyrażenia, typ parametru musi być również niejawnie Awansowanie do Edm.Int64, ale nie będzie nie nastąpi sprawdzanie poprawności wartości rzeczywisty parametr podczas kompilacji ponieważ wartości parametrów opóźnienia jest ograniczone.</span><span class="sxs-lookup"><span data-stu-id="c5b62-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>

<span data-ttu-id="c5b62-114">Oto przykład wyrażenie stałe GÓRNY:</span><span class="sxs-lookup"><span data-stu-id="c5b62-114">The following is an example of constant TOP expression:</span></span>

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

<span data-ttu-id="c5b62-115">Oto przykład sparametryzowane wyrażenia TOP:</span><span class="sxs-lookup"><span data-stu-id="c5b62-115">The following is an example of parameterized TOP expression:</span></span>

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

<span data-ttu-id="c5b62-116">Górna jest deterministyczna, chyba że zapytania są sortowane.</span><span class="sxs-lookup"><span data-stu-id="c5b62-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="c5b62-117">Jeśli potrzebujesz deterministyczne wynik, użyj [POMIŃ](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) i [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) podklauzul w [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c5b62-117">If you require a deterministic result, use the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="c5b62-118">TOP i SKIP/LIMIT wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="c5b62-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>

## <a name="example"></a><span data-ttu-id="c5b62-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5b62-119">Example</span></span>

<span data-ttu-id="c5b62-120">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa u góry określić najważniejsze jeden wiersz ma być zwracany z wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="c5b62-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="c5b62-121">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c5b62-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c5b62-122">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="c5b62-122">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="c5b62-123">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="c5b62-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="c5b62-124">Przekaż poniższe zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="c5b62-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

    [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]

## <a name="see-also"></a><span data-ttu-id="c5b62-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5b62-125">See also</span></span>

- [<span data-ttu-id="c5b62-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="c5b62-126">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [<span data-ttu-id="c5b62-127">SKIP</span><span class="sxs-lookup"><span data-stu-id="c5b62-127">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [<span data-ttu-id="c5b62-128">LIMIT</span><span class="sxs-lookup"><span data-stu-id="c5b62-128">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [<span data-ttu-id="c5b62-129">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="c5b62-129">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [<span data-ttu-id="c5b62-130">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c5b62-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
