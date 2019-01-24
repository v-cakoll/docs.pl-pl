---
title: Przepełnienie (błąd czasu wykonywania w Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: c45559042231b72ef1ba892cabbead03797df8e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642518"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="85e9c-102">Przepełnienie (błąd czasu wykonywania w Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85e9c-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="85e9c-103">Przepełnienie powoduje podczas próby przypisania przekracza limit przydziału docelowego.</span><span class="sxs-lookup"><span data-stu-id="85e9c-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="85e9c-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="85e9c-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="85e9c-105">Upewnij się, że wyniki typu przypisania, obliczeń i danych konwersje nie są zbyt duże, aby mogły być reprezentowane w ramach zakresu dozwolonych dla tego typu wartości zmiennych i przypisać wartość do zmiennej typu może przechowywać w większym zakresie wartości , jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="85e9c-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="85e9c-106">Upewnij się, że właściwości dopasowana do zakresu właściwości, do którego zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="85e9c-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="85e9c-107">Upewnij się, że numerów używanych w obliczeniach, są zmuszone do liczb całkowitych, które nie mają wyniki większy niż liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="85e9c-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e9c-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85e9c-108">See also</span></span>
- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [<span data-ttu-id="85e9c-109">Typy danych</span><span class="sxs-lookup"><span data-stu-id="85e9c-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="85e9c-110">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="85e9c-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
