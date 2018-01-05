---
title: "POMIŃ (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 28f774b8d8bb232512fb975d292df4423f56a6d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="skip-entity-sql"></a><span data-ttu-id="c9064-102">POMIŃ (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="c9064-102">SKIP (Entity SQL)</span></span>
<span data-ttu-id="c9064-103">Stronicowanie fizycznych można wykonać za pomocą klauzul podrzędnych SKIP w klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="c9064-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="c9064-104">POMIŃ nie można używać osobno z klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="c9064-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9064-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9064-105">Syntax</span></span>  
  
```  
[ SKIP n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c9064-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c9064-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="c9064-107">Liczba elementów do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="c9064-107">The number of items to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9064-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9064-108">Remarks</span></span>  
 <span data-ttu-id="c9064-109">Jeśli klauzul podrzędnych SKIP w wyrażeniu znajduje się w klauzuli ORDER BY, będzie można posortować wyników według specyfikacji sortowania i zestaw wyników zawiera wiersze, zaczynając od następnego wiersza od razu po wyrażeniu SKIP.</span><span class="sxs-lookup"><span data-stu-id="c9064-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="c9064-110">Na przykład 5 POMIŃ Pomiń pierwsze pięć wiersze i zwrócenia z wiersza szóstego do przodu.</span><span class="sxs-lookup"><span data-stu-id="c9064-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9064-111">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zapytanie jest nieprawidłowe, jeśli zarówno modyfikator TOP, jak i klauzul podrzędnych SKIP znajdują się w jednym wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="c9064-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="c9064-112">Zapytanie powinno ulegną zmieniając wyrażenia TOP w wyrażeniu LIMIT.</span><span class="sxs-lookup"><span data-stu-id="c9064-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9064-113">W [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], za pomocą POMIŃ z listą ORDER BY na niekluczowe może zwracać niepoprawne wyniki.</span><span class="sxs-lookup"><span data-stu-id="c9064-113">In [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)], using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="c9064-114">Więcej niż określoną liczbę wierszy mogły zostać pominięte, jeśli kolumna klucza ma zduplikowane dane w nim.</span><span class="sxs-lookup"><span data-stu-id="c9064-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="c9064-115">Jest to spowodowane jak SKIP jest translacja dla [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9064-115">This is due to how SKIP is translated for [!INCLUDE[ssVersion2000](../../../../../../includes/ssversion2000-md.md)].</span></span> <span data-ttu-id="c9064-116">Na przykład w poniższym kodzie więcej niż pięć wierszy mogły zostać pominięte Jeśli `E.NonKeyColumn` zawiera zduplikowane wartości:</span><span class="sxs-lookup"><span data-stu-id="c9064-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>  
>   
>  `SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L`  
  
 <span data-ttu-id="c9064-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Zapytania w [to](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) przykładzie użyto operatora ORDER BY z pominięciem można określić kolejność sortowania użyć obiektów zwracanych w instrukcji SELECT.</span><span class="sxs-lookup"><span data-stu-id="c9064-117">The  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [this](https://msdn.microsoft.com/library/bb738702\(v=vs.100\).aspx#_ESQL) example uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9064-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9064-118">See Also</span></span>  
 [<span data-ttu-id="c9064-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="c9064-119">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="c9064-120">Porady: powoduje strony za pomocą kwerendy</span><span class="sxs-lookup"><span data-stu-id="c9064-120">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="c9064-121">Stronicowanie</span><span class="sxs-lookup"><span data-stu-id="c9064-121">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="c9064-122">TOP</span><span class="sxs-lookup"><span data-stu-id="c9064-122">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
