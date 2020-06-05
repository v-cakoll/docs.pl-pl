---
title: Dzielenie przez zero (błąd czasu wykonywania Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID11
ms.assetid: 5b9bc5d6-792e-48bc-a974-012e07ad95f3
ms.openlocfilehash: 31efe395e17dfc7382abf2478139e1a2d36cc31d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394651"
---
# <a name="division-by-zero-visual-basic-run-time-error"></a><span data-ttu-id="11ab2-102">Dzielenie przez zero (błąd czasu wykonywania Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11ab2-102">Division by zero (Visual Basic Run-Time Error)</span></span>
<span data-ttu-id="11ab2-103">Wyrażenie używane jako dzielnik ma wartość zero.</span><span class="sxs-lookup"><span data-stu-id="11ab2-103">An expression being used as a divisor has a value of zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="11ab2-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="11ab2-104">To correct this error</span></span>  
  
1. <span data-ttu-id="11ab2-105">Sprawdź pisownię zmiennych w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="11ab2-105">Check the spelling of variables in the expression.</span></span> <span data-ttu-id="11ab2-106">Błędnie wpisana nazwa zmiennej może niejawnie utworzyć zmienną numeryczną, która została zainicjowana do zera.</span><span class="sxs-lookup"><span data-stu-id="11ab2-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
2. <span data-ttu-id="11ab2-107">Sprawdź poprzednie operacje na zmiennych w wyrażeniu, szczególnie te przekazane do procedury jako argumenty z innych procedur.</span><span class="sxs-lookup"><span data-stu-id="11ab2-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ab2-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11ab2-108">See also</span></span>

- [<span data-ttu-id="11ab2-109">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="11ab2-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
