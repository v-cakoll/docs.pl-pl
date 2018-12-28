---
title: Argument "NPer" musi być większa niż zero
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: 86bbf892997ee512b6042ef400e2485edabe731d
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2018
ms.locfileid: "53773487"
---
# <a name="argument-nper-must-be-greater-than-zero"></a><span data-ttu-id="62e76-102">Argument "NPer" musi być większa niż zero</span><span class="sxs-lookup"><span data-stu-id="62e76-102">Argument 'NPer' must be greater than zero</span></span>
<span data-ttu-id="62e76-103">`NPer` Funkcji, która zwraca `Double` określającą liczbę okresów renty w oparciu o okresowe płatności w stałej kwocie i stałej stopie wymaga argumentu większą niż zero.</span><span class="sxs-lookup"><span data-stu-id="62e76-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="62e76-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="62e76-104">To correct this error</span></span>  
  
-   <span data-ttu-id="62e76-105">Sprawdź pisownię argumentów w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="62e76-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="62e76-106">Nieprawidłowo zapisana nazwa zmiennej może niejawnie utworzyć zmienną liczbową, której wartość jest ustawiana na zero.</span><span class="sxs-lookup"><span data-stu-id="62e76-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
-   <span data-ttu-id="62e76-107">Sprawdź poprzednie operacje na zmiennych w wyrażeniu, zwłaszcza tych, które przekazano do procedury jako argumenty z innych procedur.</span><span class="sxs-lookup"><span data-stu-id="62e76-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e76-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62e76-108">See Also</span></span>  
 [<span data-ttu-id="62e76-109">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="62e76-109">Passing Arguments by Value and by Reference</span></span>](../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
