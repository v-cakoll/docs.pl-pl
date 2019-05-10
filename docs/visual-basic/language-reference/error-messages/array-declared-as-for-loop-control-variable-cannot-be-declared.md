---
title: Tablica zadeklarowana jako zmienna sterująca pętli for nie może być zadeklarowana z rozmiarem początkowym
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: 9f24dd2a20dc3a4935cd288a20a0e12c1d47bee1
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912345"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="0a391-102">Tablica zadeklarowana jako zmienna sterująca pętli for nie może być zadeklarowana z rozmiarem początkowym</span><span class="sxs-lookup"><span data-stu-id="0a391-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="0a391-103">A `For Each` pętli używa tablicy jako jego *elementu* Zmienna iteracji, ale inicjuje tej tablicy.</span><span class="sxs-lookup"><span data-stu-id="0a391-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="0a391-104">Poniższe instrukcje przedstawiają, jak ten błąd może zostać wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="0a391-104">The following statements show how this error can be generated.</span></span>  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="0a391-105">Pierwszy `For Each` instrukcja jest poprawny sposób dostępu do elementów `arrayList`.</span><span class="sxs-lookup"><span data-stu-id="0a391-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="0a391-106">Drugi `For Each` instrukcja generuje ten błąd.</span><span class="sxs-lookup"><span data-stu-id="0a391-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="0a391-107">**Identyfikator błędu:** BC32039</span><span class="sxs-lookup"><span data-stu-id="0a391-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a391-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="0a391-108">To correct this error</span></span>  
  
- <span data-ttu-id="0a391-109">Usuń inicjowania z deklaracji *elementu* Zmienna iteracji.</span><span class="sxs-lookup"><span data-stu-id="0a391-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a391-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a391-110">See also</span></span>

- [<span data-ttu-id="0a391-111">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0a391-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="0a391-112">Tablice</span><span class="sxs-lookup"><span data-stu-id="0a391-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="0a391-113">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="0a391-113">Collections</span></span>](../../../standard/collections/index.md)
