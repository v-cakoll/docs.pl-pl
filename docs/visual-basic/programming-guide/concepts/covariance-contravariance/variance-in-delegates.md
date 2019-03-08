---
title: Wariancje w Delegatach (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 6d341c7c2b5adeebcafc5b0787b132ab6bd57e41
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674279"
---
# <a name="variance-in-delegates-visual-basic"></a>Wariancje w Delegatach (Visual Basic)

.NET framework 3.5 wprowadzono obsługę wariancji podpisów metod dopasowania z typów obiektów delegowanych w wszystkie obiekty delegowane w C# i Visual Basic. Oznacza to, że można przypisać do deleguje nie tylko metody, które pasują do sygnatur, ale także metody, które zwracają więcej pochodne typy (korelacja) lub które przyjmują parametry, które mają mniej pochodne typy (kontrawariancja) niż określona przez typ delegata . Dotyczy to również delegatów ogólnych i nieogólnych.

Na przykład rozważmy następujący kod, który ma dwie klasy i dwa delegaty: ogólnych i nieogólnych.

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

Po utworzeniu delegatów `SampleDelegate` lub `SampleDelegate(Of A, R)` typów, w jednej z następujących metod można przypisać do tych obiektów delegowanych.

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

Poniższy przykład kodu ilustruje niejawna konwersja między podpis metody i typu delegata.

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

Aby uzyskać więcej przykładów, zobacz [przy użyciu wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) i [przy użyciu wariancji dla akcji delegatów ogólnych (Visual Basic) Func i](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

## <a name="variance-in-generic-type-parameters"></a>Wariancji w parametrach typu ogólnego

W programie .NET Framework 4 lub nowszym można włączyć niejawna konwersja między elementem delegatów, dzięki czemu delegatów ogólnych, które mają różne typy określona przez parametry typu ogólnego mogą być przypisane do siebie nawzajem, jeśli typy są dziedziczone od siebie nawzajem, zgodnie z wymaganiami WARIANCJA.

Aby włączyć niejawną konwersję, musisz jawnie deklarować parametrów ogólnych w delegatów jako kowariantnych lub kontrawariantnych przy użyciu `in` lub `out` — słowo kluczowe.

Poniższy przykład kodu pokazuje, jak utworzyć obiekt delegowany mający parametr kowariantnego typu ogólnego.

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

Jeśli używasz obsługują tylko odchylenia do dopasowania podpisy metod ze typy delegatów i nie używaj `in` i `out` słów kluczowych, może się okazać, że czasami można utworzyć wystąpienie obiektów delegowanych z wyrażenia lambda identyczne lub metody, ale nie jest możliwe Przypisz jednego delegata do innego.

W poniższym przykładzie kodu `SampleGenericDelegate(Of String)` nie może być jawnie konwertowane na `SampleGenericDelegate(Of Object)`, mimo że `String` dziedziczy `Object`. Możesz rozwiązać ten problem, oznaczając parametru ogólnego `T` z `out` — słowo kluczowe.

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

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Parametry typu delegatów ogólnych, które mają typ Variant w .NET Framework

.NET framework 4 wprowadzono obsługę wariancji dla parametrów typu rodzajowego w kilku istniejących delegatów ogólnych:

- `Action` delegaty z <xref:System> przestrzeni nazw, na przykład <xref:System.Action%601> i <xref:System.Action%602>

- `Func` delegaty z <xref:System> przestrzeni nazw, na przykład <xref:System.Func%601> i <xref:System.Func%602>

- <xref:System.Predicate%601> Delegowanie

- <xref:System.Comparison%601> Delegowanie

- <xref:System.Converter%602> Delegowanie

Aby uzyskać więcej informacji i przykładów, zobacz [przy użyciu wariancji dla akcji delegatów ogólnych (Visual Basic) Func i](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarowanie Wariantne parametry typu w delegatów ogólnych

Jeśli delegata ogólnego ma kowariantne i kontrawariantne parametry typu ogólnego, jego mogą być określane jako *variant Delegat ogólny*.

Można zadeklarować parametru typu generycznego kowariantne Delegat ogólny przy użyciu `out` — słowo kluczowe. Kowariantnego typu może służyć jedynie jako typ zwracany metody, a nie typu argumentów metody. Poniższy przykład kodu pokazuje sposób deklarowania kowariantne Delegat ogólny.

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

Kontrawariantnego parametru typu ogólnego, Delegat ogólny może zadeklarować za pomocą `in` — słowo kluczowe. Typ kontrawariantne może służyć jedynie jako typów argumentów metody, a nie typem zwracanym metody. Poniższy przykład kodu pokazuje sposób deklarowania to delegat generyczny kontrawariantny.

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> `ByRef` w języku Visual Basic nie można oznaczyć jako wariant.

Istnieje również możliwość obsługi kowariancji i Wariancja w tym samym delegatów, ale w przypadku różnych typów parametrów. Jest to pokazane w poniższym przykładzie.

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Utworzenie wystąpienia i wywoływania wariantów ogólnych delegatów

Można utworzyć wystąpienia i wywoływać delegatów typu variant, tak samo, jak utworzyć wystąpienia i wywoływać delegatów niezmiennej. W poniższym przykładzie delegat jest tworzone przez wyrażenie lambda.

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a>Łączenie delegatów ogólnych typu Variant

Nie należy łączyć wariantu delegatów. <xref:System.Delegate.Combine%2A> Metoda nie obsługuje konwersji typu variant delegata i oczekuje, że delegaty dokładnie tego samego typu. Może to prowadzić do wyjątku czasu wykonywania, podczas łączenia przy użyciu delegatów <xref:System.Delegate.Combine%2A> — metoda (w C# i Visual Basic) lub za pomocą `+` — operator (w C#), jak pokazano w poniższym przykładzie kodu.

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Wariancji w parametrach typu ogólnego dla wartości i typy odwołań

Wariancja dla parametrów typu ogólnego jest obsługiwana tylko dla typów odwołania. Na przykład `DVariant(Of Int)`nie może być niejawnie konwertowane na `DVariant(Of Object)` lub `DVariant(Of Long)`, ponieważ liczba całkowita jest typem wartości.

W poniższym przykładzie pokazano tej wariancji w typie ogólnym parametrów nie jest obsługiwana dla typów wartości.

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

## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Swobodna konwersja delegatów w języku Visual Basic

Swobodna konwersja delegatów umożliwia większą elastyczność w podpisów metod dopasowania z typów obiektów delegowanych. Na przykład dzięki temu można pominąć parametr specyfikacji i pominięto wartości zwracane przez funkcję, gdy przypiszemy metodę do delegata. Aby uzyskać więcej informacji, zobacz [swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).

## <a name="see-also"></a>Zobacz także

- [Typy ogólne](~/docs/standard/generics/index.md)
- [Korzystanie z wariancji dla Func i akcji delegatów ogólnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
