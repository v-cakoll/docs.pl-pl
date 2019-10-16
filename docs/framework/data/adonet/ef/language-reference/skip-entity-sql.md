---
title: Pomiń (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 75140384823588b8f6785de00b0ab3cd17314a3f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319342"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="4cfea-102">Pomiń (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4cfea-102">SKIP (Entity SQL)</span></span>

<span data-ttu-id="4cfea-103">Stronicowanie fizyczne można wykonać za pomocą podklauzuli SKIP w klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="4cfea-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="4cfea-104">Pomiń nie można użyć niezależnie od klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="4cfea-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>

## <a name="syntax"></a><span data-ttu-id="4cfea-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4cfea-105">Syntax</span></span>

```sql
[ SKIP n ]
```

## <a name="arguments"></a><span data-ttu-id="4cfea-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4cfea-106">Arguments</span></span>

`n` \
<span data-ttu-id="4cfea-107">Liczba elementów do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="4cfea-107">The number of items to skip.</span></span>

## <a name="remarks"></a><span data-ttu-id="4cfea-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4cfea-108">Remarks</span></span>

<span data-ttu-id="4cfea-109">Jeśli Podklauzula SKIP Expression jest obecna w klauzuli ORDER BY, wyniki zostaną posortowane zgodnie z specyfikacją sortowania, a zestaw wyników będzie zawierał wiersze zaczynające się od następnego wiersza bezpośrednio po wyrażeniu SKIP.</span><span class="sxs-lookup"><span data-stu-id="4cfea-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="4cfea-110">Na przykład Pomiń 5 spowoduje pominięcie pierwszych pięciu wierszy i zwrócenie od szóstego wiersza do przodu.</span><span class="sxs-lookup"><span data-stu-id="4cfea-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>

> [!NOTE]
> <span data-ttu-id="4cfea-111">Zapytanie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest nieprawidłowe, jeśli zarówno modyfikator GÓRNy, jak i podklauzulę SKIP są obecne w tym samym wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="4cfea-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="4cfea-112">Zapytanie powinno zostać napisaną przez zmianę wyrażenia TOP na wyrażenie limitu.</span><span class="sxs-lookup"><span data-stu-id="4cfea-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>

> [!NOTE]
> <span data-ttu-id="4cfea-113">W SQL Server 2000 użycie polecenia Pomiń z KOLEJNOŚCIą według kolumn niebędących kluczami może spowodować zwrócenie niepoprawnych wyników.</span><span class="sxs-lookup"><span data-stu-id="4cfea-113">In SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="4cfea-114">Jeśli kolumna niebędąca kluczem zawiera zduplikowane dane, może zostać pominięta więcej niż określona liczba wierszy.</span><span class="sxs-lookup"><span data-stu-id="4cfea-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="4cfea-115">Wynika to z tego, jak POMIJAnie jest tłumaczone dla SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="4cfea-115">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="4cfea-116">Na przykład, w poniższym kodzie można pominąć więcej niż pięć wierszy, jeśli `E.NonKeyColumn` ma zduplikowane wartości:</span><span class="sxs-lookup"><span data-stu-id="4cfea-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>
>
> ```sql
> SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L
> ```

<span data-ttu-id="4cfea-117">Zapytanie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] w [instrukcje: Strona za pośrednictwem wyników zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) używa operatora order by z opcją Skip, aby określić kolejność sortowania używaną dla obiektów zwracanych w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="4cfea-117">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="4cfea-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4cfea-118">See also</span></span>

- [<span data-ttu-id="4cfea-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="4cfea-119">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="4cfea-120">[Instrukcje: Strona za poorednictwem wyników zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4cfea-120">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="4cfea-121">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="4cfea-121">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="4cfea-122">TOP</span><span class="sxs-lookup"><span data-stu-id="4cfea-122">TOP</span></span>](top-entity-sql.md)
