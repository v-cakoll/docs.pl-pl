---
title: DEREF (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 1ba562ba6542e6ab0d62f1f8348434ae4f4c9b13
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305185"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="3b1d7-102">DEREF (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="3b1d7-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="3b1d7-103">Wyłuskań, wartość odniesienia i generuje wyłuskania wynik tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="3b1d7-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b1d7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b1d7-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="3b1d7-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3b1d7-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3b1d7-106">Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="3b1d7-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b1d7-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3b1d7-107">Return Value</span></span>  
 <span data-ttu-id="3b1d7-108">Wartość jednostki, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="3b1d7-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b1d7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3b1d7-109">Remarks</span></span>  
 <span data-ttu-id="3b1d7-110">DEREF operator wyłuskań, wartość odniesienia i generuje wyłuskania wynik tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="3b1d7-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="3b1d7-111">Na przykład jeśli `r` jest odwołanie do typu ref\<T >, `Deref(r)` to wyrażenie typu `T` , daje jednostek odwołuje się `r`.</span><span class="sxs-lookup"><span data-stu-id="3b1d7-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="3b1d7-112">Jeśli wartość odwołania ma wartość null lub jest delegujące (czyli docelowego odwołania nie istnieje), wynik operatora DEREF ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="3b1d7-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b1d7-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b1d7-113">Example</span></span>  
 <span data-ttu-id="3b1d7-114">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora DEREF próbę wartością odniesienia i wygenerować wyłuskania wynik tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="3b1d7-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="3b1d7-115">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3b1d7-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3b1d7-116">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="3b1d7-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3b1d7-117">Postępuj zgodnie z procedurą w [jak: Wykonywanie zapytania, które zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3b1d7-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="3b1d7-118">Przekaż poniższe zapytanie jako argument do metody ExecutePrimitiveTypeQuery:</span><span class="sxs-lookup"><span data-stu-id="3b1d7-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="3b1d7-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b1d7-119">See also</span></span>

- [<span data-ttu-id="3b1d7-120">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="3b1d7-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="3b1d7-121">REF</span><span class="sxs-lookup"><span data-stu-id="3b1d7-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [<span data-ttu-id="3b1d7-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="3b1d7-122">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [<span data-ttu-id="3b1d7-123">KEY</span><span class="sxs-lookup"><span data-stu-id="3b1d7-123">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [<span data-ttu-id="3b1d7-124">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="3b1d7-124">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
