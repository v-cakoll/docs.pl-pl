---
title: Ustalanie przeciążenia późnego nie można zastosować do &#39; &lt;nazwaprocedury&gt; &#39; , ponieważ wystąpienie uzyskujące dostęp jest typem interfejsu
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: e41cbf30f06547ef39553e31542e4e8b6df49a3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a>Ustalanie przeciążenia późnego nie można zastosować do &#39; &lt;nazwaprocedury&gt; &#39; , ponieważ wystąpienie uzyskujące dostęp jest typem interfejsu
Kompilator próbuje rozpoznać odwołania do przeciążonej właściwość lub procedura, ale odwołanie nie powiedzie się, ponieważ argument jest typu `Object` i odwołuje się do innych obiektów o typie danych interfejsu. `Object` Argument wymusza na rozpoznania odwołania jako późnym wiązaniem.  
  
 W takiej sytuacji kompilator rozpoznaje przeciążenia za pośrednictwem klasy implementującej zamiast za pośrednictwem powiązanego interfejsu. Jeśli klasa zmienia nazwę jednej z zastąpionej wersji, kompilator nie należy wziąć pod uwagę tej wersji na przeciążenia, ponieważ jego nazwa różni się. To z kolei powoduje, że kompilator ignorować zmienioną nazwę wersji, gdy było poprawne wybór rozpoznać odwołania do.  
  
 **Identyfikator błędu:** BC30933  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj `CType` można rzutować argumentu z `Object` na typ określony przez sygnaturę przeładowania ma zostać wywołana.  
  
     Należy pamiętać, że nie jest pomocne można rzutować obiektu odwołujący się do powiązanego interfejsu. Należy rzutować argumentu, aby uniknąć tego błędu.  
  
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
  
 W poprzednim przykładzie, jeśli kompilator może wywołać `s1` podczas zapisywania, rozdzielczość nastąpi za pośrednictwem klasy `c1` zamiast interfejsu `i1`. To oznacza, że kompilator może nie należy wziąć pod uwagę `s2` jego nazwa różni się w `c1`, nawet jeśli jest to poprawny wybór zgodnie z definicją w `i1`.  
  
 Zmieniając wywołania do jednej z następujących wierszy kodu można poprawić błąd:  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 Każdy z powyższych wierszy kodu jawnie rzutuje `Object` zmiennej `o1` do jednego z typów parametrów zdefiniowanych dla przeciążeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Przeciążanie procedury](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [Rozpoznanie przeciążenia](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)  
 [Funkcja CType](../../../visual-basic/language-reference/functions/ctype-function.md)
