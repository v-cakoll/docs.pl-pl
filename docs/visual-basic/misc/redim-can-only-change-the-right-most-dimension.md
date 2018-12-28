---
title: Element "reDim" można zmienić tylko wymiar najdalej z prawej strony
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 5b4f054c5d1dfad52ce19e1a9f9d246945866703
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2018
ms.locfileid: "53767400"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="a5de6-102">Element "reDim" można zmienić tylko wymiar najdalej z prawej strony</span><span class="sxs-lookup"><span data-stu-id="a5de6-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="a5de6-103">A `ReDim` instrukcji podjęto próbę użycia `Preserve` — słowo kluczowe, aby zmienić wymiaru tablicy, która nie jest ostatniego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="a5de6-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="a5de6-104">Korzystając z `Preserve`, zmiany rozmiaru tylko ostatniego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="a5de6-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="a5de6-105">Dla innych wymiarach należy określić ten sam rozmiar jak w przypadku istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="a5de6-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a5de6-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a5de6-106">To correct this error</span></span>  
  
-   <span data-ttu-id="a5de6-107">Usuń `Preserve` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="a5de6-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5de6-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5de6-108">See Also</span></span>  
 [<span data-ttu-id="a5de6-109">Tablice w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5de6-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="a5de6-110">Wymiary tablic w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5de6-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="a5de6-111">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a5de6-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="a5de6-112">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a5de6-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="a5de6-113">Zachowaj — usuwanie</span><span class="sxs-lookup"><span data-stu-id="a5de6-113">Preserve - delete</span></span>](https://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
