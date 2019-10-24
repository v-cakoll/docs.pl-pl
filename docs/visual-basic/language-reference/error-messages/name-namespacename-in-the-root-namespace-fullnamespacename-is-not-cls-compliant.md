---
title: Nazwa <namespacename> w głównej przestrzeni nazw <fullnamespacename> jest niezgodna ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 821044d3ee359a052fa6a763e9c5a89da5d6f607
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775578"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a>Nazwa \<namespacename > w głównej przestrzeni nazw \<fullnamespacename > jest niezgodna ze specyfikacją CLS
Zestaw jest oznaczony jako `<CLSCompliant(True)>`, ale element nazwy głównej przestrzeni nazw zaczyna się od znaku podkreślenia (`_`).  
  
 Element programowania może zawierać jeden lub więcej podkreśleń, ale w celu uzyskania zgodności z [niezależnymi od języka i składnikami niezależnymi od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS) nie może zaczynać się od znaku podkreślenia. Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, należy ustawić parametr `isCompliant` atrybutu na `True` lub `False`, aby wskazać zgodność lub niezgodność. Dla tego parametru nie ma wartości domyślnej i należy podać wartość.  
  
 Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> do elementu, jest on uznawany za niezgodny.  
  
 Domyślnie ten komunikat jest ostrzeżeniem. Aby uzyskać informacje na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40039  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli jest wymagana zgodność ze specyfikacją CLS, Zmień nazwę głównej przestrzeni nazw, tak aby żaden z jej elementów nie zaczynał się od znaku podkreślenia.  
  
- Jeśli potrzebujesz, aby nazwa przestrzeni nazw pozostała niezmieniona, Usuń <xref:System.CLSCompliantAttribute> z zestawu lub oznacz ją jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Zobacz także

- [Namespace, instrukcja](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [-rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Nazwy zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Konwencje nazewnictwa Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
