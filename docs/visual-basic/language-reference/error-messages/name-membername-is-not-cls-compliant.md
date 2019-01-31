---
title: Nazwa <membername> jest niezgodna ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 74b625cc3a60e591417530c6a6229c01666038e2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271255"
---
# <a name="name-membername-is-not-cls-compliant"></a>Nazwa \<membername > nie jest zgodny ze specyfikacją CLS
Zestaw jest oznaczony jako `<CLSCompliant(True)>` , ale udostępnia element członkowski o nazwie rozpoczynającej się od znaku podkreślenia (`_`).  
  
 Programowania element może zawierać jeden lub więcej podkreślenia, ale aby zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), należy nie zaczyna się ona od znaku podkreślenia. Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności. Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.  
  
 Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40031  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli masz kontrolę kodu źródłowego, Zmień nazwę elementu członkowskiego, tak, aby nie zaczyna się od znaku podkreślenia.  
  
-   Jeśli potrzebujesz, że nazwa elementu członkowskiego pozostają niezmienione, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub oznaczyć go jako `<CLSCompliant(False)>`. Nadal możesz oznaczyć zestaw jako `<CLSCompliant(True)>`.  
  
## <a name="see-also"></a>Zobacz także
- [Nazwy zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)

