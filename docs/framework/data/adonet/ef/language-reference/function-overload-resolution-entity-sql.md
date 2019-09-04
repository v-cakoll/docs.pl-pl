---
title: Rozwiązanie przeciążenia funkcji (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: 1aeebc501487a6fc443df00c24beb2bc6aa5fc49
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250920"
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="9a188-102">Rozwiązanie przeciążenia funkcji (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9a188-102">Function Overload Resolution (Entity SQL)</span></span>
<span data-ttu-id="9a188-103">W tym temacie opisano [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sposób rozwiązywania funkcji.</span><span class="sxs-lookup"><span data-stu-id="9a188-103">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="9a188-104">Można zdefiniować więcej niż jedną funkcję o tej samej nazwie, o ile funkcje mają unikatowe podpisy.</span><span class="sxs-lookup"><span data-stu-id="9a188-104">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="9a188-105">W takim przypadku należy zastosować następujące kryteria, aby określić, która funkcja jest przywoływana przez dane wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="9a188-105">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="9a188-106">Te kryteria są stosowane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="9a188-106">These criteria are applied in sequence.</span></span> <span data-ttu-id="9a188-107">Pierwsze kryterium stosowane tylko do pojedynczej funkcji jest funkcją rozpoznaną.</span><span class="sxs-lookup"><span data-stu-id="9a188-107">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1. <span data-ttu-id="9a188-108">**Numer parametru**.</span><span class="sxs-lookup"><span data-stu-id="9a188-108">**Parameter number**.</span></span> <span data-ttu-id="9a188-109">Funkcja ma taką samą liczbę parametrów, jak określono w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="9a188-109">The function has the same number of parameters specified in the expression.</span></span>  
  
2. <span data-ttu-id="9a188-110">**Dokładne dopasowanie typu**.</span><span class="sxs-lookup"><span data-stu-id="9a188-110">**Exact match on type**.</span></span> <span data-ttu-id="9a188-111">Każdy typ argumentu funkcji dokładnie pasuje do typu parametru lub jest literałem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="9a188-111">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3. <span data-ttu-id="9a188-112">**Dopasowanie dla podtypu**.</span><span class="sxs-lookup"><span data-stu-id="9a188-112">**Match on subtype**.</span></span> <span data-ttu-id="9a188-113">Każdy typ argumentu funkcji dokładnie pasuje lub jest podtypem typu parametru lub argument jest literałem null.</span><span class="sxs-lookup"><span data-stu-id="9a188-113">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="9a188-114">W przypadku, gdy kilka funkcji różni się tylko w liczbie wymaganych konwersji podtypów, funkcja o najmniejszej liczbie podtypów konwersji jest rozpoznawaną funkcją.</span><span class="sxs-lookup"><span data-stu-id="9a188-114">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4. <span data-ttu-id="9a188-115">**Dopasowanie do podtypu lub podwyższania poziomu**.</span><span class="sxs-lookup"><span data-stu-id="9a188-115">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="9a188-116">Każdy typ argumentu funkcji dokładnie pasuje, jest podtypem lub można podwyższyć poziom do typu parametru lub argument jest literałem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="9a188-116">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="9a188-117">Ponownie w przypadku, gdy kilka funkcji różni się tylko w przypadku konwersji typu podrzędnego i promocji, funkcja o najmniejszej liczbie podtypów konwersji i promocji jest funkcją rozpoznaną.</span><span class="sxs-lookup"><span data-stu-id="9a188-117">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="9a188-118">Jeśli żaden z tych kryteriów nie powoduje wybrania pojedynczej funkcji, wyrażenie wywołania funkcji jest niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="9a188-118">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="9a188-119">Nawet jeśli jedna funkcja może zostać wyodrębniona przy użyciu tych reguł, argumenty nadal mogą być niezgodne z parametrami.</span><span class="sxs-lookup"><span data-stu-id="9a188-119">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="9a188-120">W tym przypadku zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="9a188-120">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="9a188-121">W przypadku funkcji zdefiniowanych przez użytkownika definicja wbudowanej funkcji zapytania ma pierwszeństwo, nawet gdy istnieje funkcja zdefiniowana przez model z podpisem, który jest lepszym dopasowaniem dla funkcji zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9a188-121">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a188-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a188-122">See also</span></span>

- [<span data-ttu-id="9a188-123">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="9a188-123">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="9a188-124">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="9a188-124">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="9a188-125">Funkcje</span><span class="sxs-lookup"><span data-stu-id="9a188-125">Functions</span></span>](functions-entity-sql.md)
