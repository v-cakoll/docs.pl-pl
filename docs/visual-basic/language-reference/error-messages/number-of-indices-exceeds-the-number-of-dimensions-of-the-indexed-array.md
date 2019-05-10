---
title: Liczba indeksów przekracza liczbę wymiarów tablicy indeksowanej
ms.date: 07/20/2015
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords:
- BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
ms.openlocfilehash: 76cf0a997e9ad36ab4b5dfdc7c4bc29c57d309eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665691"
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a><span data-ttu-id="92832-102">Liczba indeksów przekracza liczbę wymiarów tablicy indeksowanej</span><span class="sxs-lookup"><span data-stu-id="92832-102">Number of indices exceeds the number of dimensions of the indexed array</span></span>
<span data-ttu-id="92832-103">Liczba indeksów, które umożliwiają dostęp do elementu tablicy musi być dokładnie taki sam jak rangę tablicy, czyli liczbę wymiarów zadeklarowany dla niego.</span><span class="sxs-lookup"><span data-stu-id="92832-103">The number of indices used to access an array element must be exactly the same as the rank of the array, that is, the number of dimensions declared for it.</span></span>  
  
 <span data-ttu-id="92832-104">**Identyfikator błędu:** BC30106</span><span class="sxs-lookup"><span data-stu-id="92832-104">**Error ID:** BC30106</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="92832-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="92832-105">To correct this error</span></span>  
  
- <span data-ttu-id="92832-106">Usuń indeksy dolne z odwołaniem do tablicy, aż łączna liczba indeksów dolnych jest równa rangę tablicy.</span><span class="sxs-lookup"><span data-stu-id="92832-106">Remove subscripts from the array reference until the total number of subscripts equals the rank of the array.</span></span> <span data-ttu-id="92832-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="92832-107">For example:</span></span>  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="92832-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92832-108">See also</span></span>

- [<span data-ttu-id="92832-109">Tablice</span><span class="sxs-lookup"><span data-stu-id="92832-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
