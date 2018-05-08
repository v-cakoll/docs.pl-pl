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
# <a name="directives-visual-basic"></a>Directives (Visual Basic)
Tematy w tej części dokumentu dyrektywy kompilatora kodu źródłowego języka Visual Basic.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [#Const-dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md) — zdefiniuj stałą kompilatora  
  
 [#ExternalSource — dyrektywa](../../../visual-basic/language-reference/directives/externalsource-directive.md) — wskazuje mapowanie między wierszy źródłowych i tekst do źródła zewnętrznego  
  
 [#If... Then... dyrektywy #Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md) --skompilować wybrane bloki kodu  
  
 [#Region — dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md) — zwijanie i ukrywanie fragmentów kodu w edytorze programu Visual Studio  
  
 **#Disable, #Enable** — Wyłącz i Włącz określone ostrzeżenia dla regionów kodu.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Można wyłączyć i włączyć zbyt rozdzielaną przecinkami listę kodów błędów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)
