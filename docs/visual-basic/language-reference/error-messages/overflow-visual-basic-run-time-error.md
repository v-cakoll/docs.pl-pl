---
title: Przepełnienie (błąd czasu wykonywania w Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 63223a815e1c4ff8d4e0afbb6c732fff90aad465
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345550"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="20f34-102">Przepełnienie (błąd czasu wykonywania w Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20f34-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="20f34-103">Przepełnienie powoduje podczas próby przypisania przekracza limit przydziału docelowego.</span><span class="sxs-lookup"><span data-stu-id="20f34-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="20f34-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="20f34-104">To correct this error</span></span>  
  
1. <span data-ttu-id="20f34-105">Upewnij się, że wyniki typu przypisania, obliczeń i danych konwersje nie są zbyt duże, aby mogły być reprezentowane w ramach zakresu dozwolonych dla tego typu wartości zmiennych i przypisać wartość do zmiennej typu może przechowywać w większym zakresie wartości , jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="20f34-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2. <span data-ttu-id="20f34-106">Upewnij się, że właściwości dopasowana do zakresu właściwości, do którego zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="20f34-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3. <span data-ttu-id="20f34-107">Upewnij się, że numerów używanych w obliczeniach, są zmuszone do liczb całkowitych, które nie mają wyniki większy niż liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="20f34-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20f34-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20f34-108">See also</span></span>

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [<span data-ttu-id="20f34-109">Typy danych</span><span class="sxs-lookup"><span data-stu-id="20f34-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="20f34-110">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="20f34-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
