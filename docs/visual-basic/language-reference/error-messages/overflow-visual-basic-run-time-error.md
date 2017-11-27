---
title: "Przepełnienie (błąd czasu wykonywania w Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1908ad576a499e79102aff23e3e2f11d7d99d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="overflow-visual-basic-run-time-error"></a><span data-ttu-id="98e0e-102">Przepełnienie (błąd czasu wykonywania w Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98e0e-102">Overflow (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="98e0e-103">Przepełnienie powoduje przy próbie przypisanie przekracza limity przydziału docelowej.</span><span class="sxs-lookup"><span data-stu-id="98e0e-103">An overflow results when you attempt an assignment that exceeds the limits of the assignment's target.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="98e0e-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="98e0e-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="98e0e-105">Upewnij się, że wyniki przypisania, obliczeń i danych typu konwersje nie są zbyt duże, aby mogły być reprezentowane w ramach zakresu dozwolonych dla tego typu wartości zmiennych i przypisuje wartość do zmiennej typu może przechowywać różnego rodzaju wartości , jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="98e0e-105">Make sure that results of assignments, calculations, and data type conversions are not too large to be represented within the range of variables allowed for that type of value, and assign the value to a variable of a type that can hold a larger range of values, if necessary.</span></span>  
  
2.  <span data-ttu-id="98e0e-106">Upewnij się, że właściwości mieści się zakresie właściwości, do którego zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="98e0e-106">Make sure assignments to properties fit the range of the property to which they are made.</span></span>  
  
3.  <span data-ttu-id="98e0e-107">Upewnij się, że numery używany w obliczeniach, które są przekształcić na liczby całkowite nie jest większy niż liczb całkowitych wyników.</span><span class="sxs-lookup"><span data-stu-id="98e0e-107">Make sure that numbers used in calculations that are coerced into integers do not have results larger than integers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e0e-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98e0e-108">See Also</span></span>  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [<span data-ttu-id="98e0e-109">Typy danych</span><span class="sxs-lookup"><span data-stu-id="98e0e-109">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="98e0e-110">Error — typy</span><span class="sxs-lookup"><span data-stu-id="98e0e-110">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
