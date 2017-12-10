---
title: "Nazwa &lt;namespacename&gt; w głównej przestrzeni nazw &lt;fullnamespacename&gt; nie jest zgodne ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords: BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36de8b6a27c47e9e7192aed10e6b561bb0c07acc
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a>Nazwa &lt;namespacename&gt; w głównej przestrzeni nazw &lt;fullnamespacename&gt; nie jest zgodne ze specyfikacją CLS
Zestaw jest oznaczony jako `<CLSCompliant(True)>`, ale element nazwy głównej przestrzeni nazw rozpoczyna się od znaku podkreślenia (`_`).  
  
 Element programowania może zawierać jeden lub więcej znaków podkreślenia, ale aby było zgodne z [niezależność od języka i elementy niezależne od języka](../../../../docs/standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS) musi nie zaczynać się od znaku podkreślenia. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności. Nie jest domyślnie dla tego parametru, a należy podać wartość.  
  
 Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40039  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli potrzebujesz zgodności ze specyfikacją CLS, Zmień nazwy głównej przestrzeni nazw, tak, aby żaden z elementów jego rozpoczyna się od znaku podkreślenia.  
  
-   Jeśli potrzebujesz zmieniają nazwę przestrzeni nazw, następnie usuń <xref:System.CLSCompliantAttribute> z zestawu lub Oznacz go jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Zobacz też  
 [Namespace — instrukcja](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [/ rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)  
 [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [\<PAVE za pośrednictwem > Pisanie kodu zgodne ze specyfikacją CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
