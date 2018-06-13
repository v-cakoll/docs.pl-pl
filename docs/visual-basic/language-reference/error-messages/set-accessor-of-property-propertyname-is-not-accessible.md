---
title: '&#39;Ustaw&#39; akcesor właściwości &#39; &lt;propertyname&gt; &#39; nie jest dostępny'
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: d047d03755de89d4740482db4845d5db72003ac0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595855"
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="3a34a-102">&#39;Ustaw&#39; akcesor właściwości &#39; &lt;propertyname&gt; &#39; nie jest dostępny</span><span class="sxs-lookup"><span data-stu-id="3a34a-102">&#39;Set&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="3a34a-103">Instrukcja próbuje zapisać wartości właściwości, gdy nie ma dostępu do właściwości `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="3a34a-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="3a34a-104">Jeśli [Instrukcja Set](../../../visual-basic/language-reference/statements/set-statement.md) jest oznaczony atrybutem bardziej restrykcyjnego dostępu niż poziom jego [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md), podjęto próbę ustawienia wartości właściwości może zakończyć się niepowodzeniem w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="3a34a-104">If the [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="3a34a-105">`Set` Instrukcji jest oznaczony jako [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) i kod wywołujący znajduje się poza klasy lub struktury, w którym właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="3a34a-105">The `Set` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="3a34a-106">`Set` Instrukcji jest oznaczony jako [chronione](../../../visual-basic/language-reference/modifiers/protected.md) i kod wywołujący nie w klasy lub struktury, w którym jest zdefiniowana właściwość ani w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="3a34a-106">The `Set` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="3a34a-107">`Set` Instrukcji jest oznaczony jako [Friend](../../../visual-basic/language-reference/modifiers/friend.md) i kod wywołujący nie jest w tym samym zestawie, w którym właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="3a34a-107">The `Set` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="3a34a-108">**Identyfikator błędu:** BC31102</span><span class="sxs-lookup"><span data-stu-id="3a34a-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3a34a-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="3a34a-109">To correct this error</span></span>  
  
-   <span data-ttu-id="3a34a-110">Jeśli masz kontroli kodu źródłowego Definiowanie właściwości, zaleca się zadeklarowanie `Set` procedurę za pomocą tego samego poziomu dostępu, co samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="3a34a-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="3a34a-111">Jeśli nie masz kontroli kodu źródłowego Definiowanie właściwości lub należy ograniczyć `Set` procedury więcej niż właściwość, spróbuj przenieść instrukcji, która ustawia wartości właściwości w regionie kod, który ma lepszy dostęp do poziomu dostępu Właściwość.</span><span class="sxs-lookup"><span data-stu-id="3a34a-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a34a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a34a-112">See Also</span></span>  
 [<span data-ttu-id="3a34a-113">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="3a34a-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="3a34a-114">Instrukcje: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="3a34a-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
