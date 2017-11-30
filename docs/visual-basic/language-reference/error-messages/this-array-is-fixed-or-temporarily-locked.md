---
title: Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: adff10d4ae61e45402df64ebaa3baf146371ff9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a><span data-ttu-id="e7fbd-102">Ta tablica ma ustalony rozmiar lub jest tymczasowo zablokowana (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7fbd-102">This array is fixed or temporarily locked (Visual Basic)</span></span>
<span data-ttu-id="e7fbd-103">Ten błąd ma następujące możliwe przyczyny:</span><span class="sxs-lookup"><span data-stu-id="e7fbd-103">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="e7fbd-104">Przy użyciu `ReDim` Aby zmienić liczbę elementów w tablicy o ustalonym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-104">Using `ReDim` to change the number of elements of a fixed-size array.</span></span>  
  
-   <span data-ttu-id="e7fbd-105">Redimensioning poziom modułu dynamicznego tablicy, w której jeden element został przekazany jako argument do procedury.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-105">Redimensioning a module-level dynamic array, in which one element has been passed as an argument to a procedure.</span></span> <span data-ttu-id="e7fbd-106">Jeśli element zostanie przekazany, tablicy jest zablokowany w celu uniemożliwienia cofanie przydziału pamięci dla parametru odwołania w ramach procedury.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-106">If an element is passed, the array is locked to prevent deallocating memory for the reference parameter within the procedure.</span></span>  
  
-   <span data-ttu-id="e7fbd-107">Przypisanie wartości do prób `Variant` zmienną, która zawiera tablicę, ale `Variant` jest obecnie zablokowany.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-107">Attempting to assign a value to a `Variant` variable containing an array, but the `Variant` is currently locked.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e7fbd-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e7fbd-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="e7fbd-109">Ustawić dynamiczny, zamiast stałej ona z tablicy oryginalnej `ReDim` (Jeśli tablica jest zadeklarowany w procedurze,) lub przez zadeklarowanie go bez określania liczby elementów (Jeśli tablica jest zadeklarowane na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-109">Make the original array dynamic rather than fixed by declaring it with `ReDim` (if the array is declared within a procedure), or by declaring it without specifying the number of elements (if the array is declared at the module level.</span></span>  
  
2.  <span data-ttu-id="e7fbd-110">Ustal, czy naprawdę musisz przekazać elementu, ponieważ nie jest widoczna w ramach wszystkich procedur w module.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-110">Determine whether you really need to pass the element, since it is visible within all procedures in the module.</span></span>  
  
3.  <span data-ttu-id="e7fbd-111">Określić, co jest blokowanie `Variant` i naprawienia go.</span><span class="sxs-lookup"><span data-stu-id="e7fbd-111">Determine what is locking the `Variant` and remedy it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7fbd-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7fbd-112">See Also</span></span>  
 [<span data-ttu-id="e7fbd-113">Tablice</span><span class="sxs-lookup"><span data-stu-id="e7fbd-113">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
