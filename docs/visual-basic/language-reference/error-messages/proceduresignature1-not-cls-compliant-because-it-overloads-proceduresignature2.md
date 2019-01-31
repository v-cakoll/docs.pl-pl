---
title: Element „<proceduresignature1>” nie jest zgodny ze specyfikacją CLS, ponieważ przeciąża element „<proceduresignature2>”, który różni się od niego tylko tablicą typów parametrów tablicowych lub rangą typów parametrów tablicowych
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 0bda4ad6a4d5368d93e2ca603b78bf9db6aca858
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269565"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>\<proceduresignature1 > nie jest zgodny ze specyfikacją CLS, ponieważ przeciąża \<proceduresignature2 > który różni się od niego tylko tablicą typów parametrów tablicowych lub rangą typów parametrów tablicowych
Procedura lub właściwość jest oznaczona jako `<CLSCompliant(True)>` po zastępuje ona inny procedura lub właściwość, a jedyną różnicą między swoimi listami parametr jest poziom zagnieżdżenia tablicy nieregularnej lub rangę tablicy.  
  
 W następujące deklaracje deklaracje drugi i trzeci generuje ten błąd.  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 Drugi deklaracja zmienia pierwotny parametr jednowymiarowa `arrayParam` do tablicy tablic. Trzeci zmiany deklaracji `arrayParam` dwuwymiarowej tablicy (ranga 2). Chociaż Visual Basic umożliwia przeciążenia, które mogą się różnić tylko przez jeden z tych zmian, takich przeciążenie nie jest zgodne z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności. Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.  
  
 Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40035  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli wymagana jest zgodność ze specyfikacją CLS, należy zdefiniować swoje przeciążenia mogą się różnić od siebie nawzajem na więcej sposobów niż tylko zmiany wymienione na tej stronie pomocy.  
  
-   Jeśli potrzebujesz, że przeciążenia różnią się tylko przez zmiany wymienione w tej pomocy strony, Usuń <xref:System.CLSCompliantAttribute> ze swojej definicji lub oznaczyć je jako `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Zobacz także

- [Przeciążanie procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
