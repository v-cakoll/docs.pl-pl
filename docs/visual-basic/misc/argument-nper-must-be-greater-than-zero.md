---
title: Argument "NPer" musi być większa niż zero
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: 43f700c28d5ffce8dc8b33651ce69493d9742272
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64659084"
---
# <a name="argument-nper-must-be-greater-than-zero"></a><span data-ttu-id="a6283-102">Argument "NPer" musi być większa niż zero</span><span class="sxs-lookup"><span data-stu-id="a6283-102">Argument 'NPer' must be greater than zero</span></span>
<span data-ttu-id="a6283-103">`NPer` Funkcji, która zwraca `Double` określającą liczbę okresów renty w oparciu o okresowe płatności w stałej kwocie i stałej stopie wymaga argumentu większą niż zero.</span><span class="sxs-lookup"><span data-stu-id="a6283-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a6283-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a6283-104">To correct this error</span></span>  
  
- <span data-ttu-id="a6283-105">Sprawdź pisownię argumentów w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="a6283-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="a6283-106">Nieprawidłowo zapisana nazwa zmiennej może niejawnie utworzyć zmienną liczbową, której wartość jest ustawiana na zero.</span><span class="sxs-lookup"><span data-stu-id="a6283-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="a6283-107">Sprawdź poprzednie operacje na zmiennych w wyrażeniu, zwłaszcza tych, które przekazano do procedury jako argumenty z innych procedur.</span><span class="sxs-lookup"><span data-stu-id="a6283-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6283-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6283-108">See also</span></span>

- [<span data-ttu-id="a6283-109">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="a6283-109">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
