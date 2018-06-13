---
title: '&#39;#Region&#39; i &#39;#End Region&#39; nie są prawidłowe w ramach metod treści wielowierszowych wyrażeń lambda'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: bf3843e0ec3009f3dc7d60e91c340a7f20543231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593236"
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="b554c-102">&#39;#Region&#39; i &#39;#End Region&#39; nie są prawidłowe w obrębie metody treści/wielowierszowych wyrażeń lambda</span><span class="sxs-lookup"><span data-stu-id="b554c-102">&#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="b554c-103">`#Region` Bloku musi być zadeklarowana na poziomie klasy, modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b554c-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="b554c-104">Region zwijanej mogą zawierać jedną lub więcej procedur, ale go nie może rozpoczynać się ani kończyć wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="b554c-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="b554c-105">**Identyfikator błędu:** BC32025</span><span class="sxs-lookup"><span data-stu-id="b554c-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b554c-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b554c-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="b554c-107">Upewnij się, że wcześniejsza procedura jest prawidłowo zakończony z `End Function` lub `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b554c-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="b554c-108">Upewnij się, że `#Region` i `#End Region` dyrektywy znajdują się w tym samym bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="b554c-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b554c-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b554c-109">See Also</span></span>  
 [<span data-ttu-id="b554c-110">#Region, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="b554c-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
