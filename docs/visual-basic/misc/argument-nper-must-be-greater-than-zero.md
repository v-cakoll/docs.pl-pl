---
title: Argument "lokr" musi być większy od zera
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: 0c2cf0f0000de44e1be796bb2de962b45c1d6969
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368065"
---
# <a name="argument-nper-must-be-greater-than-zero"></a><span data-ttu-id="5a754-102">Argument "lokr" musi być większy od zera</span><span class="sxs-lookup"><span data-stu-id="5a754-102">Argument 'NPer' must be greater than zero</span></span>
<span data-ttu-id="5a754-103">`NPer`Funkcja, która zwraca `Double` określenie liczby okresów dla raty rocznej na podstawie okresowych stałych płatności i stałej stopy oprocentowania, wymaga argumentu większego od zera.</span><span class="sxs-lookup"><span data-stu-id="5a754-103">The `NPer` function, which returns a `Double` specifying the number of periods for an annuity based on periodic fixed payments and a fixed interest rate, requires an argument greater than zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5a754-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="5a754-104">To correct this error</span></span>  
  
- <span data-ttu-id="5a754-105">Sprawdź pisownię argumentów w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="5a754-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="5a754-106">Błędnie wpisana nazwa zmiennej może niejawnie utworzyć zmienną numeryczną, która została zainicjowana do zera.</span><span class="sxs-lookup"><span data-stu-id="5a754-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="5a754-107">Sprawdź poprzednie operacje na zmiennych w wyrażeniu, szczególnie te przekazane do procedury jako argumenty z innych procedur.</span><span class="sxs-lookup"><span data-stu-id="5a754-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a754-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a754-108">See also</span></span>

- [<span data-ttu-id="5a754-109">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="5a754-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
