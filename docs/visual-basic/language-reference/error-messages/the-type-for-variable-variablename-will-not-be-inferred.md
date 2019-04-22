---
title: Typ zmiennej „<variablename>” nie zostanie wywnioskowany, ponieważ jest powiązany z polem w zakresie otaczającym
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: bcd142785d8ee736c6a1b41950fae80e4d26fa18
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838823"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>Typ zmiennej "\<nazwa_zmiennej >' nie zostanie wywnioskowany, ponieważ jest on powiązany z polem w zakresie otaczającym
Typ zmiennej "\<nazwa_zmiennej >' nie zostanie wywnioskowany, ponieważ jest on powiązany z polem w zakresie otaczającym. Zmień nazwę "\<nazwa_zmiennej >", lub użyj w pełni kwalifikowana nazwa (na przykład "Me.variablename" lub "MyBase.variablename").  
  
 Zmienna sterująca pętli w kodzie ma taką samą nazwę jako pola klasy lub innego zasięgu. Ponieważ zmienna sterująca jest używany bez `As` klauzula jest powiązany z polem w zasięgu, a kompilator nie tworzy nową zmienną dla niego ani nie wywnioskować jej typu.  
  
 W poniższym przykładzie `Index`, zmienna sterująca w `For` instrukcji, jest powiązany z `Index` pole `Customer` klasy. Kompilator nie tworzy nową zmienną dla zmienna sterująca `Index` lub wywnioskować jej typu.  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Aby uzyskać informacji na temat sposobu Ukryj ostrzeżenia lub jak Traktuj ostrzeżenia jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42110  
  
### <a name="to-address-this-warning"></a>Aby rozwiązać tego ostrzeżenia  
  
-   Zmienna sterująca pętli należy lokalnych, zmieniając jej nazwę na identyfikator, który nie jest również nazwę pola klasy.  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   Wyjaśnienie, że zmienna sterująca pętli wiąże pola klasy przez dodanie przedrostka `Me.` do nazwy zmiennej.  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   Zamiast polegania na wnioskowanie o typie lokalnym, użyj `As` klauzuli, aby określić typ zmienna sterująca pętli.  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia wcześniejszy przykład przy pierwszym korekcji w miejscu.  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>Zobacz także

- [Option Infer, instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Instrukcje: Odwoływanie się do bieżącego wystąpienia obiektu](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Me, My, MyBase i MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
