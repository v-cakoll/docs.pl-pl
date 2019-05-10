---
title: Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: c7b5372b6046e25aad87131ba141cb71c580e12c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625942"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="8ebc4-102">Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ebc4-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="8ebc4-103">Ten błąd ma następujące możliwe przyczyny:</span><span class="sxs-lookup"><span data-stu-id="8ebc4-103">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="8ebc4-104">Za pomocą `ReDim` Aby zmienić liczbę elementów tablicy o stałym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="8ebc4-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
- <span data-ttu-id="8ebc4-105">Redimensioning tablic dynamicznych poziom modułu, w którym jeden element został przekazany jako argument do procedury.</span><span class="sxs-lookup"><span data-stu-id="8ebc4-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="8ebc4-106">Jeśli element jest przekazywany, tablica jest zablokowane, aby uniemożliwić cofanie przydziału pamięci dla parametru odwołania w ramach procedury.</span><span class="sxs-lookup"><span data-stu-id="8ebc4-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
- <span data-ttu-id="8ebc4-107">Próba przypisania wartości do `Variant` zmienną, która zawiera tablicę, ale `Variant` jest obecnie zablokowany.</span><span class="sxs-lookup"><span data-stu-id="8ebc4-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8ebc4-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8ebc4-108">To correct this error</span></span>  
  
1. <span data-ttu-id="8ebc4-109">Utworzyć tablicy oryginalnej dynamiczną, zamiast stałej deklarując ją za pomocą `ReDim` (Jeśli tablica jest zadeklarowana w obrębie procedury), lub deklarując ją bez określania liczby elementów (Jeśli tablica jest zadeklarowana na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="8ebc4-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2. <span data-ttu-id="8ebc4-110">Ustal, czy naprawdę potrzebujesz przekazać elementu, ponieważ jest ona widoczna w ramach wszystkich procedur w module.</span><span class="sxs-lookup"><span data-stu-id="8ebc4-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3. <span data-ttu-id="8ebc4-111">Określić, co blokuje `Variant` i usunięcia go.</span><span class="sxs-lookup"><span data-stu-id="8ebc4-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ebc4-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ebc4-112">See also</span></span>

- [<span data-ttu-id="8ebc4-113">Tablice</span><span class="sxs-lookup"><span data-stu-id="8ebc4-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
