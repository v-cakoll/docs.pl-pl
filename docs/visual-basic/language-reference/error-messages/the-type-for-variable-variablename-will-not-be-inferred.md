---
title: "Typ zmiennej &#39; &lt;nazwa_zmiennej&gt;&#39; nie będzie można wywnioskować, ponieważ jest on powiązany z polem w otaczającym zakresie"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords: BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39968407f4de5436df324320c99dede4d72e2808
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>Typ zmiennej &#39; &lt;nazwa_zmiennej&gt;&#39; nie będzie można wywnioskować, ponieważ jest on powiązany z polem w otaczającym zakresie
Typ zmiennej "\<nazwa_zmiennej >' nie będzie można wywnioskować, ponieważ jest on powiązany z polem w otaczającym zakresie. Zmień nazwę "\<nazwa_zmiennej >", lub użyj w pełni kwalifikowaną nazwę (na przykład "Me.variablename" lub "MyBase.variablename").  
  
 Zmienna sterująca pętli w kodzie ma taką samą nazwę pola klasy lub innych otaczającego zakresu. Ponieważ zmiennej formantu jest używana bez `As` klauzuli jest powiązany z polem w otaczającym zakresie, a kompilator nie jest w stanie utworzyć nową zmienną dla niego lub wywnioskować jej typu.  
  
 W poniższym przykładzie `Index`, zmienna sterująca w `For` instrukcji, jest powiązany z `Index` w `Customer` klasy. Kompilator nie tworzy nową zmienną dla zmiennej formantu `Index` lub wywnioskować jej typu.  
  
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
  
 Domyślnie ten komunikat jest ostrzeżenie. Informacje o Ukryj ostrzeżenia lub Traktuj ostrzeżenia jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42110  
  
### <a name="to-address-this-warning"></a>W celu rozwiązania tego ostrzeżenia  
  
-   Zmienna sterująca pętli należy lokalnego, zmieniając jej nazwę na identyfikator, który nie jest również nazwę pola klasy.  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   Wyjaśnienie, że zmienna sterująca pętli for jest powiązany z pola klasy, prefiksu `Me.` do nazwy zmiennej.  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   Zamiast polegania na wnioskowanie o typie lokalnym, użyj `As` klauzuli, aby określić typ dla zmienna sterująca pętli for.  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia wcześniejszego przykładu z pierwszego korekty w miejscu.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Option Infer — instrukcja](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [For Each... Next — instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Dla... Next — instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Porady: odwoływanie się do bieżącego wystąpienia obiektu](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Me, My, MyBase i MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
