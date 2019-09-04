---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: 3b746a82f72fc7f42f9d91ddd0a7d6f4f86ac0bb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250574"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="5b679-102">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5b679-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="5b679-103">Określa, czy typ wyrażenia jest określonego typu czy jednego z jego podtypów.</span><span class="sxs-lookup"><span data-stu-id="5b679-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b679-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b679-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="5b679-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5b679-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5b679-106">Dowolne prawidłowe wyrażenie zapytania, aby określić typ.</span><span class="sxs-lookup"><span data-stu-id="5b679-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="5b679-107">NIEMOŻLIWE</span><span class="sxs-lookup"><span data-stu-id="5b679-107">NOT</span></span>  
 <span data-ttu-id="5b679-108">Negacja modelu EDM. Wynik wartości logicznej wynosi.</span><span class="sxs-lookup"><span data-stu-id="5b679-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="5b679-109">JEDYN</span><span class="sxs-lookup"><span data-stu-id="5b679-109">ONLY</span></span>  
 <span data-ttu-id="5b679-110">Określa, że jest zwraca `true` tylko wtedy `expression` , gdy jest `type` typu, a nie dowolnego jednego z jego podtypów.</span><span class="sxs-lookup"><span data-stu-id="5b679-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="5b679-111">Typ do przetestowania `expression` .</span><span class="sxs-lookup"><span data-stu-id="5b679-111">The type to test `expression` against.</span></span> <span data-ttu-id="5b679-112">Typ musi być kwalifikowaną przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="5b679-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b679-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5b679-113">Return Value</span></span>  
 <span data-ttu-id="5b679-114">`true`Jeśli `expression` parametr jest typu T i T jest typem podstawowym lub `type`typem pochodnym; null, jeśli `expression` ma wartość null w czasie wykonywania; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="5b679-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b679-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b679-115">Remarks</span></span>  
 <span data-ttu-id="5b679-116">Wyrażenia `expression IS NOT OF (type)` i `expression IS NOT OF (ONLY type)` są syntaktycznie równoważne z `NOT (expression IS OF (type))` i `NOT (expression IS OF (ONLY type))`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="5b679-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="5b679-117">W poniższej tabeli przedstawiono zachowanie `IS OF` operatora w przypadku niektórych wzorców typowych i narożnych.</span><span class="sxs-lookup"><span data-stu-id="5b679-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="5b679-118">Wszystkie wyjątki są zgłaszane po stronie klienta przed wywołaniem dostawcy:</span><span class="sxs-lookup"><span data-stu-id="5b679-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="5b679-119">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="5b679-119">Pattern</span></span>|<span data-ttu-id="5b679-120">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="5b679-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="5b679-121">wartość zerowa jest typu (EntityType)</span><span class="sxs-lookup"><span data-stu-id="5b679-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="5b679-122">Generuje</span><span class="sxs-lookup"><span data-stu-id="5b679-122">Throws</span></span>|  
|<span data-ttu-id="5b679-123">wartość zerowa jest równa (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="5b679-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="5b679-124">Generuje</span><span class="sxs-lookup"><span data-stu-id="5b679-124">Throws</span></span>|  
|<span data-ttu-id="5b679-125">wartość zerowa jest równa (RowType)</span><span class="sxs-lookup"><span data-stu-id="5b679-125">null IS OF (RowType)</span></span>|<span data-ttu-id="5b679-126">Generuje</span><span class="sxs-lookup"><span data-stu-id="5b679-126">Throws</span></span>|  
|<span data-ttu-id="5b679-127">Traktuj (wartość null jako element EntityType) to (EntityType)</span><span class="sxs-lookup"><span data-stu-id="5b679-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="5b679-128">Zwraca wartość DBNull</span><span class="sxs-lookup"><span data-stu-id="5b679-128">Returns DBNull</span></span>|  
|<span data-ttu-id="5b679-129">Traktuj (wartość null jako ComplexType) to (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="5b679-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="5b679-130">Generuje</span><span class="sxs-lookup"><span data-stu-id="5b679-130">Throws</span></span>|  
|<span data-ttu-id="5b679-131">Traktuj (wartość null AS RowType) to (RowType)</span><span class="sxs-lookup"><span data-stu-id="5b679-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="5b679-132">Generuje</span><span class="sxs-lookup"><span data-stu-id="5b679-132">Throws</span></span>|  
|<span data-ttu-id="5b679-133">Typ EntityType to (EntityType)</span><span class="sxs-lookup"><span data-stu-id="5b679-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="5b679-134">Zwraca wartość PRAWDA/FAŁSZ</span><span class="sxs-lookup"><span data-stu-id="5b679-134">Returns true/false</span></span>|  
|<span data-ttu-id="5b679-135">ComplexType jest typu (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="5b679-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="5b679-136">Generuje</span><span class="sxs-lookup"><span data-stu-id="5b679-136">Throws</span></span>|  
|<span data-ttu-id="5b679-137">RowType jest (RowType)</span><span class="sxs-lookup"><span data-stu-id="5b679-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="5b679-138">Generuje</span><span class="sxs-lookup"><span data-stu-id="5b679-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5b679-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b679-139">Example</span></span>  
 <span data-ttu-id="5b679-140">Następujące [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytanie używa operatora is, aby określić typ wyrażenia zapytania, a następnie używa operatora Traktuj do konwersji obiektu typu kursu do kolekcji obiektów typu OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="5b679-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="5b679-141">Zapytanie jest oparte na [modelu szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5b679-141">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="5b679-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b679-142">See also</span></span>

- [<span data-ttu-id="5b679-143">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="5b679-143">Entity SQL Reference</span></span>](entity-sql-reference.md)
