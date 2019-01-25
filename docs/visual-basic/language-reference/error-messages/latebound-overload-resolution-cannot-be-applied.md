---
title: Nie można zastosować przeciążenia późnego &#39; &lt;nazwaprocedury&gt; &#39; ponieważ wystąpienie uzyskujące dostęp jest typem interfejsu
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: db0ce88f63be8d58cc1c1abf91eda6a0e56456c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651521"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a>Nie można zastosować przeciążenia późnego &#39; &lt;nazwaprocedury&gt; &#39; ponieważ wystąpienie uzyskujące dostęp jest typem interfejsu
Kompilator próbuje rozpoznać odwołania do elementu przeciążona właściwość lub procedura, ale odwołania nie powiedzie się, ponieważ typ argumentu jest `Object` i odwołuje się do innych obiektów o typie danych interfejsu. `Object` Argument wymusza na kompilatorze rozpoznać odwołania jako z późnym wiązaniem.  
  
 W tych okolicznościach kompilator rozpoznaje przeciążenia za pośrednictwem klasy implementującej zamiast za pośrednictwem powiązanego interfejsu. Jeśli klasa zmieni nazwę jednego z przeciążone wersje, kompilator nie bierze pod uwagę tej wersji na przeciążenie, ponieważ jego nazwa różni się. To z kolei powoduje, że kompilator ignoruje wersji zmieniono nazwy, gdy było odpowiedni wybór można rozpoznać odwołania.  
  
 **Identyfikator błędu:** BC30933  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj `CType` rzutowanie argumentów z `Object` do typu określonego przez podpis przeładowania ma zostać wywołana.  
  
     Należy pamiętać, że nie jest pomocne można rzutować obiektu odwołujący się do interfejsu podstawowego. Należy rzutować argumentów, aby uniknąć tego błędu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano wywołanie przeciążonej `Sub` procedury, która powoduje, że ten błąd w czasie kompilacji.  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 W poprzednim przykładzie, jeśli kompilator może wywołanie `s1` w rozdzielczości nastąpi za pośrednictwem klasy `c1` zamiast interfejsu `i1`. To oznacza, że kompilator będzie nie bierze pod uwagę `s2` , ponieważ jego nazwa różni się w `c1`, nawet jeśli jest to poprawny wybór, zgodnie z definicją `i1`.  
  
 Błąd można rozwiązać, zmieniając wywołania do jednej z następujących wierszy kodu:  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 Każdy z poprzednich wierszy kodu jawnie rzutuje `Object` zmiennej `o1` do jednego z typów parametrów zdefiniowanych dla przeciążenia.  
  
## <a name="see-also"></a>Zobacz także
- [Przeciążanie procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Rozpoznanie przeciążenia](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)
