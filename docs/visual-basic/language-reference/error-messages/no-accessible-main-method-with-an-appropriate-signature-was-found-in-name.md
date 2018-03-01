---
title: "Brak dostępnego &#39; Main &#39; metody z odpowiednim podpisem został znaleziony w &#39; &lt;nazwa&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6a2d66c860b72bd3ef59c02f548ac563fab6b8c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a><span data-ttu-id="57697-102">Brak dostępnego &#39; Main &#39; metody z odpowiednim podpisem został znaleziony w &#39; &lt;nazwa&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="57697-102">No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;</span></span>
<span data-ttu-id="57697-103">Aplikacje wiersza poleceń musi mieć `Sub Main` zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="57697-103">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="57697-104">`Main`musi być zadeklarowany jako `Public Shared` , jeśli jest on zdefiniowany w klasie lub jako `Public` Jeśli zdefiniowany w module.</span><span class="sxs-lookup"><span data-stu-id="57697-104">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>  
  
 <span data-ttu-id="57697-105">**Identyfikator błędu:** BC30737</span><span class="sxs-lookup"><span data-stu-id="57697-105">**Error ID:** BC30737</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="57697-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="57697-106">To correct this error</span></span>  
  
-   <span data-ttu-id="57697-107">Zdefiniuj `Public Sub Main` procedury dla projektu.</span><span class="sxs-lookup"><span data-stu-id="57697-107">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="57697-108">Zadeklaruj ją jako `Shared` tylko wtedy, gdy należy zdefiniować wewnątrz klasy.</span><span class="sxs-lookup"><span data-stu-id="57697-108">Declare it as `Shared` if and only if you define it inside a class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57697-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57697-109">See Also</span></span>  
 [<span data-ttu-id="57697-110">Struktura programu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57697-110">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="57697-111">Procedury</span><span class="sxs-lookup"><span data-stu-id="57697-111">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
