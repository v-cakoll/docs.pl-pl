---
title: <proceduresignature1> jest niezgodna ze specyfikacją CLS, ponieważ przeciążania <proceduresignature2>, które różnią się tylko tablicą typów parametrów tablicowych lub według rangi typów parametrów tablicy
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 6143ebfbe7f131b0e196e531ed4282c8333be4ea
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250182"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>\<proceduresignature1 > jest niezgodna ze specyfikacją CLS, ponieważ przeciąż \<proceduresignature2 >, które różnią się tylko tablicą typów parametrów tablicowych lub według rangi typów parametrów tablicy

Procedura lub właściwość jest oznaczona jako `<CLSCompliant(True)>`, gdy zastępuje inną procedurę lub właściwość i jedyną różnicą między ich listami parametrów jest poziom zagnieżdżenia tablicy nieregularnej lub rangi tablicy.
  
 W poniższych deklaracjach druga i trzecia deklaracja generują ten błąd:
  
 `Overloads Sub ProcessArray(arrayParam() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam()() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`  
  
 Druga deklaracja zmienia oryginalny jednowymiarowy parametr `arrayParam` na tablicę tablic. Trzecia deklaracja zmienia `arrayParam` na tablicę dwuwymiarową (ranga 2). Chociaż Visual Basic zezwala na przeciążenia tylko jednej z tych zmian, takie Przeciążenie nie jest zgodne z [niezależnymi od języka i składnikami niezależnymi od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, należy ustawić parametr `isCompliant` atrybutu na `True` lub `False`, aby wskazać zgodność lub niezgodność. Dla tego parametru nie ma wartości domyślnej i należy podać wartość.  
  
 Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> do elementu, jest on uznawany za niezgodny.  
  
 Domyślnie ten komunikat jest ostrzeżeniem. Aby uzyskać informacje na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40035  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Jeśli jest wymagana zgodność ze specyfikacją CLS, zdefiniuj przeciążenia tak, aby różnią się od siebie na więcej sposobów niż zmiany wprowadzone na tej stronie pomocy.
- Jeśli wymagane jest, aby przeciążenia różniły się tylko zmianami wprowadzonymi na tej stronie pomocy, Usuń <xref:System.CLSCompliantAttribute> z ich definicji lub Oznacz je jako `<CLSCompliant(False)>`.
  
## <a name="see-also"></a>Zobacz także

- [Przeciążanie procedury](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [Przeciążenia](../modifiers/overloads.md)
