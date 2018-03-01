---
title: "Tablice deklarowane jako członkowie struktury nie mogą być deklarowane z rozmiarem początkowym"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 983154a144a79991c86db5056ad0e0e563a3ba73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="a39bb-102">Tablice deklarowane jako członkowie struktury nie mogą być deklarowane z rozmiarem początkowym</span><span class="sxs-lookup"><span data-stu-id="a39bb-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="a39bb-103">Tablicy w strukturze jest zadeklarowana z rozmiarem początkowym.</span><span class="sxs-lookup"><span data-stu-id="a39bb-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="a39bb-104">Nie można zainicjować dowolny element struktury i deklarowanie rozmiaru tablicy jest jeden formularz inicjowania.</span><span class="sxs-lookup"><span data-stu-id="a39bb-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="a39bb-105">**Identyfikator błędu:** BC31043</span><span class="sxs-lookup"><span data-stu-id="a39bb-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a39bb-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a39bb-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="a39bb-107">Zdefiniuj tablicy w strukturze jako dynamiczny (nie początkowy rozmiar).</span><span class="sxs-lookup"><span data-stu-id="a39bb-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2.  <span data-ttu-id="a39bb-108">Jeśli potrzebujesz rozmiar tablicy można zmiany jego wymiarów tablicy dynamicznej z [instrukcji ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="a39bb-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="a39bb-109">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="a39bb-109">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a39bb-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a39bb-110">See Also</span></span>  
 [<span data-ttu-id="a39bb-111">Tablice</span><span class="sxs-lookup"><span data-stu-id="a39bb-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="a39bb-112">Porady: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="a39bb-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
