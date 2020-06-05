---
title: Metoda dostępu „Get” właściwości „<propertyname>” jest niedostępna
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: cb953671e624d5b9170aa0b3a9dd80c7ba8337e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402917"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="73c11-102">Metoda dostępu „Get” właściwości „\<propertyname>” jest niedostępna</span><span class="sxs-lookup"><span data-stu-id="73c11-102">'Get' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="73c11-103">Instrukcja próbuje pobrać wartość właściwości, gdy nie ma dostępu do `Get` procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="73c11-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="73c11-104">Jeśli [instrukcja GET](../statements/get-statement.md) jest oznaczona przy użyciu bardziej restrykcyjnego poziomu dostępu niż jego [instrukcja Property](../statements/property-statement.md), próba odczytu wartości właściwości może zakończyć się niepowodzeniem w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="73c11-104">If the [Get Statement](../statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="73c11-105">`Get`Instrukcja jest oznaczona jako [Private](../modifiers/private.md) , a kod wywołujący znajduje się poza klasą lub strukturą, w której właściwość jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="73c11-105">The `Get` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="73c11-106">`Get`Instrukcja jest oznaczona jako [Protected](../modifiers/protected.md) , a wywoływany kod nie znajduje się w klasie lub strukturze, w której właściwość jest zdefiniowana, ani w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="73c11-106">The `Get` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="73c11-107">`Get`Instrukcja jest oznaczona jako [Friend](../modifiers/friend.md) i kod wywołujący nie znajduje się w tym samym zestawie, w którym jest zdefiniowana właściwość.</span><span class="sxs-lookup"><span data-stu-id="73c11-107">The `Get` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="73c11-108">**Identyfikator błędu:** BC31103</span><span class="sxs-lookup"><span data-stu-id="73c11-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="73c11-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="73c11-109">To correct this error</span></span>  
  
- <span data-ttu-id="73c11-110">Jeśli masz kontrolę nad kodem źródłowym definiującym właściwość, rozważ zadeklarowanie `Get` procedury z takim samym poziomem dostępu jak sama właściwość.</span><span class="sxs-lookup"><span data-stu-id="73c11-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="73c11-111">Jeśli nie masz kontroli nad kodem źródłowym definiującym właściwość lub musisz ograniczyć `Get` poziom dostępu do procedury więcej niż sama właściwość, spróbuj przenieść instrukcję, która odczytuje wartość właściwości do regionu kodu, który ma lepszy dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="73c11-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73c11-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73c11-112">See also</span></span>

- [<span data-ttu-id="73c11-113">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="73c11-113">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="73c11-114">Porady: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="73c11-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
