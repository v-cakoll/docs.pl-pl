---
title: Directives (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797855"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="c75ca-102">Directives (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c75ca-102">Directives (Visual Basic)</span></span>
<span data-ttu-id="c75ca-103">Tematy w tej części dokumentu dyrektywy kompilatora kod źródłowy języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c75ca-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c75ca-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c75ca-104">In This Section</span></span>  
 <span data-ttu-id="c75ca-105">[#Const-dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md) — zdefiniuj stałą kompilatora</span><span class="sxs-lookup"><span data-stu-id="c75ca-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="c75ca-106">[#ExternalSource — dyrektywa](../../../visual-basic/language-reference/directives/externalsource-directive.md) — wskaż mapowanie między wierszami źródłowymi a tekstem zewnętrznym do źródła</span><span class="sxs-lookup"><span data-stu-id="c75ca-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="c75ca-107">[#If... Then... dyrektywy #Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md) — skompiluj wybrane bloki kodu</span><span class="sxs-lookup"><span data-stu-id="c75ca-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="c75ca-108">[#Region — dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md) — zwijanie i ukrywanie fragmentów kodu w edytorze programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c75ca-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="c75ca-109">**#Disable, #Enable** — Wyłącz i Włącz określone ostrzeżenia dotyczące regionów kodu.</span><span class="sxs-lookup"><span data-stu-id="c75ca-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="c75ca-110">Można wyłączyć i włączyć zbyt rozdzielaną przecinkami listę kodów ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="c75ca-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c75ca-111">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c75ca-111">Related Sections</span></span>  
 [<span data-ttu-id="c75ca-112">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c75ca-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="c75ca-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c75ca-113">Visual Basic</span></span>](../../../visual-basic/index.md)
