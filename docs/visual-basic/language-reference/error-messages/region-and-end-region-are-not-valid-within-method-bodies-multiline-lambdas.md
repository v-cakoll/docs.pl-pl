---
title: '&#39;#Region&#39; i &#39;#End Region&#39; instrukcje nie są prawidłowe w ramach metod treści wielowierszowych wyrażeń lambda'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 55399cd123ce4d67cc833f2eabe3230acdafc0bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737218"
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="35936-102">&#39;#Region&#39; i &#39;#End Region&#39; instrukcje nie są prawidłowe w ramach metody treści/wielowierszowych wyrażeń lambda</span><span class="sxs-lookup"><span data-stu-id="35936-102">&#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="35936-103">`#Region` Bloku musi być zadeklarowany na poziomie klasy, modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="35936-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="35936-104">Region zwijany może zawierać jedną lub kilkoma procedurami, ale go nie może rozpoczynać się ani kończyć się wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="35936-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="35936-105">**Identyfikator błędu:** BC32025</span><span class="sxs-lookup"><span data-stu-id="35936-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="35936-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="35936-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="35936-107">Upewnij się, że poprzedniej procedury prawidłowo jest kończony przy użyciu `End Function` lub `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="35936-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="35936-108">Upewnij się, że `#Region` i `#End Region` dyrektywy znajdują się w tym samym bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="35936-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35936-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35936-109">See also</span></span>
- [<span data-ttu-id="35936-110">#Region, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="35936-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
