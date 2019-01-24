---
title: '&#39;Ustaw&#39; metody dostępu właściwości &#39; &lt;propertyname&gt; &#39; jest niedostępny'
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: a543506b06742f3ee9101edbac962e761ddd531d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606572"
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="dd5f5-102">&#39;Ustaw&#39; metody dostępu właściwości &#39; &lt;propertyname&gt; &#39; jest niedostępny</span><span class="sxs-lookup"><span data-stu-id="dd5f5-102">&#39;Set&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="dd5f5-103">Instrukcję próbuje zapisać wartość właściwości, gdy nie ma dostępu do właściwości `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="dd5f5-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="dd5f5-104">Jeśli [instrukcji Set](../../../visual-basic/language-reference/statements/set-statement.md) jest oznaczony przy użyciu bardziej restrykcyjne poziomu niż jego [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md), ustawić wartość właściwości może się nie powieść w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="dd5f5-104">If the [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="dd5f5-105">`Set` Oznaczonej instrukcji [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) i kod wywołujący znajduje się poza klasy lub struktury, w którym właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="dd5f5-105">The `Set` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="dd5f5-106">`Set` Oznaczonej instrukcji [chronione](../../../visual-basic/language-reference/modifiers/protected.md) i kod wywołujący nie ma w klasy lub struktury, w którym zdefiniowano właściwość ani w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="dd5f5-106">The `Set` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="dd5f5-107">`Set` Oznaczonej instrukcji [Friend](../../../visual-basic/language-reference/modifiers/friend.md) i kod wywołujący nie jest w tym samym zestawie, w którym właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="dd5f5-107">The `Set` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="dd5f5-108">**Identyfikator błędu:** BC31102</span><span class="sxs-lookup"><span data-stu-id="dd5f5-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dd5f5-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="dd5f5-109">To correct this error</span></span>  
  
-   <span data-ttu-id="dd5f5-110">Jeśli masz kontroli kodu źródłowego, definiując właściwość, należy rozważyć deklarowanie `Set` procedury na tym samym poziomie dostępu jako samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd5f5-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="dd5f5-111">Jeśli nie masz kontroli kodu źródłowego, definiując właściwość lub należy ograniczyć `Set` procedury więcej niż właściwość, spróbuj przenieść instrukcję, która ustawia wartości właściwości w regionie kodu, który ma lepszy dostęp do poziomu dostępu Właściwość.</span><span class="sxs-lookup"><span data-stu-id="dd5f5-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd5f5-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd5f5-112">See also</span></span>
- [<span data-ttu-id="dd5f5-113">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="dd5f5-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="dd5f5-114">Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="dd5f5-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
