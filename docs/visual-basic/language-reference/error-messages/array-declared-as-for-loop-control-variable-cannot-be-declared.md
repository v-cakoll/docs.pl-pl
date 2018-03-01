---
title: "Tablica zadeklarowana jako zmienna sterująca pętli for nie może być zadeklarowana z rozmiarem początkowym"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef36f14d5323a4592afe59573e249d8cfb218df9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="da908-102">Tablica zadeklarowana jako zmienna sterująca pętli for nie może być zadeklarowana z rozmiarem początkowym</span><span class="sxs-lookup"><span data-stu-id="da908-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="da908-103">A `For Each` pętli używa tablicy jako jego *elementu* zmiennej iteracji, ale inicjuje tablicy.</span><span class="sxs-lookup"><span data-stu-id="da908-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="da908-104">Poniższe instrukcje przedstawiają sposób tego błędu mogą być generowane.</span><span class="sxs-lookup"><span data-stu-id="da908-104">The following statements show how this error can be generated.</span></span>  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="da908-105">Pierwszy `For Each` instrukcja jest prawidłowy sposób do dostępu do elementów `arrayList`.</span><span class="sxs-lookup"><span data-stu-id="da908-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="da908-106">Drugi `For Each` instrukcji generuje ten błąd.</span><span class="sxs-lookup"><span data-stu-id="da908-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="da908-107">**Identyfikator błędu:** BC32039</span><span class="sxs-lookup"><span data-stu-id="da908-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="da908-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="da908-108">To correct this error</span></span>  
  
-   <span data-ttu-id="da908-109">Usuń inicjowania z deklaracji *elementu* zmiennej iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="da908-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da908-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da908-110">See Also</span></span>  
 [<span data-ttu-id="da908-111">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="da908-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="da908-112">Tablice</span><span class="sxs-lookup"><span data-stu-id="da908-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="da908-113">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="da908-113">Collections</span></span>](../../../standard/collections/index.md)
