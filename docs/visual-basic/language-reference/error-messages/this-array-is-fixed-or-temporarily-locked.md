---
title: Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 4a86460104b6c4d9d6791e60f6f377cec0030425
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363036"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="f196c-102">Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f196c-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="f196c-103">Ten błąd ma następujące możliwe przyczyny:</span><span class="sxs-lookup"><span data-stu-id="f196c-103">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="f196c-104">Przy użyciu `ReDim` programu można zmienić liczbę elementów tablicy o stałym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="f196c-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
- <span data-ttu-id="f196c-105">Przewymiarowanie dynamicznej tablicy na poziomie modułu, w którym jeden element został przekazano jako argument do procedury.</span><span class="sxs-lookup"><span data-stu-id="f196c-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="f196c-106">Jeśli element jest zakończony, tablica jest zablokowana, aby zapobiec cofnięciu przydziału pamięci dla parametru Reference w ramach procedury.</span><span class="sxs-lookup"><span data-stu-id="f196c-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
- <span data-ttu-id="f196c-107">Podjęto próbę przypisania wartości do `Variant` zmiennej zawierającej tablicę, ale `Variant` jest ona obecnie zablokowana.</span><span class="sxs-lookup"><span data-stu-id="f196c-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f196c-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f196c-108">To correct this error</span></span>  
  
1. <span data-ttu-id="f196c-109">Oznacz oryginalną tablicę zamiast naprawić, deklarując ją z `ReDim` (jeśli tablica jest zadeklarowana w ramach procedury) lub deklarując ją bez określania liczby elementów (jeśli tablica jest zadeklarowana na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="f196c-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2. <span data-ttu-id="f196c-110">Ustal, czy naprawdę potrzebujesz przekazać element, ponieważ jest on widoczny we wszystkich procedurach w module.</span><span class="sxs-lookup"><span data-stu-id="f196c-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3. <span data-ttu-id="f196c-111">Określ, co blokuje `Variant` i zaradzenia.</span><span class="sxs-lookup"><span data-stu-id="f196c-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f196c-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f196c-112">See also</span></span>

- [<span data-ttu-id="f196c-113">Tablice</span><span class="sxs-lookup"><span data-stu-id="f196c-113">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
