---
title: Tworzenie interfejsów typu Variant (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: d6afddf018b4608418f82fa851d018f2c3e1d0fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663261"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>Tworzenie interfejsów typu Variant (Visual Basic)
Możesz deklarować parametry typu ogólnego w interfejsach jako kowariantny lub kontrawariantny. *Kowariancja* umożliwia metod interfejsu do mają bardziej pochodne typy zwracane niż określone przez parametry typu ogólnego. *Kontrawariancja* umożliwia metod interfejsu mieć typy argumentów, które są mniej pochodnego niż określona przez parametry ogólne. Ogólny interfejs, który ma kowariantne i kontrawariantne parametry typu ogólnego jest nazywany *wariant*.  
  
> [!NOTE]
>  .NET framework 4 wprowadzono wariancji obsługę kilka istniejących interfejsów ogólnych. Aby uzyskać listę interfejsów typu variant w programie .NET Framework, zobacz [wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="declaring-variant-generic-interfaces"></a>Deklarujący interfejsów ogólnych typu Variant  
 Można zadeklarować interfejsów ogólnych typu variant, za pomocą `in` i `out` słowa kluczowe dla parametrów typu genetycznego.  
  
> [!IMPORTANT]
>  `ByRef` w języku Visual Basic nie może być typ variant. Typy wartości nie obsługują także wariancji.  
  
 Można zadeklarować parametru typu generycznego kowariantne przy użyciu `out` — słowo kluczowe. Kowariantnego typu musi spełniać następujące warunki:  
  
-   Typ jest używany tylko jako zwracany typ metody interfejsu i nie jest używany jako typ argumentów metody. Jest to zilustrowane w poniższym przykładzie, w którym typ `R` jest zadeklarowany jako kowariantny.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     Istnieje jeden wyjątek od tej reguły. Jeśli Delegat ogólny kontrawariantny, jako parametru metody, można użyć typu co parametr typu ogólnego, dla delegata. Jest to zilustrowane przez typ `R` w poniższym przykładzie. Aby uzyskać więcej informacji, zobacz [wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancji dla akcji delegatów ogólnych (Visual Basic) Func i](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   Typ nie jest używany jako ograniczenia typu ogólnego dla metod interfejsu. Jest to zilustrowane w poniższym kodzie.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 Można zadeklarować kontrawariantnego parametru typu ogólnego przy użyciu `in` — słowo kluczowe. Typ kontrawariantne może służyć jedynie jako typów argumentów metody, a nie typu zwracanego metody interfejsu. Można także kontrawariantnego typu dla ograniczenia ogólne. Poniższy kod przedstawia sposób deklarowania interfejsu kontrawariantnego i na użytek ograniczenie generyczne jednej z jego metod.  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 Istnieje również możliwość obsługuje zarówno kowariancji i kontrawariancji w ten sam interfejs, ale dla parametrów innego typu, jak pokazano w poniższym przykładzie kodu.  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 W języku Visual Basic nie można zadeklarować zdarzenia w interfejsów typu variant, bez określania typu delegata. Ponadto wariantu interfejsu nie mogą zagnieżdżać klas, wyliczeń lub struktur, ale mogą być zagnieżdżone interfejsów. Jest to zilustrowane w poniższym kodzie.  
  
```vb  
Interface ICovariant(Of Out R)  
    ' The following statement generates a compiler error.  
    ' Event SampleEvent()  
    ' The following statement specifies the delegate type and   
    ' does not generate an error.  
    Event AnotherEvent As EventHandler  
  
    ' The following statements generate compiler errors,  
    ' because a variant interface cannot have  
    ' nested enums, classes, or structures.  
  
    'Enum SampleEnum : test : End Enum  
    'Class SampleClass : End Class  
    'Structure SampleStructure : Dim value As Integer : End Structure  
  
    ' Variant interfaces can have nested interfaces.  
    Interface INested : End Interface  
End Interface  
```  
  
## <a name="implementing-variant-generic-interfaces"></a>Implementowanie interfejsów ogólnych typu Variant  
 Możesz zaimplementować interfejsów ogólnych typu variant klas przy użyciu składni, która jest używana niezmienna interfejsów. Poniższy przykład kodu pokazuje sposób implementacji kowariantne interfejsu w klasie ogólnej.  
  
```vb  
Interface ICovariant(Of Out R)  
    Function GetSomething() As R  
End Interface  
  
Class SampleImplementation(Of R)  
    Implements ICovariant(Of R)  
    Public Function GetSomething() As R _  
    Implements ICovariant(Of R).GetSomething  
        ' Some code.  
    End Function  
End Class  
```  
  
 Klasy, które implementują interfejsów typu variant są niezmienne. Rozważmy na przykład, poniższy kod.  
  
```vb  
 The interface is covariant.  
Dim ibutton As ICovariant(Of Button) =  
    New SampleImplementation(Of Button)  
Dim iobj As ICovariant(Of Object) = ibutton  
  
' The class is invariant.  
Dim button As SampleImplementation(Of Button) =  
    New SampleImplementation(Of Button)  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim obj As SampleImplementation(Of Object) = button  
```  
  
## <a name="extending-variant-generic-interfaces"></a>Rozszerzanie interfejsów ogólnych typu Variant  
 Podczas rozszerzania typu variant interfejs ogólny, trzeba użyć `in` i `out` słów kluczowych, aby jawnie określić, czy interfejsu pochodnego obsługuje wariancji. Kompilator nie są rozpoznawane przez odchylenie od interfejsu, który jest rozszerzany. Na przykład należy wziąć pod uwagę następujące interfejsy.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T)  
End Interface  
  
Interface IExtCovariant(Of Out T)  
    Inherits ICovariant(Of T)  
End Interface  
```  
  
 W `Invariant(Of T)` interfejsu, parametr typu ogólnego `T` jest niezmienny, natomiast w `IExtCovariant (Of Out T)`parametr typu jest kowariantny, mimo że oba interfejsy rozszerzyć ten sam interfejs. Ta sama zasada dotyczy kontrawariantne parametry typu ogólnego.  
  
 Można utworzyć interfejsu, który rozszerza interfejs gdzie parametr typu ogólnego `T` jest kowariantny interfejs, w której jest kontrawariantny w rozszerzanie interfejsu parametr typu ogólnego i `T` jest niezmienny. Jest to zilustrowane w poniższym przykładzie kodu.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 Jednak jeśli parametr typu ogólnego `T` jest kowariantny zadeklarowana w ramach jednego interfejsu, nie można zadeklarować je kontrawariantnego w interfejsie rozszerzanie lub na odwrót. Jest to zilustrowane w poniższym przykładzie kodu.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a>Unikanie niejednoznaczności  
 Podczas implementowania interfejsów ogólnych typu variant wariancji czasami może prowadzić do niejednoznaczności. Należy ich unikać.  
  
 Na przykład w przypadku zastosowania jawnie tego samego typu variant ogólny interfejs z parametrami typu rodzajowego różnych w jednej klasie, można utworzyć niejednoznaczności. Kompilator generuje błąd w takiej sytuacji, ale nie zostanie określony, zostanie wybrany co do implementacji interfejsu w czasie wykonywania. Może to prowadzić do subtelnych błędów w kodzie. Rozważmy następujący przykład kodu.  
  
> [!NOTE]
>  Za pomocą `Option Strict Off`, Visual Basic generuje ostrzeżenia kompilatora, gdy jest implementacją interfejsu niejednoznaczne. Za pomocą `Option Strict On`, Visual Basic generuje błąd kompilatora.  
  
```vb  
' Simple class hierarchy.  
Class Animal  
End Class  
  
Class Cat  
    Inherits Animal  
End Class  
  
Class Dog  
    Inherits Animal  
End Class  
  
' This class introduces ambiguity  
' because IEnumerable(Of Out T) is covariant.  
Class Pets  
    Implements IEnumerable(Of Cat), IEnumerable(Of Dog)  
  
    Public Function GetEnumerator() As IEnumerator(Of Cat) _  
        Implements IEnumerable(Of Cat).GetEnumerator  
        Console.WriteLine("Cat")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator1() As IEnumerator(Of Dog) _  
        Implements IEnumerable(Of Dog).GetEnumerator  
        Console.WriteLine("Dog")  
        ' Some code.  
    End Function  
  
    Public Function GetEnumerator2() As IEnumerator _  
        Implements IEnumerable.GetEnumerator  
        ' Some code.  
    End Function  
End Class  
  
Sub Main()  
    Dim pets As IEnumerable(Of Animal) = New Pets()  
    pets.GetEnumerator()  
End Sub  
```  
  
 W tym przykładzie jest nieokreślona sposób, w jaki `pets.GetEnumerator` metoda wybiera między `Cat` i `Dog`. Może to spowodować problemy w kodzie.  
  
## <a name="see-also"></a>Zobacz także
- [Wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Korzystanie z wariancji dla Func i akcji delegatów ogólnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
