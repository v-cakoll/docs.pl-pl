---
title: Nazwa &lt;membername&gt; nie jest zgodne ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 26ff13de461d5a96724868b7928129a326cdf1d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593345"
---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a>Nazwa &lt;membername&gt; nie jest zgodne ze specyfikacją CLS
Zestaw jest oznaczony jako `<CLSCompliant(True)>` , ale udostępnia element członkowski o nazwie, która rozpoczyna się od znaku podkreślenia (`_`).  
  
 Element programowania może zawierać jeden lub więcej znaków podkreślenia, ale aby było zgodne z [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS) musi nie zaczynać się od znaku podkreślenia. Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności. Nie jest domyślnie dla tego parametru, a należy podać wartość.  
  
 Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40031  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli masz kontrolę kodu źródłowego, Zmień nazwę elementu członkowskiego, tak, aby nie zaczyna się od znaku podkreślenia.  
  
-   Jeśli potrzebujesz, że nazwa elementu członkowskiego pozostają niezmienione, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub Oznacz go jako `<CLSCompliant(False)>`. Można nadal Oznacz zestaw jako `<CLSCompliant(True)>`.  
  
## <a name="see-also"></a>Zobacz też  
 [Nazwy zadeklarowanych elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Visual Basic — konwencje nazewnictwa](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  

