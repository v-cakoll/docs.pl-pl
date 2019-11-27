---
title: Wariancje w delegatach
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 11146bc4a60f55fc0373f0b5dfa5d44dcf748a5b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349000"
---
# <a name="variance-in-delegates-visual-basic"></a>Wariancja w delegatach (Visual Basic)

W .NET Framework 3,5 wprowadzono obsługę wariancji dla pasujących sygnatur metod z typami delegatów C# we wszystkich delegatach w i Visual Basic. Oznacza to, że można przypisać do delegatów nie tylko metod, które mają pasujące podpisy, ale również metody, które zwracają więcej typów pochodnych (Kowariancja) lub akceptują parametry, które mają mniej pochodne typy (kontrawariancja) niż określone przez typ delegata . Dotyczy to zarówno delegatów rodzajowych, jak i nieogólnych.

Rozważmy na przykład poniższy kod, który ma dwie klasy i dwa Delegaty: generyczne i nieogólne.

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

Podczas tworzenia delegatów typów `SampleDelegate` lub `SampleDelegate(Of A, R)` można przypisać do tych delegatów jedną z następujących metod.

```vb
' Matching signature.
Public Shared Function ASecondRFirst(
    ByVal second As Second) As First
    Return New First()
End Function

' The return type is more derived.
Public Shared Function ASecondRSecond(
    ByVal second As Second) As Second
    Return New Second()
End Function

' The argument type is less derived.
Public Shared Function AFirstRFirst(
    ByVal first As First) As First
    Return New First()
End Function

' The return type is more derived
' and the argument type is less derived.
Public Shared Function AFirstRSecond(
    ByVal first As First) As Second
    Return New Second()
End Function
```

Poniższy przykład kodu ilustruje niejawną konwersję między sygnaturą metody a typem delegata.

```vb
' Assigning a method with a matching signature
' to a non-generic delegate. No conversion is necessary.
Dim dNonGeneric As SampleDelegate = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a non-generic delegate.
' The implicit conversion is used.
Dim dNonGenericConversion As SampleDelegate = AddressOf AFirstRSecond

' Assigning a method with a matching signature to a generic delegate.
' No conversion is necessary.
Dim dGeneric As SampleGenericDelegate(Of Second, First) = AddressOf ASecondRFirst
' Assigning a method with a more derived return type
' and less derived argument type to a generic delegate.
' The implicit conversion is used.
Dim dGenericConversion As SampleGenericDelegate(Of Second, First) = AddressOf AFirstRSecond
```

