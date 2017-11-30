---
title: "&#39; ReDim &#39; można zmienić tylko wymiar z prawej"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 989a06f94824dfd051d1a7d2e7749dbb8c8e11a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="a4410-102">&#39; ReDim &#39; można zmienić tylko wymiar z prawej</span><span class="sxs-lookup"><span data-stu-id="a4410-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="a4410-103">A `ReDim` instrukcji podjęto próbę użycia `Preserve` — słowo kluczowe, aby zmienić wymiaru tablicy, która nie jest ostatni wymiar.</span><span class="sxs-lookup"><span data-stu-id="a4410-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="a4410-104">Korzystając z `Preserve`, zmianie rozmiaru tylko ostatniego wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4410-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="a4410-105">Dla wszystkich innych wymiarów należy określić ten sam rozmiar jak w przypadku istniejącej tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4410-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a4410-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a4410-106">To correct this error</span></span>  
  
-   <span data-ttu-id="a4410-107">Usuń `Preserve` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="a4410-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4410-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4410-108">See Also</span></span>  
 [<span data-ttu-id="a4410-109">Tablice w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4410-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="a4410-110">Wymiary tablicy w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4410-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="a4410-111">ReDim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="a4410-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="a4410-112">Dim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="a4410-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="a4410-113">Zachowaj — usuwanie</span><span class="sxs-lookup"><span data-stu-id="a4410-113">Preserve - delete</span></span>](http://msdn.microsoft.com/en-us/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
