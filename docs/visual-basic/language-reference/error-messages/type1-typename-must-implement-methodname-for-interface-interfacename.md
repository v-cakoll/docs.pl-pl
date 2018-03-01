---
title: "&lt;type1&gt;&#39;&lt; Właściwość TypeName&gt;&#39; musi wdrożenie &#39;&lt; methodname&gt;&#39; dla interfejsu &#39;&lt; InterfaceName&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e803ec7d0054f2fa1b9ed2a731fd30c9c3060468
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="e0956-102">&lt;type1&gt;&#39;&lt; Właściwość TypeName&gt;&#39; musi wdrożenie &#39;&lt; methodname&gt;&#39; dla interfejsu &#39;&lt; InterfaceName&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="e0956-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;methodname&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="e0956-103">Klasy lub struktury oświadczeń do zaimplementowania interfejsu, ale nie implementuje określonymi przez interfejs.</span><span class="sxs-lookup"><span data-stu-id="e0956-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="e0956-104">Każdy element członkowski interfejsu musi być implementowana.</span><span class="sxs-lookup"><span data-stu-id="e0956-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="e0956-105">**Identyfikator błędu:** BC30149</span><span class="sxs-lookup"><span data-stu-id="e0956-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e0956-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e0956-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="e0956-107">Deklaruje procedurę o tej samej nazwie i podpisie zgodnie z definicją w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="e0956-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="e0956-108">Należy uwzględnić co najmniej `End Function` lub `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e0956-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="e0956-109">Dodaj `Implements` klauzuli na końcu `Function` lub `Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e0956-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="e0956-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e0956-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e0956-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0956-111">See Also</span></span>  
 [<span data-ttu-id="e0956-112">Implements — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e0956-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="e0956-113">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e0956-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
