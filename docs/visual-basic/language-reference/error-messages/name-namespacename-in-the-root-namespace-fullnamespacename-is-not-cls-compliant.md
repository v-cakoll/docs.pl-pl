---
title: Nazwa <namespacename> w głównej przestrzeni nazw <fullnamespacename> jest niezgodna ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: c5afdcc98b7acb1927c9b0735a69fbe64c3d8e60
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268720"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a>Nazwa \<namespacename > w głównej przestrzeni nazw \<fullnamespacename > nie jest zgodny ze specyfikacją CLS
Zestaw jest oznaczony jako `<CLSCompliant(True)>`, ale element główna nazwa przestrzeni nazw, który rozpoczyna się od znaku podkreślenia (`_`).  
  
 Programowania element może zawierać jeden lub więcej podkreślenia, ale aby zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), należy nie zaczyna się ona od znaku podkreślenia. Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności. Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.  
  
 Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40039  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli wymagana jest zgodność ze specyfikacją CLS, należy zmienić główna nazwa przestrzeni nazw, aby żaden z jej elementów zaczyna się od znaku podkreślenia.  
  
-   Jeśli potrzebujesz, że nazwa przestrzeni nazw pozostają niezmienione, następnie usuń <xref:System.CLSCompliantAttribute> z zestawu lub oznaczyć go jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Zobacz także
- [Namespace, instrukcja](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Przestrzenie nazw w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Nazwy zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)

