---
title: POMIŃ (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: b17f73f97d32f151ed4f51b025c0c5a7a97393bb
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904182"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="25bbf-102">POMIŃ (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="25bbf-102">SKIP (Entity SQL)</span></span>
<span data-ttu-id="25bbf-103">Stronicowania fizycznych można wykonać przy użyciu Podklauzula POMIŃ w klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="25bbf-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="25bbf-104">POMIŃ nie można użyć oddzielnie od klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="25bbf-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25bbf-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="25bbf-105">Syntax</span></span>  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="25bbf-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="25bbf-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="25bbf-107">Liczba elementów do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="25bbf-107">The number of items to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25bbf-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25bbf-108">Remarks</span></span>  
 <span data-ttu-id="25bbf-109">Jeśli POMIŃ wyrażenie Podklauzula znajduje się w klauzuli ORDER BY, wyniki będą sortowane według specyfikacji sortowania i zestawu wyników będzie zawierać wiersze, rozpoczynając od następnego wiersza od razu po wyrażeniu SKIP.</span><span class="sxs-lookup"><span data-stu-id="25bbf-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="25bbf-110">Na przykład 5 POMIŃ Pomiń pierwsze pięć wierszy i zwraca od szóstego wierszy do przodu.</span><span class="sxs-lookup"><span data-stu-id="25bbf-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25bbf-111">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zapytanie jest nieprawidłowe, jeśli modyfikator GÓRNYM i POMIŃ Podklauzula znajdują się w jednym wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="25bbf-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="25bbf-112">Zmieniając wyrażenia TOP wyrażenie LIMIT powinien zostać przepisany z zapytania.</span><span class="sxs-lookup"><span data-stu-id="25bbf-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25bbf-113">W [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], za pomocą POMIŃ z listą ORDER BY-key kolumn może zwracać nieprawidłowe wyniki.</span><span class="sxs-lookup"><span data-stu-id="25bbf-113">In [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="25bbf-114">Więcej niż określoną liczbę wierszy może zostać pominięta, jeżeli kolumnę niebędącą kolumną klucza zawiera zduplikowane dane.</span><span class="sxs-lookup"><span data-stu-id="25bbf-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="25bbf-115">Jest to spowodowane jak SKIP jest tłumaczony na [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25bbf-115">This is due to how SKIP is translated for [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="25bbf-116">Na przykład w poniższym kodzie więcej niż pięć wierszy może zostać pominięta, jeżeli `E.NonKeyColumn` zawiera zduplikowane wartości:</span><span class="sxs-lookup"><span data-stu-id="25bbf-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 <span data-ttu-id="25bbf-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zapytania w [jak: Strona za pośrednictwem wyników zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) używa operatora klauzuli ORDER BY z pominięciem, aby określić kolejność sortowania na obiekty zwrócone w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="25bbf-117">The  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25bbf-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25bbf-118">See also</span></span>
- [<span data-ttu-id="25bbf-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="25bbf-119">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- <span data-ttu-id="25bbf-120">[Instrukcje: Przejrzyj wyniki zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="25bbf-120">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="25bbf-121">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="25bbf-121">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)
- [<span data-ttu-id="25bbf-122">TOP</span><span class="sxs-lookup"><span data-stu-id="25bbf-122">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
