---
title: Metoda dostępu „Set” właściwości „<propertyname>” jest niedostępna
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 077533a5b1fe241b61ded9516ad8f450d7dbbf5e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400347"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="f5e46-102">Metoda dostępu „Set” właściwości „\<propertyname>” jest niedostępna</span><span class="sxs-lookup"><span data-stu-id="f5e46-102">'Set' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="f5e46-103">Instrukcja próbuje zapisać wartość właściwości, gdy nie ma dostępu do `Set` procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="f5e46-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="f5e46-104">Jeśli [instrukcja set](../statements/set-statement.md) jest oznaczona przy użyciu bardziej restrykcyjnego poziomu dostępu niż jego [instrukcja Property](../statements/property-statement.md), próba ustawienia wartości właściwości może zakończyć się niepowodzeniem w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="f5e46-104">If the [Set Statement](../statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="f5e46-105">`Set`Instrukcja jest oznaczona jako [Private](../modifiers/private.md) , a kod wywołujący znajduje się poza klasą lub strukturą, w której właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="f5e46-105">The `Set` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="f5e46-106">`Set`Instrukcja jest oznaczona jako [Protected](../modifiers/protected.md) , a wywoływany kod nie znajduje się w klasie lub strukturze, w której właściwość jest zdefiniowana, ani w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="f5e46-106">The `Set` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="f5e46-107">`Set`Instrukcja jest oznaczona jako [Friend](../modifiers/friend.md) i kod wywołujący nie znajduje się w tym samym zestawie, w którym jest zdefiniowana właściwość.</span><span class="sxs-lookup"><span data-stu-id="f5e46-107">The `Set` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="f5e46-108">**Identyfikator błędu:** BC31102</span><span class="sxs-lookup"><span data-stu-id="f5e46-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f5e46-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f5e46-109">To correct this error</span></span>  
  
- <span data-ttu-id="f5e46-110">Jeśli masz kontrolę nad kodem źródłowym definiującym właściwość, rozważ zadeklarowanie `Set` procedury z takim samym poziomem dostępu jak sama właściwość.</span><span class="sxs-lookup"><span data-stu-id="f5e46-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="f5e46-111">Jeśli nie masz kontroli nad kodem źródłowym definiującym właściwość lub musisz ograniczyć `Set` poziom dostępu do procedury więcej niż sama właściwość, spróbuj przenieść instrukcję, która ustawia wartość właściwości na region kodu, który ma lepszy dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="f5e46-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5e46-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5e46-112">See also</span></span>

- [<span data-ttu-id="f5e46-113">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="f5e46-113">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="f5e46-114">Porady: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="f5e46-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
