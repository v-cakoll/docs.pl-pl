---
title: Brak dostępnego &#39;Main&#39; metody z odpowiednim podpisem został znaleziony w &#39; &lt;nazwy&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6a60e26a2bd0e31c0f92dbbfb2518c75f304d9f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="9589a-102">Brak dostępnego &#39;Main&#39; metody z odpowiednim podpisem został znaleziony w &#39; &lt;nazwy&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="9589a-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="9589a-103">Aplikacje wiersza poleceń musi mieć `Sub Main` zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="9589a-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="9589a-104">`Main` musi być zadeklarowany jako `Public Shared` , jeśli jest on zdefiniowany w klasie lub jako `Public` Jeśli zdefiniowany w module.</span><span class="sxs-lookup"><span data-stu-id="9589a-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="9589a-105">**Identyfikator błędu:** BC30737</span><span class="sxs-lookup"><span data-stu-id="9589a-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9589a-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9589a-106">To correct this error</span></span>  
  
-   <span data-ttu-id="9589a-107">Zdefiniuj `Public Sub Main` procedury dla projektu.</span><span class="sxs-lookup"><span data-stu-id="9589a-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="9589a-108">Zadeklaruj ją jako `Shared` tylko wtedy, gdy należy zdefiniować wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="9589a-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9589a-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9589a-109">See Also</span></span>  
 [<span data-ttu-id="9589a-110">Struktura programu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9589a-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="9589a-111">Procedury</span><span class="sxs-lookup"><span data-stu-id="9589a-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
