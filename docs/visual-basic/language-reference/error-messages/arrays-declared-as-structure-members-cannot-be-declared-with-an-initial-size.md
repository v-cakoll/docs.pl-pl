---
title: Tablice deklarowane jako członkowie struktury nie mogą być deklarowane z rozmiarem początkowym
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 5d58b531b670715716e849cd37227bc899195df6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335306"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="c70a0-102">Tablice deklarowane jako członkowie struktury nie mogą być deklarowane z rozmiarem początkowym</span><span class="sxs-lookup"><span data-stu-id="c70a0-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="c70a0-103">Tablica w strukturze jest zadeklarowana z rozmiarem początkowym.</span><span class="sxs-lookup"><span data-stu-id="c70a0-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="c70a0-104">Nie można zainicjować dowolnego elementu struktury i deklarowanie rozmiar tablicy jest jeden formularz inicjowania.</span><span class="sxs-lookup"><span data-stu-id="c70a0-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="c70a0-105">**Identyfikator błędu:** BC31043</span><span class="sxs-lookup"><span data-stu-id="c70a0-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c70a0-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c70a0-106">To correct this error</span></span>  
  
1. <span data-ttu-id="c70a0-107">Zdefiniować tablicę w strukturze jako dynamiczna (nie rozmiar początkowy).</span><span class="sxs-lookup"><span data-stu-id="c70a0-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2. <span data-ttu-id="c70a0-108">Jeśli potrzebujesz rozmiar tablicy, możesz redimension tablic dynamicznych z [instrukcji ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="c70a0-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="c70a0-109">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="c70a0-109">The following example illustrates this.</span></span>  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c70a0-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c70a0-110">See also</span></span>

- [<span data-ttu-id="c70a0-111">Tablice</span><span class="sxs-lookup"><span data-stu-id="c70a0-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="c70a0-112">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="c70a0-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
