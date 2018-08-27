---
title: DEREF (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: abe47f8c72abe13bd5c27fe10a412ff94ab861cf
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930015"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="4b8dd-102">DEREF (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="4b8dd-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="4b8dd-103">Wyłuskań, wartość odniesienia i generuje wyłuskania wynik tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4b8dd-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b8dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b8dd-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b8dd-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4b8dd-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4b8dd-106">Dowolne wyrażenie prawidłowe zapytanie, które zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="4b8dd-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b8dd-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4b8dd-107">Return Value</span></span>  
 <span data-ttu-id="4b8dd-108">Wartość jednostki, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="4b8dd-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b8dd-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b8dd-109">Remarks</span></span>  
 <span data-ttu-id="4b8dd-110">DEREF operator wyłuskań, wartość odniesienia i generuje wyłuskania wynik tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4b8dd-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="4b8dd-111">Na przykład jeśli `r` jest odwołanie do typu ref\<T >, `Deref(r)` to wyrażenie typu `T` , daje jednostek odwołuje się `r`.</span><span class="sxs-lookup"><span data-stu-id="4b8dd-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="4b8dd-112">Jeśli wartość odwołania ma wartość null lub jest delegujące (czyli docelowego odwołania nie istnieje), wynik operatora DEREF ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="4b8dd-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b8dd-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b8dd-113">Example</span></span>  
 <span data-ttu-id="4b8dd-114">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora DEREF próbę wartością odniesienia i wygenerować wyłuskania wynik tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4b8dd-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="4b8dd-115">Zapytanie jest oparty na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4b8dd-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4b8dd-116">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="4b8dd-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4b8dd-117">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytania, że zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4b8dd-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="4b8dd-118">Przekaż poniższe zapytanie jako argument do metody ExecutePrimitiveTypeQuery:</span><span class="sxs-lookup"><span data-stu-id="4b8dd-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="4b8dd-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b8dd-119">See Also</span></span>  
 [<span data-ttu-id="4b8dd-120">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="4b8dd-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="4b8dd-121">REF</span><span class="sxs-lookup"><span data-stu-id="4b8dd-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="4b8dd-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="4b8dd-122">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="4b8dd-123">KEY</span><span class="sxs-lookup"><span data-stu-id="4b8dd-123">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="4b8dd-124">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="4b8dd-124">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
