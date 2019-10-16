---
title: Góra (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 16be25336bac386c993eae7527c9377be1073d1e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319275"
---
# <a name="top-entity-sql"></a><span data-ttu-id="e4d81-102">Góra (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e4d81-102">TOP (Entity SQL)</span></span>

<span data-ttu-id="e4d81-103">Klauzula SELECT może mieć opcjonalną podklauzulę TOP, która znajduje się po opcjonalnym modyfikatorze ALL/DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="e4d81-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="e4d81-104">Podklauzula TOP określa, że tylko pierwszy zestaw wierszy zostanie zwrócony z wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="e4d81-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4d81-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4d81-105">Syntax</span></span>

```sql
[ TOP (n) ]
```

## <a name="arguments"></a><span data-ttu-id="e4d81-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e4d81-106">Arguments</span></span>

<span data-ttu-id="e4d81-107">`n` wyrażenie liczbowe określające liczbę wierszy, które mają zostać zwrócone.</span><span class="sxs-lookup"><span data-stu-id="e4d81-107">`n` The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="e4d81-108">`n` może być pojedynczym literałem numerycznym lub pojedynczym parametrem.</span><span class="sxs-lookup"><span data-stu-id="e4d81-108">`n` could be a single numeric literal or a single parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4d81-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4d81-109">Remarks</span></span>

<span data-ttu-id="e4d81-110">Wyrażenie TOP musi być pojedynczym literałem numerycznym lub pojedynczym parametrem.</span><span class="sxs-lookup"><span data-stu-id="e4d81-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="e4d81-111">W przypadku użycia literału stałego typ literału musi być niejawnie awansowany do modelu EDM. Int64 (Byte, Int16, Int32 lub Int64 lub dowolnego typu dostawcy, który jest mapowany do typu, który jest promocyjny do modelu EDM. Int64), a jego wartość musi być większa lub równa zero.</span><span class="sxs-lookup"><span data-stu-id="e4d81-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="e4d81-112">W przeciwnym razie zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e4d81-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="e4d81-113">Jeśli parametr jest używany jako wyrażenie, typ parametru musi również być niejawnie awansowany do EDM. Int64, ale nie będzie można zweryfikować rzeczywistej wartości parametru podczas kompilacji, ponieważ wartości parametrów są opóźnione.</span><span class="sxs-lookup"><span data-stu-id="e4d81-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>

<span data-ttu-id="e4d81-114">Poniżej znajduje się przykład stałego wyrażenia TOP:</span><span class="sxs-lookup"><span data-stu-id="e4d81-114">The following is an example of constant TOP expression:</span></span>

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

<span data-ttu-id="e4d81-115">Poniżej znajduje się przykład sparametryzowanego wyrażenia TOP:</span><span class="sxs-lookup"><span data-stu-id="e4d81-115">The following is an example of parameterized TOP expression:</span></span>

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

<span data-ttu-id="e4d81-116">Góra nie jest deterministyczna, chyba że zapytanie jest sortowane.</span><span class="sxs-lookup"><span data-stu-id="e4d81-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="e4d81-117">Jeśli potrzebujesz deterministycznych wyników, użyj podklauzul [Skip](skip-entity-sql.md) i [Limit](limit-entity-sql.md) w klauzuli [order by](order-by-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="e4d81-117">If you require a deterministic result, use the [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses in the [ORDER BY](order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="e4d81-118">Wartość TOP i SKIP/LIMIT wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="e4d81-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>

## <a name="example"></a><span data-ttu-id="e4d81-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4d81-119">Example</span></span>

<span data-ttu-id="e4d81-120">Poniższe zapytanie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] używa góry, aby określić pierwszy wiersz, który ma zostać zwrócony z wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="e4d81-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="e4d81-121">Zapytanie jest oparte na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e4d81-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e4d81-122">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="e4d81-122">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="e4d81-123">Postępuj zgodnie z procedurą w temacie [How to: Execute a Query zwracającej wyniki StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e4d81-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="e4d81-124">Przekaż następujące zapytanie jako argument do metody `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="e4d81-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

    [!code-sql[DP EntityServices Concepts#TOP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#top)]

## <a name="see-also"></a><span data-ttu-id="e4d81-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4d81-125">See also</span></span>

- [<span data-ttu-id="e4d81-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="e4d81-126">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="e4d81-127">SKIP</span><span class="sxs-lookup"><span data-stu-id="e4d81-127">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="e4d81-128">LIMIT</span><span class="sxs-lookup"><span data-stu-id="e4d81-128">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="e4d81-129">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="e4d81-129">ORDER BY</span></span>](order-by-entity-sql.md)
- [<span data-ttu-id="e4d81-130">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="e4d81-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
