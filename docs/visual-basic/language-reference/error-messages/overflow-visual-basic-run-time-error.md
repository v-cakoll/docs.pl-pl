---
title: Przepełnienie (błąd czasu wykonywania w Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 5606ae8188c12142800adef46819791b732ff73c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387273"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="17cc8-102">Przepełnienie (błąd czasu wykonywania w Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17cc8-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="17cc8-103">Przepełnienie wyników podczas próby przypisania, które przekracza limity docelowego przypisania.</span><span class="sxs-lookup"><span data-stu-id="17cc8-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="17cc8-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="17cc8-104">To correct this error</span></span>  
  
1. <span data-ttu-id="17cc8-105">Upewnij się, że wyniki przypisań, obliczeń i konwersji typów danych nie są zbyt duże, aby były reprezentowane w zakresie zmiennych dozwolonych dla tego typu wartości, i przypisz wartość do zmiennej typu, która może zawierać większy zakres wartości, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="17cc8-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2. <span data-ttu-id="17cc8-106">Upewnij się, że przypisania do właściwości mieszczą się w zakresie właściwości, w której zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="17cc8-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3. <span data-ttu-id="17cc8-107">Upewnij się, że liczby używane w obliczeniach, które są przekształcane w liczby całkowite, nie mają wyników większych niż liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="17cc8-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cc8-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17cc8-108">See also</span></span>

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [<span data-ttu-id="17cc8-109">Typy danych</span><span class="sxs-lookup"><span data-stu-id="17cc8-109">Data Types</span></span>](../data-types/index.md)
- [<span data-ttu-id="17cc8-110">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="17cc8-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
