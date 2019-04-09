---
title: Literały null i wnioskowanie o typie (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 22b548f2fc889b20f76a41001438f75c25f99c00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118095"
---
# <a name="null-literals-and-type-inference-entity-sql"></a><span data-ttu-id="f4650-102">Literały null i wnioskowanie o typie (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="f4650-102">Null Literals and Type Inference (Entity SQL)</span></span>
<span data-ttu-id="f4650-103">Literały null są zgodne z żadnym typem w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] system typów.</span><span class="sxs-lookup"><span data-stu-id="f4650-103">Null literals are compatible with any type in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] type system.</span></span> <span data-ttu-id="f4650-104">Jednak w przypadku typu literałem o wartości null, aby był wywnioskowany poprawnie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nakłada pewne ograniczenia dotyczące użycia właściwość literal o wartości null.</span><span class="sxs-lookup"><span data-stu-id="f4650-104">However, for the type of a null literal to be inferred correctly, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] imposes certain constraints on where a null literal can be used.</span></span>  
  
## <a name="typed-nulls"></a><span data-ttu-id="f4650-105">Wpisane wartości null</span><span class="sxs-lookup"><span data-stu-id="f4650-105">Typed Nulls</span></span>  
 <span data-ttu-id="f4650-106">Wpisane wartości null może służyć w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="f4650-106">Typed nulls can be used anywhere.</span></span> <span data-ttu-id="f4650-107">Wnioskowanie o typie nie jest wymagana dla wpisane wartości null, ponieważ typ jest znany.</span><span class="sxs-lookup"><span data-stu-id="f4650-107">Type inference is not required for typed nulls because the type is known.</span></span> <span data-ttu-id="f4650-108">Na przykład można utworzyć wartości null typu Int16 następującym kodem [!INCLUDE[esql](../../../../../../includes/esql-md.md)] konstruowania:</span><span class="sxs-lookup"><span data-stu-id="f4650-108">For example, you can construct a null of type Int16 with the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] construct:</span></span>  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a><span data-ttu-id="f4650-109">Swobodny literały Null</span><span class="sxs-lookup"><span data-stu-id="f4650-109">Free-Floating Null Literals</span></span>  
 <span data-ttu-id="f4650-110">Swobodny literały null może służyć w następujących okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="f4650-110">Free-floating null literals can be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="f4650-111">Jako argument do RZUTOWANIA lub TRAKTUJ wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f4650-111">As an argument to a CAST or TREAT expression.</span></span> <span data-ttu-id="f4650-112">Jest to zalecany sposób tworzenia wpisane wyrażenie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="f4650-112">This is the recommended way to produce a typed null expression.</span></span>  
  
-   <span data-ttu-id="f4650-113">Jako argument do metody lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="f4650-113">As an argument to a method or a function.</span></span> <span data-ttu-id="f4650-114">Przeciążenie standardowe reguły mają zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="f4650-114">Standard overload rules apply.</span></span>  
  
-   <span data-ttu-id="f4650-115">Jako jeden z argumentów do wyrażenia arytmetyczne, takie jak +, -, lub /.</span><span class="sxs-lookup"><span data-stu-id="f4650-115">As one of the arguments to an arithmetic expression such as +, -, or /.</span></span> <span data-ttu-id="f4650-116">Drugi argument nie może być literały null, w przeciwnym razie wnioskowanie typu zerowalnego nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="f4650-116">The other arguments cannot be null literals, otherwise type inference is not possible.</span></span>  
  
-   <span data-ttu-id="f4650-117">Jako argumenty, które mają wyrażenie logiczne (AND, OR lub nie).</span><span class="sxs-lookup"><span data-stu-id="f4650-117">As any of the arguments to a logical expression (AND, OR, or NOT).</span></span> <span data-ttu-id="f4650-118">Wszystkie argumenty są znane jako typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="f4650-118">All the arguments are known to be of type Boolean.</span></span>  
  
-   <span data-ttu-id="f4650-119">Jako argument wyrażenia jest wartość NULL lub nie jest równa NULL.</span><span class="sxs-lookup"><span data-stu-id="f4650-119">As the argument to an IS NULL or IS NOT NULL expression.</span></span>  
  
-   <span data-ttu-id="f4650-120">Jako co najmniej jeden z argumentów do wyrażenia LIKE.</span><span class="sxs-lookup"><span data-stu-id="f4650-120">As one or more of the arguments to a LIKE expression.</span></span> <span data-ttu-id="f4650-121">Wszystkie argumenty powinny być ciągami.</span><span class="sxs-lookup"><span data-stu-id="f4650-121">All arguments are expected to be strings.</span></span>  
  
-   <span data-ttu-id="f4650-122">Jako jeden lub więcej argumentów konstruktora typu o nazwie.</span><span class="sxs-lookup"><span data-stu-id="f4650-122">As one or more of the arguments to a named-type constructor.</span></span>  
  
-   <span data-ttu-id="f4650-123">Jako jeden lub więcej argumentów Konstruktor multiset.</span><span class="sxs-lookup"><span data-stu-id="f4650-123">As one or more of the arguments to a multiset constructor.</span></span> <span data-ttu-id="f4650-124">Co najmniej jeden argument Pro Konstruktor multiset — musi być wyrażeniem, które nie jest literałem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="f4650-124">At least one argument to the multiset constructor must be an expression that is not a null literal.</span></span>  
  
-   <span data-ttu-id="f4650-125">Ponieważ co najmniej jedno z wyrażeń w wyrażeniu CASE następnie albo też.</span><span class="sxs-lookup"><span data-stu-id="f4650-125">As one or more of the THEN or ELSE expressions in a CASE expression.</span></span> <span data-ttu-id="f4650-126">Co najmniej jedno z wyrażeń w wyrażeniu CASE następnie albo też musi być wyrażeniem innym niż literałem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="f4650-126">At least one of the THEN or ELSE expressions in the CASE expression must be an expression other than a null literal.</span></span>  
  
 <span data-ttu-id="f4650-127">Swobodny literały null nie można używać w innych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="f4650-127">Free-floating null literals cannot be used in other scenarios.</span></span> <span data-ttu-id="f4650-128">Na przykład nie mogą być używane jako argumenty konstruktorze wierszy.</span><span class="sxs-lookup"><span data-stu-id="f4650-128">For example,  they cannot be used as arguments to a row constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4650-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4650-129">See also</span></span>

- [<span data-ttu-id="f4650-130">Przegląd języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f4650-130">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
