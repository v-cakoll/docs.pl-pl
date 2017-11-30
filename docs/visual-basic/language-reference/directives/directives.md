---
title: Directives (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8219f17f1b8093b4d02b370c7b008101923b1873
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="directives-visual-basic"></a><span data-ttu-id="dd701-102">Directives (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd701-102">Directives (Visual Basic)</span></span>
<span data-ttu-id="dd701-103">Tematy w tej części dokumentu dyrektywy kompilatora kodu źródłowego języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dd701-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd701-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="dd701-104">In This Section</span></span>  
 <span data-ttu-id="dd701-105">[#Const-dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md) — zdefiniuj stałą kompilatora</span><span class="sxs-lookup"><span data-stu-id="dd701-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="dd701-106">[#ExternalSource — dyrektywa](../../../visual-basic/language-reference/directives/externalsource-directive.md) — wskazuje mapowanie między wierszy źródłowych i tekst do źródła zewnętrznego</span><span class="sxs-lookup"><span data-stu-id="dd701-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="dd701-107">[#If... Then... dyrektywy #Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md) --skompilować wybrane bloki kodu</span><span class="sxs-lookup"><span data-stu-id="dd701-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="dd701-108">[#Region — dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md) — zwijanie i ukrywanie fragmentów kodu w edytorze programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dd701-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="dd701-109">**#Disable, #Enable** — Wyłącz i Włącz określone ostrzeżenia dla regionów kodu.</span><span class="sxs-lookup"><span data-stu-id="dd701-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="dd701-110">Można wyłączyć i włączyć zbyt rozdzielaną przecinkami listę kodów błędów.</span><span class="sxs-lookup"><span data-stu-id="dd701-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="dd701-111">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="dd701-111">Related Sections</span></span>  
 [<span data-ttu-id="dd701-112">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dd701-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="dd701-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dd701-113">Visual Basic</span></span>](../../../visual-basic/index.md)