Aby uzyskać więcej przykładów, zobacz [Korzystanie z wariancji w delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) i [Używanie wariancji dla delegatów funkcji Func i Action (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

## <a name="variance-in-generic-type-parameters"></a>Wariancja w parametrach typu ogólnego

W .NET Framework 4 i nowszych można włączyć niejawną konwersję między delegatami, tak aby generyczne Delegaty mające różne typy określone przez parametry typu generycznego można przypisać do siebie nawzajem, jeśli typy są dziedziczone od siebie, zgodnie z wymaganiami względem.

Aby włączyć niejawną konwersję, należy jawnie zadeklarować parametry ogólne w delegatze jako współvariant lub kontrawariantne za pomocą słowa kluczowego `in` lub `out`.

Poniższy przykład kodu pokazuje, jak można utworzyć delegata, który ma parametr typu ogólnego.

```vb
' Type T is declared covariant by using the out keyword.
Public Delegate Function SampleGenericDelegate(Of Out T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "
    ' You can assign delegates to each other,
    ' because the type T is declared covariant.
    Dim dObject As SampleGenericDelegate(Of Object) = dString
End Sub
```

Jeśli używasz tylko wariancji do dopasowywania sygnatur metod z typami delegatów i nie używaj `in` i `out` słowa kluczowe, może się okazać, że czasami można utworzyć wystąpienia delegatów z identycznymi wyrażeniami lambda lub metodami, ale nie można przypisać jednego delegata do innego.

W poniższym przykładzie kodu `SampleGenericDelegate(Of String)` nie można jawnie przekonwertować na `SampleGenericDelegate(Of Object)`, chociaż `String` dziedziczy `Object`. Możesz rozwiązać ten problem, zaznaczając parametr generyczny `T` za pomocą słowa kluczowego `out`.

```vb
Public Delegate Function SampleGenericDelegate(Of T)() As T
Sub Test()
    Dim dString As SampleGenericDelegate(Of String) = Function() " "

    ' You can assign the dObject delegate
    ' to the same lambda expression as dString delegate
    ' because of the variance support for
    ' matching method signatures with delegate types.
    Dim dObject As SampleGenericDelegate(Of Object) = Function() " "

    ' The following statement generates a compiler error
    ' because the generic type T is not marked as covariant.
    ' Dim dObject As SampleGenericDelegate(Of Object) = dString

End Sub
```

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Delegaty ogólne, które mają parametry typu Variant w .NET Framework

.NET Framework 4 wprowadził obsługę wariancji dla parametrów typu ogólnego w kilku istniejących delegatach ogólnych:

- `Action` delegatów z przestrzeni nazw <xref:System>, na przykład <xref:System.Action%601> i <xref:System.Action%602>

- `Func` delegatów z przestrzeni nazw <xref:System>, na przykład <xref:System.Func%601> i <xref:System.Func%602>

- Delegat <xref:System.Predicate%601>

- Delegat <xref:System.Comparison%601>

- Delegat <xref:System.Converter%602>

Aby uzyskać więcej informacji i zapoznać się z przykładami, zobacz [using WARIANCJA dla delegatów "Func" i "Akcja" (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarowanie parametrów typu Variant w delegatach generycznych

Jeśli delegat generyczny ma parametry typu generycznego lub kontrawariantne, może być określany jako *Delegat generyczny elementu Variant*.

Za pomocą słowa kluczowego `out` można zadeklarować współwariant parametru typu ogólnego w delegatze ogólnym. Typ współwariantu może być używany tylko jako zwracany typ metody, a nie jako typ argumentów metody. Poniższy przykład kodu pokazuje, jak zadeklarować delegata generycznego.

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

Parametry typu ogólnego kontrawariantne można zadeklarować w delegatze ogólnym za pomocą słowa kluczowego `in`. Typ kontrawariantne może być używany tylko jako typ argumentów metody, a nie jako zwracany typ metody. Poniższy przykład kodu pokazuje, jak zadeklarować delegata generycznego kontrawariantne.

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> parametrów `ByRef` w Visual Basic nie można oznaczyć jako VARIANT.

Istnieje również możliwość obsługi zarówno wariancji, jak i kowariancji w tym samym delegatze, ale dla różnych parametrów typu. Pokazano to w poniższym przykładzie.

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Tworzenie wystąpień i wywoływanie delegatów ogólnych typu Variant

Można tworzyć wystąpienia delegatów wariantów i wywoływać je tak samo jak w przypadku wystąpienia i wywoływać delegatów niezmiennej. W poniższym przykładzie obiekt delegowany jest tworzone przez wyrażenie lambda.

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a>Łączenie delegatów ogólnych typu Variant

Nie należy łączyć delegatów wariantów. Metoda <xref:System.Delegate.Combine%2A> nie obsługuje konwersji delegata typu Variant i oczekuje, że Delegaty będą dokładnie tego samego typu. Może to prowadzić do wyjątku czasu wykonywania podczas łączenia delegatów za pomocą metody <xref:System.Delegate.Combine%2A> (w C# i Visual Basic) lub przy użyciu operatora `+` (w C#), jak pokazano w poniższym przykładzie kodu.

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Wariancja w parametrach typu ogólnego dla typów wartości i odwołań

WARIANCJA dla parametrów typu ogólnego jest obsługiwana tylko w przypadku typów referencyjnych. Na przykład `DVariant(Of Int)`nie może być niejawnie konwertowany na `DVariant(Of Object)` lub `DVariant(Of Long)`, ponieważ liczba całkowita jest typem wartości.

W poniższym przykładzie pokazano, że Wariancja w parametrach typu ogólnego nie jest obsługiwana w przypadku typów wartości.

```vb
' The type T is covariant.
Public Delegate Function DVariant(Of Out T)() As T
' The type T is invariant.
Public Delegate Function DInvariant(Of T)() As T
Sub Test()
    Dim i As Integer = 0
    Dim dInt As DInvariant(Of Integer) = Function() i
    Dim dVariantInt As DVariant(Of Integer) = Function() i

    ' All of the following statements generate a compiler error
    ' because type variance in generic parameters is not supported
    ' for value types, even if generic type parameters are declared variant.
    ' Dim dObject As DInvariant(Of Object) = dInt
    ' Dim dLong As DInvariant(Of Long) = dInt
    ' Dim dVariantObject As DInvariant(Of Object) = dInt
    ' Dim dVariantLong As DInvariant(Of Long) = dInt
End Sub
```

## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Swobodna konwersja delegata w Visual Basic

Swobodna konwersja delegatów umożliwia większą elastyczność w dopasowaniu sygnatur metod z typami delegatów. Na przykład pozwala pominąć specyfikacje parametrów i pomijać wartości zwracane przez funkcję przy przypisywaniu metody do delegata. Aby uzyskać więcej informacji, zobacz [Swobodna konwersja delegata](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).

## <a name="see-also"></a>Zobacz także

- [Typy ogólne](../../../../standard/generics/index.md)
- [Korzystanie z wariancji dla delegatów "Func" i "Action Generic" (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
