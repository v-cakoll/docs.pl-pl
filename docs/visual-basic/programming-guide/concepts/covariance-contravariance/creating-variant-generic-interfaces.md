---
title: Tworzenie interfejsów ogólnych typu Variant
ms.date: 07/20/2015
ms.assetid: d4037dd2-dfe9-4811-9150-93d4e8b20113
ms.openlocfilehash: 884349159d2738d8481b217f9dab383483616f2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400645"
---
# <a name="creating-variant-generic-interfaces-visual-basic"></a>Tworzenie interfejsów ogólnych typu Variant (Visual Basic)

Parametry typu ogólnego można zadeklarować w interfejsach jako współvariant lub kontrawariantne. *Kowariancja* umożliwia metodom interfejsu posiadanie bardziej pochodnych typów zwracanych niż te zdefiniowane przez parametry typu ogólnego. *Kontrawariancja* umożliwia metodom interfejsu posiadanie typów argumentów, które są mniej pochodne niż określone przez parametry ogólne. Ogólny interfejs, który ma parametry typu generycznego lub kontrawariantne, nazywa się *wariantem*.

> [!NOTE]
> .NET Framework 4 wprowadziła obsługę wariancji dla kilku istniejących interfejsów ogólnych. Aby uzyskać listę interfejsów wariantów w .NET Framework, zobacz [Wariancja w interfejsach ogólnych (Visual Basic)](variance-in-generic-interfaces.md).

## <a name="declaring-variant-generic-interfaces"></a>Deklarowanie interfejsów ogólnych typu Variant

Można zadeklarować interfejsy ogólne wariantu przy użyciu `in` `out` słów kluczowych i dla parametrów typu ogólnego.

> [!IMPORTANT]
> `ByRef`parametry w Visual Basic nie mogą być wariantem. Typy wartości nie obsługują również wariancji.

Za pomocą słowa kluczowego można zadeklarować współwariant parametru typu ogólnego `out` . Typ współwariantu musi spełniać następujące warunki:

