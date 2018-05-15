---
title: Argument &#39;NPer&#39; musi być większa od zera.
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: 5939262d2a58a17d8af88ebc0ba0c7597983e4aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="argument-39nper39-must-be-greater-than-zero"></a><span data-ttu-id="6936b-102">Argument &#39;NPer&#39; musi być większa od zera.</span><span class="sxs-lookup"><span data-stu-id="6936b-102">Argument &#39;NPer&#39; must be greater than zero</span></span>
<span data-ttu-id="6936b-103">`NPer` Funkcji, która zwraca `Double` określającą liczbę okresów renty wieczystej w oparciu o okresowe płatności w stałej kwocie i przy stałej stopie procentowej wymaga argumentu jest większa niż zero.</span><span class="sxs-lookup"><span data-stu-id="6936b-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6936b-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6936b-104">To correct this error</span></span>  
  
-   <span data-ttu-id="6936b-105">Sprawdź pisownię argumentów w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="6936b-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="6936b-106">Nieprawidłowo zapisana nazwa zmiennej może niejawnie utworzyć zmienną liczbową, której wartość jest ustawiana na zero.</span><span class="sxs-lookup"><span data-stu-id="6936b-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
-   <span data-ttu-id="6936b-107">Sprawdź poprzednie operacje na zmiennych w wyrażeniu, zwłaszcza tych, które przekazano do procedury jako argumenty z innych procedur.</span><span class="sxs-lookup"><span data-stu-id="6936b-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6936b-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6936b-108">See Also</span></span>  
 [<span data-ttu-id="6936b-109">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="6936b-109">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
