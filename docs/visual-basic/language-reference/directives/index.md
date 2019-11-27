---
title: Dyrektyw
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: d76e10ad5ce8ad3accdc84f97146e0816048d8f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343803"
---
# <a name="directives-visual-basic"></a>Directives (Visual Basic)

W tematach w tej sekcji udokumentowano dyrektywy kompilatora Visual Basic kodu źródłowego.  
  
## <a name="in-this-section"></a>W tej sekcji  

 [#Const — dyrektywa](../../../visual-basic/language-reference/directives/const-directive.md) — Definiowanie stałej kompilatora  
  
 [#ExternalSource dyrektywie](../../../visual-basic/language-reference/directives/externalsource-directive.md) --wskazać mapowanie między liniami źródłowymi a tekstem zewnętrznym względem źródła  
  
 [#If... Then... #Else — dyrektywy](../../../visual-basic/language-reference/directives/if-then-else-directives.md) — Kompilowanie wybranych bloków kodu  
  
 [#Region dyrektywie](../../../visual-basic/language-reference/directives/region-directive.md) — zwijanie i ukrywanie fragmentów kodu w edytorze programu Visual Studio  
  
 **#Disable, #Enable** --wyłączyć i włączyć określone ostrzeżenia dla regionów kodu.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Można również wyłączyć i włączyć listę kodów ostrzeżeń rozdzielonych przecinkami.  
  
## <a name="related-sections"></a>Sekcje pokrewne  

 [Dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)
