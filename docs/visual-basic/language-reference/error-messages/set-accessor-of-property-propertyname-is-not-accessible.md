---
title: Metoda dostępu „Set” właściwości „<propertyname>” jest niedostępna
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: cf0158692c1154a8a903c893ba287e51c1e34ac8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593270"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="fca1a-102">Ustaw metody dostępu właściwości "\<propertyname >" jest niedostępny</span><span class="sxs-lookup"><span data-stu-id="fca1a-102">'Set' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="fca1a-103">Instrukcję próbuje zapisać wartość właściwości, gdy nie ma dostępu do właściwości `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="fca1a-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="fca1a-104">Jeśli [instrukcji Set](../../../visual-basic/language-reference/statements/set-statement.md) jest oznaczony przy użyciu bardziej restrykcyjne poziomu niż jego [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md), ustawić wartość właściwości może się nie powieść w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="fca1a-104">If the [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="fca1a-105">`Set` Oznaczonej instrukcji [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) i kod wywołujący znajduje się poza klasy lub struktury, w którym właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="fca1a-105">The `Set` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="fca1a-106">`Set` Oznaczonej instrukcji [chronione](../../../visual-basic/language-reference/modifiers/protected.md) i kod wywołujący nie ma w klasy lub struktury, w którym zdefiniowano właściwość ani w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="fca1a-106">The `Set` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="fca1a-107">`Set` Oznaczonej instrukcji [Friend](../../../visual-basic/language-reference/modifiers/friend.md) i kod wywołujący nie jest w tym samym zestawie, w którym właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="fca1a-107">The `Set` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="fca1a-108">**Identyfikator błędu:** BC31102</span><span class="sxs-lookup"><span data-stu-id="fca1a-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fca1a-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="fca1a-109">To correct this error</span></span>  
  
- <span data-ttu-id="fca1a-110">Jeśli masz kontroli kodu źródłowego, definiując właściwość, należy rozważyć deklarowanie `Set` procedury na tym samym poziomie dostępu jako samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="fca1a-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="fca1a-111">Jeśli nie masz kontroli kodu źródłowego, definiując właściwość lub należy ograniczyć `Set` procedury więcej niż właściwość, spróbuj przenieść instrukcję, która ustawia wartości właściwości w regionie kodu, który ma lepszy dostęp do poziomu dostępu Właściwość.</span><span class="sxs-lookup"><span data-stu-id="fca1a-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca1a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fca1a-112">See also</span></span>

- [<span data-ttu-id="fca1a-113">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="fca1a-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="fca1a-114">Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="fca1a-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
