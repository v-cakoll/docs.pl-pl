---
title: Rozpoznanie przeciążenia funkcji (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: 0248fdd3f3ba6afb5c7edca740d9aad3ca74bd03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034180"
---
# <a name="function-overload-resolution-entity-sql"></a><span data-ttu-id="4cf6f-102">Rozpoznanie przeciążenia funkcji (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="4cf6f-102">Function Overload Resolution (Entity SQL)</span></span>
<span data-ttu-id="4cf6f-103">W tym temacie opisano sposób [!INCLUDE[esql](../../../../../../includes/esql-md.md)] funkcje zostaną rozwiązane.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-103">This topic describes how [!INCLUDE[esql](../../../../../../includes/esql-md.md)] functions are resolved.</span></span>  
  
 <span data-ttu-id="4cf6f-104">Tak długo, jak funkcje mają unikatowe podpisy, można zdefiniować więcej niż jednej funkcji o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-104">More than one function can be defined with the same name, as long as the functions have unique signatures.</span></span>  
  
 <span data-ttu-id="4cf6f-105">W przypadku następujących kryteriów musi można zastosować w taki sposób, aby ustalić, funkcja, która odwołuje się do podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-105">When this is the case, the following criteria must be applied to determine which function is referenced by a given expression.</span></span> <span data-ttu-id="4cf6f-106">Te kryteria są stosowane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-106">These criteria are applied in sequence.</span></span> <span data-ttu-id="4cf6f-107">Kryterium, która dotyczy tylko jednej funkcji jest funkcją rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-107">The first criterion that applies only to a single function is the resolved function.</span></span>  
  
1. <span data-ttu-id="4cf6f-108">**Liczba parametrów**.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-108">**Parameter number**.</span></span> <span data-ttu-id="4cf6f-109">Funkcja ma taką samą liczbę parametrów określonych w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-109">The function has the same number of parameters specified in the expression.</span></span>  
  
2. <span data-ttu-id="4cf6f-110">**Dokładne dopasowanie typu**.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-110">**Exact match on type**.</span></span> <span data-ttu-id="4cf6f-111">Każdy typ argumentu funkcji dokładnie zgodny z typem parametru lub jest literałem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-111">Each argument type of the function exactly matches the parameter type, or is the null literal.</span></span>  
  
3. <span data-ttu-id="4cf6f-112">**Dopasować wybrany parametr podtypu**.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-112">**Match on subtype**.</span></span> <span data-ttu-id="4cf6f-113">Każdy typ argumentu funkcji dokładnie pasuje do lub jest podtyp typu parametru lub argument jest literał o wartości null.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-113">Each argument type of the function exactly matches or is a sub-type of the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="4cf6f-114">W przypadku, gdy kilka funkcji różnią się tylko w wymagana liczba podtyp konwersji, funkcja o najmniejszej liczby konwersje podtyp jest funkcją rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-114">In the event that several functions differ only in the number of sub-type conversions required, the function with the least number of sub-type conversions is the resolved function.</span></span>  
  
4. <span data-ttu-id="4cf6f-115">**Dopasowanie w promocji typu lub podtypu**.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-115">**Match on subtype or type promotion**.</span></span> <span data-ttu-id="4cf6f-116">Typ każdego argumentu funkcji dokładnie odpowiada, jest typem podrzędne lub może być podwyższony do typu parametru lub argument jest literał o wartości null.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-116">Each argument type of the function exactly matches, is a sub-type of, or can be promoted to the parameter type, or the argument is the null literal.</span></span> <span data-ttu-id="4cf6f-117">Ponownie w zdarzeniu, które kilka funkcji różnią się jedynie liczby konwersje podtyp i promocje, funkcja o najmniejszej liczby konwersje podtyp i promocji jest funkcją rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-117">Again, in the event that several functions differ only in the number of sub-type conversions and promotions, the function with the least number of sub-type conversions and promotions is the resolved function.</span></span>  
  
 <span data-ttu-id="4cf6f-118">Jeśli żadne z tych kryteriów wynik w jednej funkcji jest zaznaczone, wyrażenie wywołania funkcji jest niejednoznaczny.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-118">If none of these criteria result in a single function being selected, the function invocation expression is ambiguous.</span></span>  
  
 <span data-ttu-id="4cf6f-119">Nawet wtedy, gdy przy użyciu tych reguł można wyodrębnić jednej funkcji, argumenty nadal mogą być niezgodne parametry.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-119">Even if a single function can be extracted using these rules, the arguments still might not match the parameters.</span></span> <span data-ttu-id="4cf6f-120">Błąd w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-120">An error is raised in this case.</span></span>  
  
 <span data-ttu-id="4cf6f-121">Funkcje zdefiniowane przez użytkownika definicji wbudowanej funkcji zapytanie ma pierwszeństwo, nawet wtedy, gdy istnieje funkcji definiowanych przez model, za pomocą podpisu, który lepiej pasuje do funkcji zdefiniowanej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4cf6f-121">For user-defined functions, the definition for an inline query function takes precedence even when a model-defined function exists with a signature that is a better match for the user-defined function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf6f-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4cf6f-122">See also</span></span>

- [<span data-ttu-id="4cf6f-123">Odwołanie do jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="4cf6f-123">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="4cf6f-124">Omówienie jednostki SQL</span><span class="sxs-lookup"><span data-stu-id="4cf6f-124">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="4cf6f-125">Funkcje</span><span class="sxs-lookup"><span data-stu-id="4cf6f-125">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
