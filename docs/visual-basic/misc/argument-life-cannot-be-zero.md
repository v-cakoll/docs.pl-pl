---
title: Argument "czas_życia" nie może mieć wartości zero
ms.date: 07/20/2015
f1_keywords:
- vbrFinancial_LifeNEZero
ms.assetid: c402da97-a2b2-4219-a83a-0cebbfdffef2
ms.openlocfilehash: a737afb8901382d75c3858f84be1b2359338b057
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368169"
---
# <a name="argument-life-cannot-be-zero"></a><span data-ttu-id="6e7b2-102">Argument "czas_życia" nie może mieć wartości zero</span><span class="sxs-lookup"><span data-stu-id="6e7b2-102">Argument 'Life' cannot be zero</span></span>
<span data-ttu-id="6e7b2-103">Argument dla `Life` , który musi mieć wartość określającą `Double` Długość użytecznego okresu istnienia elementu zawartości, jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="6e7b2-103">An argument for `Life`, which must be a `Double` that specifies the length of useful life of the asset, is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6e7b2-104">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6e7b2-104">To correct this error</span></span>  
  
- <span data-ttu-id="6e7b2-105">Sprawdź pisownię argumentów w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="6e7b2-105">Check the spelling of arguments in the expression.</span></span> <span data-ttu-id="6e7b2-106">Błędnie wpisana nazwa zmiennej może niejawnie utworzyć zmienną numeryczną, która została zainicjowana do zera.</span><span class="sxs-lookup"><span data-stu-id="6e7b2-106">A misspelled variable name can implicitly create a numeric variable that is initialized to zero.</span></span>  
  
- <span data-ttu-id="6e7b2-107">Sprawdź poprzednie operacje na zmiennych w wyrażeniu, szczególnie te przekazane do procedury jako argumenty z innych procedur.</span><span class="sxs-lookup"><span data-stu-id="6e7b2-107">Check previous operations on variables in the expression, especially those passed into the procedure as arguments from other procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e7b2-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e7b2-108">See also</span></span>

- [<span data-ttu-id="6e7b2-109">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="6e7b2-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
