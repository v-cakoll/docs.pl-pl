---
title: Dyrektyw
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: b5fcf3cb8801bc99dd2096c28cc41ebefeb34592
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410000"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="c50f0-102">Directives (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c50f0-102">Directives (Visual Basic)</span></span>

<span data-ttu-id="c50f0-103">W tematach w tej sekcji udokumentowano dyrektywy kompilatora Visual Basic kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="c50f0-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c50f0-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c50f0-104">In This Section</span></span>  

 <span data-ttu-id="c50f0-105">[#Const — dyrektywa](const-directive.md) — Definiowanie stałej kompilatora</span><span class="sxs-lookup"><span data-stu-id="c50f0-105">[#Const Directive](const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="c50f0-106">[#ExternalSource dyrektywie](externalsource-directive.md) --wskazać mapowanie między liniami źródłowymi a tekstem zewnętrznym względem źródła</span><span class="sxs-lookup"><span data-stu-id="c50f0-106">[#ExternalSource Directive](externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="c50f0-107">[#If... Then... #Else — dyrektywy](if-then-else-directives.md) — Kompilowanie wybranych bloków kodu</span><span class="sxs-lookup"><span data-stu-id="c50f0-107">[#If...Then...#Else Directives](if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="c50f0-108">[#Region dyrektywie](region-directive.md) — zwijanie i ukrywanie fragmentów kodu w edytorze programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c50f0-108">[#Region Directive](region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="c50f0-109">**#Disable, #Enable** --wyłączyć i włączyć określone ostrzeżenia dla regionów kodu.</span><span class="sxs-lookup"><span data-stu-id="c50f0-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="c50f0-110">Można również wyłączyć i włączyć listę kodów ostrzeżeń rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="c50f0-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c50f0-111">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c50f0-111">Related Sections</span></span>  

 [<span data-ttu-id="c50f0-112">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c50f0-112">Visual Basic Language Reference</span></span>](../index.md)  
  