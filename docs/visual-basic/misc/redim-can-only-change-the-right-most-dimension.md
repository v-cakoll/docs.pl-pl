---
title: '&#39;ReDim&#39; można zmienić tylko wymiar najdalej z prawej strony'
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 94e0fe81f7e750a67943b68f2db700e3a7831da1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502589"
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="24645-102">&#39;ReDim&#39; można zmienić tylko wymiar najdalej z prawej strony</span><span class="sxs-lookup"><span data-stu-id="24645-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="24645-103">A `ReDim` instrukcji podjęto próbę użycia `Preserve` — słowo kluczowe, aby zmienić wymiaru tablicy, która nie jest ostatniego wymiaru.</span><span class="sxs-lookup"><span data-stu-id="24645-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="24645-104">Korzystając z `Preserve`, zmiany rozmiaru tylko ostatniego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="24645-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="24645-105">Dla innych wymiarach należy określić ten sam rozmiar jak w przypadku istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="24645-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="24645-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="24645-106">To correct this error</span></span>  
  
-   <span data-ttu-id="24645-107">Usuń `Preserve` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="24645-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24645-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24645-108">See Also</span></span>  
 [<span data-ttu-id="24645-109">Tablice w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24645-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="24645-110">Wymiary tablic w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24645-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="24645-111">ReDim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="24645-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="24645-112">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="24645-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="24645-113">Zachowaj — usuwanie</span><span class="sxs-lookup"><span data-stu-id="24645-113">Preserve - delete</span></span>](https://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
