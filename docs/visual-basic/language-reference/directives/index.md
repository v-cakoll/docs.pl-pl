---
title: Directives (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43409190"
---
# <a name="directives-visual-basic"></a>Directives (Visual Basic)
Tematy w tej części dokumentu dyrektywy kompilatora kod źródłowy języka Visual Basic.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [#Const-dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md) — zdefiniuj stałą kompilatora  
  
 [#ExternalSource — dyrektywa](../../../visual-basic/language-reference/directives/externalsource-directive.md) — wskaż mapowanie między wierszami źródłowymi a tekstem zewnętrznym do źródła  
  
 [#If... Then... dyrektywy #Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md) — skompiluj wybrane bloki kodu  
  
 [#Region — dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md) — zwijanie i ukrywanie fragmentów kodu w edytorze programu Visual Studio  
  
 **#Disable, #Enable** — Wyłącz i Włącz określone ostrzeżenia dotyczące regionów kodu.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Można wyłączyć i włączyć zbyt rozdzielaną przecinkami listę kodów ostrzeżeń.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)
