---
title: Granice tablicy nie mogą wystąpić w specyfikatorze typu
ms.date: 07/20/2015
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords:
- BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
ms.openlocfilehash: f20ed883005641082eb89e2effa5221594910ffe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838784"
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="2eab2-102">Granice tablicy nie mogą wystąpić w specyfikatorze typu</span><span class="sxs-lookup"><span data-stu-id="2eab2-102">Array bounds cannot appear in type specifiers</span></span>
<span data-ttu-id="2eab2-103">Rozmiar tablicy nie można zadeklarować jako część specyfikatora typu danych.</span><span class="sxs-lookup"><span data-stu-id="2eab2-103">Array sizes cannot be declared as part of a data type specifier.</span></span>  
  
 <span data-ttu-id="2eab2-104">**Identyfikator błędu:** BC30638</span><span class="sxs-lookup"><span data-stu-id="2eab2-104">**Error ID:** BC30638</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2eab2-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2eab2-105">To correct this error</span></span>  
  
-   <span data-ttu-id="2eab2-106">Określ rozmiar tablicy, natychmiast po nazwę zmiennej, zamiast wykonywać rozmiaru tablicy po typie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2eab2-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   <span data-ttu-id="2eab2-107">Zdefiniować tablicę i zainicjuj ją z odpowiednią liczbę elementów, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2eab2-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2eab2-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2eab2-108">See also</span></span>

- [<span data-ttu-id="2eab2-109">Tablice</span><span class="sxs-lookup"><span data-stu-id="2eab2-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
