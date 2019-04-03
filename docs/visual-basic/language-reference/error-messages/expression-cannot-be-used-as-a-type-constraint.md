---
title: Elementu „<expression>” nie można użyć jako ograniczenia typu
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 8dbf510d7c6ee80e2dcd2f9d2552bc870413cbab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838108"
---
# <a name="expression-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="9e392-102">"\<wyrażenia >" nie można użyć jako ograniczenia typu</span><span class="sxs-lookup"><span data-stu-id="9e392-102">'\<expression>' cannot be used as a type constraint</span></span>
<span data-ttu-id="9e392-103">Lista ograniczeń zawiera wyrażenie, które nie stanowi prawidłowe ograniczenie dotyczące parametru typu.</span><span class="sxs-lookup"><span data-stu-id="9e392-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="9e392-104">Lista ograniczeń nakłada się na typ argumentu przekazanego do parametru typu wymagania.</span><span class="sxs-lookup"><span data-stu-id="9e392-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="9e392-105">W dowolnej kombinacji, należy określić następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="9e392-105">You can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="9e392-106">Argument typu musi implementować jeden lub więcej interfejsów</span><span class="sxs-lookup"><span data-stu-id="9e392-106">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="9e392-107">Argument typu musi dziedziczyć z co najwyżej jednej klasy</span><span class="sxs-lookup"><span data-stu-id="9e392-107">The type argument must inherit from at most one class</span></span>  
  
-   <span data-ttu-id="9e392-108">Argument typu musi ujawniać konstruktor bez parametrów, które mogą uzyskiwać dostęp do tworzenia kodu (obejmują `New` ograniczenia)</span><span class="sxs-lookup"><span data-stu-id="9e392-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="9e392-109">Jeśli w lista ograniczeń nie zawiera żadnych konkretną klasę lub interfejs, można skonfigurować bardziej ogólnych wymagań, określając jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="9e392-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
-   <span data-ttu-id="9e392-110">Argument typu musi być typem wartości (obejmują `Structure` ograniczenia)</span><span class="sxs-lookup"><span data-stu-id="9e392-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
-   <span data-ttu-id="9e392-111">Argument typu musi być typem referencyjnym (obejmują `Class` ograniczenia)</span><span class="sxs-lookup"><span data-stu-id="9e392-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="9e392-112">Nie można określić zarówno `Structure` i `Class` dla tego samego typu parametru, a nie można określić jeden więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="9e392-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="9e392-113">**Identyfikator błędu:** BC32061</span><span class="sxs-lookup"><span data-stu-id="9e392-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9e392-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9e392-114">To correct this error</span></span>  
  
-   <span data-ttu-id="9e392-115">Upewnij się, że wyrażenie i jego elementy są poprawne.</span><span class="sxs-lookup"><span data-stu-id="9e392-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
-   <span data-ttu-id="9e392-116">Jeśli wyrażenie nie kwalifikują się do powyższej listy wymagań, należy go usunąć z listy ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="9e392-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
-   <span data-ttu-id="9e392-117">Wyrażenie odwołuje się do interfejsu lub klasy, sprawdź, czy kompilator ma dostęp do tego interfejsu lub klasy.</span><span class="sxs-lookup"><span data-stu-id="9e392-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="9e392-118">Może być konieczne jego nazwy i może być konieczne dodać odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="9e392-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="9e392-119">Aby uzyskać więcej informacji, zobacz "Odwołania do projektów" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="9e392-119">For more information, see "References to Projects" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e392-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e392-120">See also</span></span>

- [<span data-ttu-id="9e392-121">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e392-121">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="9e392-122">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="9e392-122">Value Types and Reference Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="9e392-123">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="9e392-123">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
