---
title: Tablice deklarowane jako członkowie struktury nie mogą być deklarowane z rozmiarem początkowym
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: de9d77aa9ea853b6f044e91878044115588ca77c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701254"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="d1013-102">Tablice deklarowane jako członkowie struktury nie mogą być deklarowane z rozmiarem początkowym</span><span class="sxs-lookup"><span data-stu-id="d1013-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="d1013-103">Tablica w strukturze jest zadeklarowana z rozmiarem początkowym.</span><span class="sxs-lookup"><span data-stu-id="d1013-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="d1013-104">Nie można zainicjować żadnego elementu struktury i deklarowania rozmiaru tablicy jest jedną z form inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="d1013-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="d1013-105">**Identyfikator błędu:** BC31043</span><span class="sxs-lookup"><span data-stu-id="d1013-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d1013-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d1013-106">To correct this error</span></span>  
  
1. <span data-ttu-id="d1013-107">Zdefiniuj tablicę w strukturze jako dynamiczną (bez początkowego rozmiaru).</span><span class="sxs-lookup"><span data-stu-id="d1013-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2. <span data-ttu-id="d1013-108">Jeśli potrzebujesz pewnego rozmiaru tablicy, możesz zmienić wymiar tablicy dynamicznej z [instrukcją ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) , gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="d1013-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="d1013-109">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="d1013-109">The following example illustrates this.</span></span>  
  
    ```vb  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d1013-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1013-110">See also</span></span>

- [<span data-ttu-id="d1013-111">Tablice</span><span class="sxs-lookup"><span data-stu-id="d1013-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="d1013-112">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="d1013-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
