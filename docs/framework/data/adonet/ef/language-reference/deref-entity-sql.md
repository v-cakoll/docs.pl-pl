---
title: DEREF (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4e2bbac28e3f0f1149a9fa540692890512fb5941
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="deref-entity-sql"></a><span data-ttu-id="80085-102">DEREF (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="80085-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="80085-103">Wyłuskań wartość odniesienia i daje w wyniku tego usunąć odwołania do.</span><span class="sxs-lookup"><span data-stu-id="80085-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80085-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80085-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="80085-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="80085-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="80085-106">Dowolne wyrażenie prawidłową kwerendę, która zwraca kolekcję.</span><span class="sxs-lookup"><span data-stu-id="80085-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80085-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="80085-107">Return Value</span></span>  
 <span data-ttu-id="80085-108">Wartość jednostek, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="80085-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80085-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="80085-109">Remarks</span></span>  
 <span data-ttu-id="80085-110">DEREF operator wyłuskań wartość odniesienia i daje w wyniku tego usunąć odwołania do.</span><span class="sxs-lookup"><span data-stu-id="80085-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="80085-111">Na przykład jeśli `r` jest odwołaniem do typu ref\<T >, `Deref``(r)` jest wyrażeniem typu `T` który daje jednostki odwołuje się `r`.</span><span class="sxs-lookup"><span data-stu-id="80085-111">For example, if `r` is a reference of type ref\<T>, `Deref``(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="80085-112">Jeśli wartość odwołania ma wartość null lub jest zawieszonego (to znaczy docelowego odwołania nie istnieje), wynik operatora DEREF ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="80085-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80085-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="80085-113">Example</span></span>  
 <span data-ttu-id="80085-114">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa DEREF operator, aby usunąć odwołania do wartości odwołania i usunąć odwołania do wyniku tego produktu.</span><span class="sxs-lookup"><span data-stu-id="80085-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="80085-115">Kwerenda jest oparta na modelu sprzedaży AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="80085-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="80085-116">Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="80085-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="80085-117">Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="80085-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="80085-118">Przekaż następujące zapytanie jako argument do metody ExecutePrimitiveTypeQuery:</span><span class="sxs-lookup"><span data-stu-id="80085-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="80085-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80085-119">See Also</span></span>  
 [<span data-ttu-id="80085-120">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="80085-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="80085-121">REF</span><span class="sxs-lookup"><span data-stu-id="80085-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="80085-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="80085-122">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="80085-123">KEY</span><span class="sxs-lookup"><span data-stu-id="80085-123">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [<span data-ttu-id="80085-124">Typy strukturalne dopuszczające wartości Null</span><span class="sxs-lookup"><span data-stu-id="80085-124">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
