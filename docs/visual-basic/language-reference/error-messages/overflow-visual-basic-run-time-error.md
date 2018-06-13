---
title: Przepełnienie (błąd czasu wykonywania w Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 9db79071c4895d49680352bde2d0824a3756d941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594178"
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="969b0-102">Przepełnienie (błąd czasu wykonywania w Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="969b0-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="969b0-103">Przepełnienie powoduje przy próbie przypisanie przekracza limity przydziału docelowej.</span><span class="sxs-lookup"><span data-stu-id="969b0-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="969b0-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="969b0-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="969b0-105">Upewnij się, że wyniki przypisania, obliczeń i danych typu konwersje nie są zbyt duże, aby mogły być reprezentowane w ramach zakresu dozwolonych dla tego typu wartości zmiennych i przypisuje wartość do zmiennej typu może przechowywać różnego rodzaju wartości , jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="969b0-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="969b0-106">Upewnij się, że właściwości mieści się zakresie właściwości, do którego zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="969b0-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="969b0-107">Upewnij się, że numery używany w obliczeniach, które są przekształcić na liczby całkowite nie jest większy niż liczb całkowitych wyników.</span><span class="sxs-lookup"><span data-stu-id="969b0-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="969b0-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="969b0-108">See Also</span></span>  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [<span data-ttu-id="969b0-109">Typy danych</span><span class="sxs-lookup"><span data-stu-id="969b0-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="969b0-110">Typy błędów</span><span class="sxs-lookup"><span data-stu-id="969b0-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
