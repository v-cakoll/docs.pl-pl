---
title: "Rozpoznanie przeciążenia funkcji (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3a303ca917a9f6cfee42d11456a1f80b52ffd2ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="a0724-102">Rozpoznanie przeciążenia funkcji (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="a0724-102">Function Overload Resolution (Entity SQL)</span></span>
<span data-ttu-id="a0724-103">W tym temacie opisano sposób [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje zostaną rozwiązane.</span><span class="sxs-lookup"><span data-stu-id="a0724-103">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="a0724-104">Tak długo, jak długo mają unikatowe sygnatury można zdefiniować więcej niż jedna funkcja o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="a0724-104">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="a0724-105">W przypadku, należy zastosować następujące kryteria ustalenie funkcji odwołuje się do niego danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a0724-105">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="a0724-106">Te kryteria są stosowane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="a0724-106">These criteria are applied in sequence.</span></span> <span data-ttu-id="a0724-107">Pierwsze kryterium, która ma zastosowanie tylko do jednej funkcji jest funkcją rozwiązane.</span><span class="sxs-lookup"><span data-stu-id="a0724-107">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1.  <span data-ttu-id="a0724-108">**Liczba parametrów**.</span><span class="sxs-lookup"><span data-stu-id="a0724-108">**Parameter number**.</span></span> <span data-ttu-id="a0724-109">Funkcja ma taką samą liczbę parametrów w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="a0724-109">The function has the same number of parameters specified in the expression.</span></span>  
  
2.  <span data-ttu-id="a0724-110">**Dokładnego dopasowania w typie**.</span><span class="sxs-lookup"><span data-stu-id="a0724-110">**Exact match on type**.</span></span> <span data-ttu-id="a0724-111">Każdy typ argumentu funkcji dokładnie zgodny z typem parametru lub jest pusty literał.</span><span class="sxs-lookup"><span data-stu-id="a0724-111">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3.  <span data-ttu-id="a0724-112">**Dopasować podtypu**.</span><span class="sxs-lookup"><span data-stu-id="a0724-112">**Match on subtype**.</span></span> <span data-ttu-id="a0724-113">Każdy typ argumentu funkcji dokładnie odpowiada i jest podtypem typu parametru lub argument jest pusty literał.</span><span class="sxs-lookup"><span data-stu-id="a0724-113">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="a0724-114">W przypadku, gdy kilka funkcji różnią się tylko w wymagana liczba podtyp konwersji, funkcja o najmniejszej Liczba konwersji podtyp jest rozwiązany funkcji.</span><span class="sxs-lookup"><span data-stu-id="a0724-114">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4.  <span data-ttu-id="a0724-115">**Odpowiednik typu lub podtypu podwyższania poziomu**.</span><span class="sxs-lookup"><span data-stu-id="a0724-115">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="a0724-116">Każdy typ argumentu funkcji dokładnie odpowiada, jest podtyp o lub może być podwyższony do typu parametru lub argument jest pusty literał.</span><span class="sxs-lookup"><span data-stu-id="a0724-116">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="a0724-117">Ponownie w zdarzeniu kilka funkcji różnią się jedynie liczby konwersje podtypem i promocjach, funkcja o najmniejszej liczby konwersje podtypem i promocji jest rozwiązany funkcji.</span><span class="sxs-lookup"><span data-stu-id="a0724-117">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="a0724-118">Jeśli żaden z tych kryteriów spowodować jednej funkcji wybierane wyrażenie wywołania funkcji jest niejednoznaczny.</span><span class="sxs-lookup"><span data-stu-id="a0724-118">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="a0724-119">Nawet jeśli stosowanie tych reguł można wyodrębnić jednej funkcji, argumenty nadal mogą być niezgodne parametry.</span><span class="sxs-lookup"><span data-stu-id="a0724-119">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="a0724-120">Błąd w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="a0724-120">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="a0724-121">Funkcje zdefiniowane przez użytkownika definicji wbudowanej funkcji zapytania ma pierwszeństwo, nawet wtedy, gdy istnieje funkcję zdefiniowaną w modelu przy użyciu podpisu lepsze dopasowanie dla funkcji zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a0724-121">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0724-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0724-122">See Also</span></span>  
 [<span data-ttu-id="a0724-123">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="a0724-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="a0724-124">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="a0724-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="a0724-125">Funkcje</span><span class="sxs-lookup"><span data-stu-id="a0724-125">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
