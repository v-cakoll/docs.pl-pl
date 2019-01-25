---
title: Element "reDim" można zmienić tylko wymiar najdalej z prawej strony
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 97eedabd550be397f9cdffc5fd864d7a88c30c31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714207"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="46cec-102">Element "reDim" można zmienić tylko wymiar najdalej z prawej strony</span><span class="sxs-lookup"><span data-stu-id="46cec-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="46cec-103">A `ReDim` instrukcji podjęto próbę użycia `Preserve` — słowo kluczowe, aby zmienić wymiaru tablicy, która nie jest ostatniego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="46cec-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="46cec-104">Korzystając z `Preserve`, zmiany rozmiaru tylko ostatniego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="46cec-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="46cec-105">Dla innych wymiarach należy określić ten sam rozmiar jak w przypadku istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="46cec-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="46cec-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="46cec-106">To correct this error</span></span>  
  
-   <span data-ttu-id="46cec-107">Usuń `Preserve` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="46cec-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46cec-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46cec-108">See also</span></span>
- [<span data-ttu-id="46cec-109">Tablice w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="46cec-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="46cec-110">Wymiary tablic w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="46cec-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="46cec-111">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="46cec-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="46cec-112">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="46cec-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="46cec-113">Zachowaj — usuwanie</span><span class="sxs-lookup"><span data-stu-id="46cec-113">Preserve - delete</span></span>](https://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
