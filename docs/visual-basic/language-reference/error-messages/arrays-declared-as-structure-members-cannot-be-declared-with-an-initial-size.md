---
title: Tablice deklarowane jako elementy członkowskie struktury nie mogą być deklarowane z rozmiarem początkowym
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 83342b780c0fa7c3a2e0a6797b80ef788117ae92
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250156"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="4498d-102">Tablice deklarowane jako elementy członkowskie struktury nie mogą być deklarowane z rozmiarem początkowym</span><span class="sxs-lookup"><span data-stu-id="4498d-102">Arrays declared as structure members cannot be declared with an initial size</span></span>

<span data-ttu-id="4498d-103">Tablica w strukturze jest zadeklarowana z rozmiarem początkowym.</span><span class="sxs-lookup"><span data-stu-id="4498d-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="4498d-104">Nie można zainicjować żadnego elementu struktury i deklarowania rozmiaru tablicy jest jedną z form inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="4498d-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>

<span data-ttu-id="4498d-105">**Identyfikator błędu:** BC31043</span><span class="sxs-lookup"><span data-stu-id="4498d-105">**Error ID:** BC31043</span></span>

## <a name="example"></a><span data-ttu-id="4498d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="4498d-106">Example</span></span>

<span data-ttu-id="4498d-107">Poniższy przykład generuje BC31043:</span><span class="sxs-lookup"><span data-stu-id="4498d-107">The following example generates BC31043:</span></span>

```vb
Structure DemoStruct
    Public demoArray(9) As Integer
End Structure
```

## <a name="to-correct-this-error"></a><span data-ttu-id="4498d-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4498d-108">To correct this error</span></span>

1. <span data-ttu-id="4498d-109">Zdefiniuj tablicę w strukturze jako dynamiczną (bez początkowego rozmiaru).</span><span class="sxs-lookup"><span data-stu-id="4498d-109">Define the array in your structure as dynamic (no initial size).</span></span>

2. <span data-ttu-id="4498d-110">Jeśli potrzebujesz pewnego rozmiaru tablicy, możesz zmienić wymiar tablicy dynamicznej z [instrukcją ReDim](../statements/redim-statement.md) , gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="4498d-110">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="4498d-111">Poniższy przykład ilustruje:</span><span class="sxs-lookup"><span data-stu-id="4498d-111">The following example illustrates this:</span></span>
  
    ```vb
    Structure DemoStruct
        Public demoArray() As Integer
    End Structure
    Sub UseStruct()
        Dim struct As DemoStruct  
        ReDim struct.demoArray(9)
        Struct.demoArray(2) = 777
    End Sub  
    ```
  
## <a name="see-also"></a><span data-ttu-id="4498d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4498d-112">See also</span></span>

- [<span data-ttu-id="4498d-113">Tablice</span><span class="sxs-lookup"><span data-stu-id="4498d-113">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="4498d-114">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="4498d-114">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