- Typ jest używany tylko jako typ zwracany metod interfejsu i nie jest używany jako typ argumentów metody. Jest to zilustrowane w poniższym przykładzie, w którym typ `R` jest zadeklarowany jako współvariant.

    ```vb
    Interface ICovariant(Of Out R)
        Function GetSomething() As R
        ' The following statement generates a compiler error.
        ' Sub SetSomething(ByVal sampleArg As R)
    End Interface
    ```

    Istnieje jeden wyjątek dla tej reguły. Jeśli masz delegata generycznego kontrawariantne jako parametr metody, możesz użyć typu jako parametru typu ogólnego dla delegata. Jest to zilustrowane przez typ `R` w poniższym przykładzie. Aby uzyskać więcej informacji, zobacz [Wariancja w delegatach (Visual Basic)](variance-in-delegates.md) i [Korzystanie z wariancji dla delegatów "Func" i "Action Generic" (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).

    ```vb
    Interface ICovariant(Of Out R)
        Sub DoSomething(ByVal callback As Action(Of R))
    End Interface
    ```

- Typ nie jest używany jako ograniczenie ogólne metod interfejsu. Jest to zilustrowane w poniższym kodzie.

    ```vb
    Interface ICovariant(Of Out R)
        ' The following statement generates a compiler error
        ' because you can use only contravariant or invariant types
        ' in generic constraints.
        ' Sub DoSomething(Of T As R)()
    End Interface
    ```

Parametry typu ogólnego kontrawariantne można zadeklarować za pomocą `in` słowa kluczowego. Typ kontrawariantne może być używany tylko jako typ argumentów metody, a nie jako zwracany typ metod interfejsu. Typ kontrawariantne może być również używany dla ograniczeń ogólnych. Poniższy kod przedstawia sposób deklarowania interfejsu kontrawariantne i używania ograniczenia ogólnego dla jednej z jej metod.

```vb
Interface IContravariant(Of In A)
    Sub SetSomething(ByVal sampleArg As A)
    Sub DoSomething(Of T As A)()
    ' The following statement generates a compiler error.
    ' Function GetSomething() As A
End Interface
```

Istnieje również możliwość obsługi zarówno kowariancji, jak i kontrawariancja w tym samym interfejsie, ale dla różnych parametrów typu, jak pokazano w poniższym przykładzie kodu.

```vb
Interface IVariant(Of Out R, In A)
    Function GetSomething() As R
    Sub SetSomething(ByVal sampleArg As A)
    Function GetSetSomething(ByVal sampleArg As A) As R
End Interface
```

W Visual Basic nie można zadeklarować zdarzeń w interfejsach Variant bez określania typu delegata. Ponadto interfejs wariantu nie może mieć klas zagnieżdżonych, wyliczeniowych ani struktur, ale może mieć zagnieżdżone interfejsy. Jest to zilustrowane w poniższym kodzie.

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

W klasach można zaimplementować interfejsy ogólne o zmiennej, korzystając z tej samej składni, która jest używana dla interfejsów niezmienna. Poniższy przykład kodu pokazuje, jak zaimplementować interfejs współvariant w klasie generycznej.

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

Klasy implementujące interfejsy Variant są niezmienne. Rozważmy na przykład poniższy kod.

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

Po rozłączeniu uniwersalnego interfejsu wariantowego należy użyć `in` `out` słów kluczowych i, aby jawnie określić, czy interfejs pochodny obsługuje wariancję. Kompilator nie wywnioskuje wariancji z rozszerzanego interfejsu. Rozważmy na przykład następujące interfejsy.

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

W `Invariant(Of T)` interfejsie parametr typu generycznego `T` jest niezmienny, natomiast w `IExtCovariant (Of Out T)` parametrze typu jest współwariant, chociaż oba interfejsy rozszerzającą ten sam interfejs. Ta sama reguła jest stosowana do parametrów typu ogólnego kontrawariantne.

Można utworzyć interfejs, który rozszerza zarówno interfejs, w którym parametr typu generycznego `T` to współwariant, jak i interfejs, w którym jest kontrawariantne, jeśli w rozszerzanym interfejsie parametr typu generycznego `T` jest niezmienny. Jest to zilustrowane w poniższym przykładzie kodu.

```vb
Interface ICovariant(Of Out T)
End Interface

Interface IContravariant(Of In T)
End Interface

Interface IInvariant(Of T)
    Inherits ICovariant(Of T), IContravariant(Of T)
End Interface
```

Jeśli jednak parametr typu generycznego `T` jest zadeklarowany jako współwariant w jednym interfejsie, nie można zadeklarować go kontrawariantne w interfejsie rozszerzającym lub na odwrót. Jest to zilustrowane w poniższym przykładzie kodu.

```vb
Interface ICovariant(Of Out T)
End Interface

' The following statements generate a compiler error.
' Interface ICoContraVariant(Of In T)
'     Inherits ICovariant(Of T)
' End Interface
```

### <a name="avoiding-ambiguity"></a>Unikanie niejednoznaczności

Podczas implementowania interfejsów ogólnych typu Variant WARIANCJA może czasami prowadzić do niejednoznaczności. Należy to uniknąć.

Na przykład w przypadku jawnego zaimplementowania tego samego uniwersalnego interfejsu wariantu z różnymi parametrami typu ogólnego w jednej klasie można utworzyć niejednoznaczność. Kompilator nie generuje błędu w tym przypadku, ale nie jest określony, która implementacja interfejsu zostanie wybrana w czasie wykonywania. Może to prowadzić do delikatnych usterek w kodzie. Spójrz na poniższy przykład kodu.

> [!NOTE]
> W programie `Option Strict Off` Visual Basic generuje ostrzeżenie kompilatora, gdy istnieje niejednoznaczna implementacja interfejsu. W programie `Option Strict On` Visual Basic generuje błąd kompilatora.

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

W tym przykładzie nie określono `pets.GetEnumerator` metody wybieranej między `Cat` i `Dog` . Może to spowodować problemy w kodzie.

## <a name="see-also"></a>Zobacz też

- [Wariancja w interfejsach ogólnych (Visual Basic)](variance-in-generic-interfaces.md)
- [Korzystanie z wariancji dla delegatów "Func" i "Action Generic" (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md)
