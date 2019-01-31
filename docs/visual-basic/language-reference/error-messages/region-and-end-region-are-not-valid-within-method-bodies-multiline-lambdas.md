---
title: Instrukcje "#Region" i "#End Region" nie są prawidłowe w metod treści wielowierszowych wyrażeń lambda
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 2a2f5692518c6784dfc6e3be6302f1e8dcf2aaa7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265574"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="37e89-102">Instrukcje „#Region” i „#End Region” nie są prawidłowe w treści metod/wielowierszowych wyrażeń lambda</span><span class="sxs-lookup"><span data-stu-id="37e89-102">'#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="37e89-103">`#Region` Bloku musi być zadeklarowany na poziomie klasy, modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="37e89-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="37e89-104">Region zwijany może zawierać jedną lub kilkoma procedurami, ale go nie może rozpoczynać się ani kończyć się wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="37e89-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="37e89-105">**Identyfikator błędu:** BC32025</span><span class="sxs-lookup"><span data-stu-id="37e89-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="37e89-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="37e89-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="37e89-107">Upewnij się, że poprzedniej procedury prawidłowo jest kończony przy użyciu `End Function` lub `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="37e89-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="37e89-108">Upewnij się, że `#Region` i `#End Region` dyrektywy znajdują się w tym samym bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="37e89-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e89-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37e89-109">See also</span></span>
- [<span data-ttu-id="37e89-110">#Region, dyrektywa</span><span class="sxs-lookup"><span data-stu-id="37e89-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
