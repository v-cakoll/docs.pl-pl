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
