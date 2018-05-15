---
title: '&#39;&lt;wyrażenie&gt; &#39; nie można użyć jako ograniczenia typu'
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: 8e9aad2ec65e037b15e19ca2e624fdc8f28bc94e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="f5097-102">&#39;&lt;wyrażenie&gt; &#39; nie można użyć jako ograniczenia typu</span><span class="sxs-lookup"><span data-stu-id="f5097-102">&#39;&lt;expression&gt;&#39; cannot be used as a type constraint</span></span>
<span data-ttu-id="f5097-103">Lista ograniczeń zawiera wyrażenie, które nie stanowi prawidłowe ograniczenie parametru typu.</span><span class="sxs-lookup"><span data-stu-id="f5097-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="f5097-104">Lista ograniczeń nakłada wymagań dotyczących typu argumentu przekazanego do parametru typu.</span><span class="sxs-lookup"><span data-stu-id="f5097-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="f5097-105">W dowolnej kombinacji można określić następujące wymagania:</span><span class="sxs-lookup"><span data-stu-id="f5097-105">You can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="f5097-106">Argument typu musi implementować jeden lub więcej interfejsów</span><span class="sxs-lookup"><span data-stu-id="f5097-106">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="f5097-107">Argument typu musi dziedziczyć po co najwyżej jedną klasę</span><span class="sxs-lookup"><span data-stu-id="f5097-107">The type argument must inherit from at most one class</span></span>  
  
-   <span data-ttu-id="f5097-108">Argument typu musi ujawniać konstruktor bez parametrów, dostępnym dla tworzenia kodu (obejmują `New` ograniczenia)</span><span class="sxs-lookup"><span data-stu-id="f5097-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="f5097-109">Jeśli na liście ograniczeń nie zostanie uwzględniony określonej klasy lub interfejsu, można skonfigurować więcej ogólnych wymagań, określając jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f5097-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
-   <span data-ttu-id="f5097-110">Argument typu musi być typem wartości (obejmują `Structure` ograniczenia)</span><span class="sxs-lookup"><span data-stu-id="f5097-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
-   <span data-ttu-id="f5097-111">Argument typu musi być typu odwołania (obejmują `Class` ograniczenia)</span><span class="sxs-lookup"><span data-stu-id="f5097-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="f5097-112">Nie można określić zarówno `Structure` i `Class` dla tego samego typu parametru, a nie można określić jedną więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="f5097-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="f5097-113">**Identyfikator błędu:** BC32061</span><span class="sxs-lookup"><span data-stu-id="f5097-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f5097-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f5097-114">To correct this error</span></span>  
  
-   <span data-ttu-id="f5097-115">Upewnij się, że wyrażenie i jej elementy są poprawne.</span><span class="sxs-lookup"><span data-stu-id="f5097-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
-   <span data-ttu-id="f5097-116">Jeśli wyrażenie nie kwalifikuje się do poprzedniego listę wymagań, należy go usunąć z listy ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="f5097-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
-   <span data-ttu-id="f5097-117">Wyrażenie odwołuje się do interfejsu lub klasa, sprawdź, czy kompilator ma dostęp do tego interfejsu lub klasy.</span><span class="sxs-lookup"><span data-stu-id="f5097-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="f5097-118">Może być konieczne jego nazwy, a czasami trzeba dodać odwołanie do projektu.</span><span class="sxs-lookup"><span data-stu-id="f5097-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="f5097-119">Aby uzyskać więcej informacji, zobacz "Odwołań do projektów" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="f5097-119">For more information, see "References to Projects" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5097-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5097-120">See Also</span></span>  
 [<span data-ttu-id="f5097-121">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f5097-121">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="f5097-122">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="f5097-122">Value Types and Reference Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="f5097-123">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="f5097-123">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 
