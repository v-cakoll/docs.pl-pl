---
title: Directives (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="directives-visual-basic"></a><span data-ttu-id="294ab-102">Directives (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="294ab-102">Directives (Visual Basic)</span></span>
<span data-ttu-id="294ab-103">Tematy w tej części dokumentu dyrektywy kompilatora kodu źródłowego języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="294ab-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="294ab-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="294ab-104">In This Section</span></span>  
 <span data-ttu-id="294ab-105">[#Const-dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md) — zdefiniuj stałą kompilatora</span><span class="sxs-lookup"><span data-stu-id="294ab-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="294ab-106">[#ExternalSource — dyrektywa](../../../visual-basic/language-reference/directives/externalsource-directive.md) — wskazuje mapowanie między wierszy źródłowych i tekst do źródła zewnętrznego</span><span class="sxs-lookup"><span data-stu-id="294ab-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="294ab-107">[#If... Then... dyrektywy #Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md) --skompilować wybrane bloki kodu</span><span class="sxs-lookup"><span data-stu-id="294ab-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="294ab-108">[#Region — dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md) — zwijanie i ukrywanie fragmentów kodu w edytorze programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="294ab-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="294ab-109">**#Disable, #Enable** — Wyłącz i Włącz określone ostrzeżenia dla regionów kodu.</span><span class="sxs-lookup"><span data-stu-id="294ab-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="294ab-110">Można wyłączyć i włączyć zbyt rozdzielaną przecinkami listę kodów błędów.</span><span class="sxs-lookup"><span data-stu-id="294ab-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="294ab-111">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="294ab-111">Related Sections</span></span>  
 [<span data-ttu-id="294ab-112">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="294ab-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="294ab-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="294ab-113">Visual Basic</span></span>](../../../visual-basic/index.md)
