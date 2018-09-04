---
title: POMIŃ (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 321f6c5ae62ce21249ae4c1081b8e98427bc3df2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500745"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="05256-102">POMIŃ (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="05256-102">SKIP (Entity SQL)</span></span>
<span data-ttu-id="05256-103">Stronicowania fizycznych można wykonać przy użyciu Podklauzula POMIŃ w klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="05256-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="05256-104">POMIŃ nie można użyć oddzielnie od klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="05256-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05256-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="05256-105">Syntax</span></span>  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="05256-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="05256-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="05256-107">Liczba elementów do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="05256-107">The number of items to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05256-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05256-108">Remarks</span></span>  
 <span data-ttu-id="05256-109">Jeśli POMIŃ wyrażenie Podklauzula znajduje się w klauzuli ORDER BY, wyniki będą sortowane według specyfikacji sortowania i zestawu wyników będzie zawierać wiersze, rozpoczynając od następnego wiersza od razu po wyrażeniu SKIP.</span><span class="sxs-lookup"><span data-stu-id="05256-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="05256-110">Na przykład 5 POMIŃ Pomiń pierwsze pięć wierszy i zwraca od szóstego wierszy do przodu.</span><span class="sxs-lookup"><span data-stu-id="05256-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05256-111">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zapytanie jest nieprawidłowe, jeśli modyfikator GÓRNYM i POMIŃ Podklauzula znajdują się w jednym wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="05256-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="05256-112">Zmieniając wyrażenia TOP wyrażenie LIMIT powinien zostać przepisany z zapytania.</span><span class="sxs-lookup"><span data-stu-id="05256-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05256-113">W [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], za pomocą POMIŃ z listą ORDER BY-key kolumn może zwracać nieprawidłowe wyniki.</span><span class="sxs-lookup"><span data-stu-id="05256-113">In [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="05256-114">Więcej niż określoną liczbę wierszy może zostać pominięta, jeżeli kolumnę niebędącą kolumną klucza zawiera zduplikowane dane.</span><span class="sxs-lookup"><span data-stu-id="05256-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="05256-115">Jest to spowodowane jak SKIP jest tłumaczony na [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05256-115">This is due to how SKIP is translated for [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="05256-116">Na przykład w poniższym kodzie więcej niż pięć wierszy może zostać pominięta, jeżeli `E.NonKeyColumn` zawiera zduplikowane wartości:</span><span class="sxs-lookup"><span data-stu-id="05256-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 <span data-ttu-id="05256-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zapytania w [to](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) przykładzie użyto operatora w klauzuli ORDER BY z pominięciem określić kolejność sortowania na obiekty zwrócone w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="05256-117">The  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [this](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) example uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05256-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05256-118">See Also</span></span>  
 [<span data-ttu-id="05256-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="05256-119">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="05256-120">Porady: wyniki strony za pomocą kwerendy</span><span class="sxs-lookup"><span data-stu-id="05256-120">How to: Page Through Query Results</span></span>](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="05256-121">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="05256-121">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="05256-122">TOP</span><span class="sxs-lookup"><span data-stu-id="05256-122">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
