---
title: Metoda dostępu „Get” właściwości „<propertyname>” jest niedostępna
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 8fb78f3c14708c79f1910e202287c25a3b2213b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803054"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="59ad1-102">Metoda dostępu właściwości "get" "\<propertyname >" jest niedostępny</span><span class="sxs-lookup"><span data-stu-id="59ad1-102">'Get' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="59ad1-103">Próbuje pobrać wartość właściwości, gdy nie ma dostępu do właściwości instrukcji `Get` procedury.</span><span class="sxs-lookup"><span data-stu-id="59ad1-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="59ad1-104">Jeśli [instrukcja Get](../../../visual-basic/language-reference/statements/get-statement.md) jest oznaczony przy użyciu bardziej restrykcyjne poziomu niż jego [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md), próba odczytu wartość właściwości może się nie powieść w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="59ad1-104">If the [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="59ad1-105">`Get` Oznaczonej instrukcji [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) i kod wywołujący znajduje się poza klasy lub struktury, w którym właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="59ad1-105">The `Get` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="59ad1-106">`Get` Oznaczonej instrukcji [chronione](../../../visual-basic/language-reference/modifiers/protected.md) i kod wywołujący nie ma w klasy lub struktury, w którym zdefiniowano właściwość ani w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="59ad1-106">The `Get` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="59ad1-107">`Get` Oznaczonej instrukcji [Friend](../../../visual-basic/language-reference/modifiers/friend.md) i kod wywołujący nie jest w tym samym zestawie, w którym właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="59ad1-107">The `Get` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="59ad1-108">**Identyfikator błędu:** BC31103</span><span class="sxs-lookup"><span data-stu-id="59ad1-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="59ad1-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="59ad1-109">To correct this error</span></span>  
  
- <span data-ttu-id="59ad1-110">Jeśli masz kontroli kodu źródłowego, definiując właściwość, należy rozważyć deklarowanie `Get` procedury na tym samym poziomie dostępu jako samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="59ad1-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="59ad1-111">Jeśli nie masz kontroli kodu źródłowego, definiując właściwość lub należy ograniczyć `Get` procedury więcej niż właściwość, spróbuj przenieść instrukcję, która odczytuje wartości właściwości do regionu kod, który ma lepszy dostęp do poziomu dostępu Właściwość.</span><span class="sxs-lookup"><span data-stu-id="59ad1-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ad1-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59ad1-112">See also</span></span>

- [<span data-ttu-id="59ad1-113">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="59ad1-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="59ad1-114">Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="59ad1-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
