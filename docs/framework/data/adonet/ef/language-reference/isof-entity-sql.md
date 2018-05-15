---
title: ISOF (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 7aecb8e2740ffd711278bfd5735c71c2dacf9c3c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="isof-entity-sql"></a><span data-ttu-id="c778f-102">ISOF (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="c778f-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="c778f-103">Określa, czy typ wyrażenia jest określonego typu lub jednego z jego podtypach.</span><span class="sxs-lookup"><span data-stu-id="c778f-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c778f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c778f-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="c778f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c778f-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c778f-106">Dowolne prawidłowe zapytanie wyrażenie można określić typu.</span><span class="sxs-lookup"><span data-stu-id="c778f-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="c778f-107">NIE</span><span class="sxs-lookup"><span data-stu-id="c778f-107">NOT</span></span>  
 <span data-ttu-id="c778f-108">Negacja EDM. Wartość logiczna wynik jest programu.</span><span class="sxs-lookup"><span data-stu-id="c778f-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="c778f-109">TYLKO</span><span class="sxs-lookup"><span data-stu-id="c778f-109">ONLY</span></span>  
 <span data-ttu-id="c778f-110">Określa, że jest z zwraca `true` tylko wtedy, gdy `expression` jest typu `type` i nie wszystkie jednego jego podtypach.</span><span class="sxs-lookup"><span data-stu-id="c778f-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="c778f-111">Typ do testowania `expression` przed.</span><span class="sxs-lookup"><span data-stu-id="c778f-111">The type to test `expression` against.</span></span> <span data-ttu-id="c778f-112">Typ musi być kwalifikowana przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c778f-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c778f-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c778f-113">Return Value</span></span>  
 <span data-ttu-id="c778f-114">`true` Jeśli `expression` jest typu T i T jest typu podstawowego lub typu pochodnego `type`; wartość null, jeśli `expression` wartości null w czasie wykonywania, a w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="c778f-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c778f-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c778f-115">Remarks</span></span>  
 <span data-ttu-id="c778f-116">Wyrażenia `expression IS NOT OF (type)` i `expression IS NOT OF (ONLY type)` składniowo odpowiadające `NOT (expression IS OF (type))` i `NOT (expression IS OF (ONLY type))`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c778f-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="c778f-117">W poniższej tabeli przedstawiono zachowania `IS OF` operator przez niektóre typowe i rogu wzorce.</span><span class="sxs-lookup"><span data-stu-id="c778f-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="c778f-118">Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem pobiera dostawcy:</span><span class="sxs-lookup"><span data-stu-id="c778f-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="c778f-119">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="c778f-119">Pattern</span></span>|<span data-ttu-id="c778f-120">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="c778f-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="c778f-121">wartość null jest typu (EntityType)</span><span class="sxs-lookup"><span data-stu-id="c778f-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="c778f-122">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="c778f-122">Throws</span></span>|  
|<span data-ttu-id="c778f-123">wartość null jest elementów (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="c778f-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="c778f-124">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="c778f-124">Throws</span></span>|  
|<span data-ttu-id="c778f-125">wartość null jest z (RowType)</span><span class="sxs-lookup"><span data-stu-id="c778f-125">null IS OF (RowType)</span></span>|<span data-ttu-id="c778f-126">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="c778f-126">Throws</span></span>|  
|<span data-ttu-id="c778f-127">TRAKTUJ (wartość null dla obiektu AS) jest typu (EntityType)</span><span class="sxs-lookup"><span data-stu-id="c778f-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="c778f-128">Zwraca wartość DBNull</span><span class="sxs-lookup"><span data-stu-id="c778f-128">Returns DBNull</span></span>|  
|<span data-ttu-id="c778f-129">TRAKTUJ (null AS ComplexType) jest elementów (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="c778f-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="c778f-130">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="c778f-130">Throws</span></span>|  
|<span data-ttu-id="c778f-131">TRAKTUJ (null AS RowType) jest z (RowType)</span><span class="sxs-lookup"><span data-stu-id="c778f-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="c778f-132">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="c778f-132">Throws</span></span>|  
|<span data-ttu-id="c778f-133">Obiekt EntityType jest (ENTITYTYPE)</span><span class="sxs-lookup"><span data-stu-id="c778f-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="c778f-134">Zwraca wartość true, false</span><span class="sxs-lookup"><span data-stu-id="c778f-134">Returns true/false</span></span>|  
|<span data-ttu-id="c778f-135">Element ComplexType jest elementów (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="c778f-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="c778f-136">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="c778f-136">Throws</span></span>|  
|<span data-ttu-id="c778f-137">JEST RowType z (RowType)</span><span class="sxs-lookup"><span data-stu-id="c778f-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="c778f-138">Zgłasza wyjątek</span><span class="sxs-lookup"><span data-stu-id="c778f-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c778f-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="c778f-139">Example</span></span>  
 <span data-ttu-id="c778f-140">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania korzysta jest OF — operator można określić typu wyrażenia zapytania, a następnie operator TRAKTUJ można przekonwertować obiektu typu kursu do kolekcji obiektów typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="c778f-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="c778f-141">Zapytanie jest oparta na [modelu służbowe](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span><span class="sxs-lookup"><span data-stu-id="c778f-141">The query is based on the [School Model](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="c778f-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c778f-142">See Also</span></span>  
 [<span data-ttu-id="c778f-143">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="c778f-143">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
