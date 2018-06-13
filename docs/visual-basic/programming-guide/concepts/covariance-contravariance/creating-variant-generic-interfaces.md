---
title: Tworzenie interfejsów ogólnych typu Variant (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: 9e79183cd75e3e222cfa82c6b8ca651eb99ffc02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643890"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>Tworzenie interfejsów ogólnych typu Variant (Visual Basic)
Można zadeklarować parametry typu ogólnego w interfejsach jako kowariantnego lub kontrawariantnego. *Kowariancja* umożliwia metod interfejsu do bardziej pochodnego zwracanych typów niż określone przez parametry typu ogólnego. *Kontrawariancja* umożliwia metod interfejsu do typy argumentu są mniej pochodnego od określonej przez parametry ogólne. Ogólny interfejs, który ma kowariantnego lub kontrawariantnego parametry typu ogólnego jest nazywany *variant*.  
  
> [!NOTE]
>  .NET framework 4 wprowadzono obsługę wariancji w kilku interfejsach istniejących. Aby uzyskać listę interfejsów typu variant w programie .NET Framework, zobacz [wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="declaring-variant-generic-interfaces"></a>Deklarujący interfejsów ogólnych typu Variant  
 Interfejsów ogólnych typu variant można zadeklarować przy użyciu `in` i `out` słowa kluczowe dla parametrów typu ogólnego.  
  
> [!IMPORTANT]
>  `ByRef` Parametry w języku Visual Basic nie może być wariantem. Typy wartości nie obsługują również wariancji.  
  
 Można zadeklarować parametru typu ogólnego kowariantnego przy użyciu `out` — słowo kluczowe. Kowariantnego typu muszą spełniać następujące warunki:  
  
-   Typ jest używany tylko jako typ zwracany metody interfejsu i nie jest używany jako typ argumentów metody. Jest to zilustrowane w poniższym przykładzie, w którym typ `R` zadeklarowano kowariantny.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Function GetSomething() As R  
        ' The following statement generates a compiler error.  
        ' Sub SetSomething(ByVal sampleArg As R)  
    End Interface  
    ```  
  
     Istnieje jeden wyjątek od tej reguły. Jeśli masz to delegat generyczny kontrawariantnego jako parametr metody dla obiekt delegowany mogą używać typu co parametr typu ogólnego. Jest to zilustrowane przez typ `R` w poniższym przykładzie. Aby uzyskać więcej informacji, zobacz [wariancji w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [wariancji Func i akcji Delegaty ogólne (Visual Basic) przy użyciu](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        Sub DoSomething(ByVal callback As Action(Of R))  
    End Interface  
    ```  
  
-   Typ nie jest używany jako ogólne ograniczenia dla metod interfejsu. Jest to zilustrowane w poniższym kodzie.  
  
    ```vb  
    Interface ICovariant(Of Out R)  
        ' The following statement generates a compiler error  
        ' because you can use only contravariant or invariant types  
        ' in generic contstraints.  
        ' Sub DoSomething(Of T As R)()  
    End Interface  
    ```  
  
 Można zadeklarować kontrawariantnego parametru typu ogólnego przy użyciu `in` — słowo kluczowe. Typ kontrawariantnego może służyć jedynie jako typ argumenty metody, a nie typu zwracanego metody interfejsu. Można także kontrawariantnego typu dla ograniczenia ogólne. Poniższy kod przedstawia sposób zadeklarować interfejsu kontrawariantnego i użyć ogólne ograniczenia dla jednej z metod.  
  
```vb  
Interface IContravariant(Of In A)  
    Sub SetSomething(ByVal sampleArg As A)  
    Sub DoSomething(Of T As A)()  
    ' The following statement generates a compiler error.  
    ' Function GetSomething() As A  
End Interface  
```  
  
 Istnieje również możliwość obsługuje zarówno Kowariancja i kontrawariancja w ten sam interfejs, ale dla różnych typów parametrów, jak pokazano w poniższym przykładzie kodu.  
  
```vb  
Interface IVariant(Of Out R, In A)  
    Function GetSomething() As R  
    Sub SetSomething(ByVal sampleArg As A)  
    Function GetSetSomething(ByVal sampleArg As A) As R  
End Interface  
```  
  
 W języku Visual Basic nie można zadeklarować zdarzenia w interfejsach variant bez określania typu delegowanego. Ponadto variant interfejsu nie mogą mieć zagnieżdżonych klas, wyliczeń lub struktury, ale można mieć zagnieżdżonych interfejsów. Jest to zilustrowane w poniższym kodzie.  
  
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
  
## <a name="implementing-variant-generic-interfaces"></a>Implementującej interfejsów ogólnych typu Variant  
 Zaimplementowanie interfejsów ogólnych typu variant w klasach przy użyciu składni, która jest używana dla niezmiennej interfejsów. Poniższy przykład kodu pokazuje, jak do zaimplementowania w klasie rodzajowej kowariantnego interfejsu.  
  
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
  
 Klasy, które implementują interfejsów typu variant są niezmienne. Rozważmy na przykład następujący kod.  
  
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
 Podczas rozszerzania typu variant interfejs ogólny, należy użyć `in` i `out` słów kluczowych, aby jawnie określić, czy interfejsu pochodnego obsługuje wariancji. Kompilator wariancję z interfejsu, który zostanie rozszerzone nie są rozpoznawane. Na przykład należy wziąć pod uwagę następujące interfejsy.  
  
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
  
 W `Invariant(Of T)` interfejsu, parametru typu ogólnego `T` jest niezmienne, natomiast w `IExtCovariant (Of Out T)`parametr typu jest kowariantny, mimo że oba interfejsy rozszerzenia tego samego interfejsu. Ta zasada dotyczy kontrawariantnego parametry typu ogólnego.  
  
 Można utworzyć interfejs, który rozszerza interfejs gdzie parametr typu ogólnego `T` jest kowariantny i interfejsu, w której jest kontrawariantny Jeśli rozszerzenie interfejsu parametr typu ogólnego `T` jest niezmienne. Jest to zilustrowane w poniższym przykładzie kodu.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
Interface IContravariant(Of In T)  
End Interface  
  
Interface IInvariant(Of T)  
    Inherits ICovariant(Of T), IContravariant(Of T)  
End Interface  
```  
  
 Jednak jeśli parametr typu ogólnego `T` jest zadeklarowana kowariantnego w jeden interfejs, nie można zadeklarować go kontrawariantnego w interfejsie rozszerzanie lub na odwrót. Jest to zilustrowane w poniższym przykładzie kodu.  
  
```vb  
Interface ICovariant(Of Out T)  
End Interface  
  
' The following statements generate a compiler error.  
' Interface ICoContraVariant(Of In T)  
'     Inherits ICovariant(Of T)  
' End Interface  
```  
  
### <a name="avoiding-ambiguity"></a>Unikanie niejednoznaczności  
 Podczas implementowania interfejsów ogólnych typu variant wariancję czasami może prowadzić do niejednoznaczności. Należy unikać to.  
  
 Na przykład jawnie w przypadku zastosowania tego samego typu variant interfejsu ogólne z parametrami innego typu ogólnego w jedną klasę, można utworzyć niejednoznaczności. Kompilator nie tworzy w tym przypadku błąd, ale nie określono implementacji interfejsu, który zostanie wybrany w czasie wykonywania. Może to prowadzić do subtelnych błędów w kodzie. Rozważmy poniższy przykład kodu.  
  
> [!NOTE]
>  Z `Option Strict Off`, Visual Basic generuje ostrzeżenie kompilatora po implementacji interfejsu niejednoznaczne. Z `Option Strict On`, Visual Basic generuje błąd kompilatora.  
  
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
  
 W tym przykładzie jest nieokreślony sposób `pets.GetEnumerator` metody wybierze między `Cat` i `Dog`. Może to spowodować problemy w kodzie.  
  
## <a name="see-also"></a>Zobacz też  
 [Wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [Korzystanie z wariancji dla Func i akcji Delegaty ogólne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
