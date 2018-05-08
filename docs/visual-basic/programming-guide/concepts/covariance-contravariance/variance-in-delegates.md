---
title: Wariancje w Delegatach (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: d857f120be0fe810489ba69edb55af9cc0dd6940
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="variance-in-delegates-visual-basic"></a>Wariancje w Delegatach (Visual Basic)
.NET framework 3.5 wprowadzono obsługę wariancję dopasowania podpisy metod typów delegata w wszystkich delegatów w języku C# i Visual Basic. Oznacza to, że można przypisać do deleguje nie tylko metody, które pasują do podpisów, ale również metody, które zwracają więcej pochodnych typów (kowariancja) lub akceptujących parametrów, które mają mniej typów pochodnych (kontrawariancja) od określonej przez typ delegata . Dotyczy to również ogólne i inny niż ogólny delegatów.  
  
 Rozważmy na przykład następujący kod, który ma dwie klasy i delegaci dwóch: ogólne i inny niż ogólny.  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 Podczas tworzenia delegatów `SampleDelegate` lub `SampleDelegate(Of A, R)` typów, w jednej z następujących metod można przypisać do tych obiektów delegowanych.  
  
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
  
 Poniższy przykładowy kod przedstawia niejawna konwersja między podpis metody i typu delegowanego.  
  
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
  
 Aby uzyskać więcej przykładów, zobacz [przy użyciu wariancji w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) i [przy użyciu wariancję Func i akcji Delegaty ogólne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Wariancje w parametry typu ogólnego  
 W programie .NET Framework 4 lub nowszym można włączyć niejawna konwersja między delegatów, dzięki czemu delegaty ogólne, które mają różne typy określona przez parametry typu ogólnego można przypisać do siebie, jeśli typy są dziedziczone od siebie, co jest wymagane przez WARIANCJA.  
  
 Aby włączyć niejawna konwersja, musisz jawnie zadeklarować parametry ogólne delegat jako kowariantnego lub kontrawariantnego przy użyciu `in` lub `out` — słowo kluczowe.  
  
 Poniższy przykład kodu pokazuje, jak można utworzyć delegata, który ma parametr typu kowariantnego ogólnego.  
  
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
  
 Jeśli używasz obsługują tylko wariancję odpowiadające podpisy metod z typów delegatów i nie używaj `in` i `out` słowa kluczowe, może się okazać, że czasami można utworzyć wystąpienia obiektów delegowanych z wyrażenia lambda identyczne lub metody, ale nie można wykonać Przypisz jednego delegata do innego.  
  
 W poniższym przykładzie kodu `SampleGenericDelegate(Of String)` nie można jawnie przekonwertować na `SampleGenericDelegate(Of Object)`, mimo że `String` dziedziczy `Object`. Można rozwiązać ten problem, oznaczając parametru ogólnego `T` z `out` — słowo kluczowe.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Delegaty ogólne, które mają typ Variant parametry typu w programie .NET Framework  
 .NET framework 4 wprowadzono obsługę wariancji dla parametrów typu ogólnego w kilka istniejących delegaty ogólne:  
  
-   `Action` deleguje z <xref:System> przestrzeni nazw, na przykład <xref:System.Action%601> i <xref:System.Action%602>  
  
-   `Func` deleguje z <xref:System> przestrzeni nazw, na przykład <xref:System.Func%601> i <xref:System.Func%602>  
  
-   <xref:System.Predicate%601> Delegowanie  
  
-   <xref:System.Comparison%601> Delegowanie  
  
-   <xref:System.Converter%602> Delegowanie  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [wariancji Func i akcji Delegaty ogólne (Visual Basic) przy użyciu](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarowanie parametrów typu Variant w Delegaty ogólne  
 Jeśli Delegat ogólny ma kowariantnego lub kontrawariantnego parametry typu ogólnego, ona może być określana jako *variant Delegat ogólny*.  
  
 Można zadeklarować parametru typu ogólnego kowariantnego Delegat ogólny przy użyciu `out` — słowo kluczowe. Kowariantnego typu może służyć jedynie jako zwracany typ metody, a nie typu argumenty metody. Poniższy przykład kodu pokazuje, jak można zadeklarować kowariantnego Delegat ogólny.  
  
```vb  
Public Delegate Function DCovariant(Of Out R)() As R  
```  
  
 Kontrawariantnego parametru typu ogólnego, Delegat ogólny można zadeklarować przy użyciu `in` — słowo kluczowe. Typ kontrawariantnego może służyć wyłącznie jako argumenty metody, a nie jako zwracany typ metody. Poniższy przykład kodu pokazuje, jak można zadeklarować kontrawariantnego Delegat ogólny.  
  
```vb  
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)  
```  
  
> [!IMPORTANT]
>  `ByRef` Parametry w języku Visual Basic nie można oznaczyć jako typ variant.  
  
 Istnieje również możliwość do obsługi wariancji i Kowariancja w tego samego obiektu delegowanego, ale także dla parametrów innego typu. Przedstawiono to w poniższym przykładzie.  
  
```vb  
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Tworzenie wystąpień i powoływanie delegatów ogólnych typu Variant  
 Można utworzyć wystąpienia i wywołać variant delegatów tak samo, jak wystąpienia i wywoływać niezmiennej delegatów. W poniższym przykładzie delegat jest utworzone przez wyrażenie lambda.  
  
```vb  
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "  
dvariant("test")  
```  
  
### <a name="combining-variant-generic-delegates"></a>Łączenie Variant Delegaty ogólne  
 Nie należy łączyć variant delegatów. <xref:System.Delegate.Combine%2A> — Metoda nie obsługuje konwersji typu variant delegata i oczekuje delegatów być tego samego typu. Może to spowodować wyjątek czasu wykonywania podczas łączenia delegaty przy użyciu <xref:System.Delegate.Combine%2A> — metoda (w języku C# i Visual Basic) lub za pomocą `+` — operator (w języku C#), jak pokazano w poniższym przykładzie kodu.  
  
```vb  
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)  
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)  
  
' The following statement throws an exception at run time.  
' Dim actCombine = [Delegate].Combine(actStr, actObj)  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Wariancje w parametry typu ogólnego dla wartości i typy referencyjne  
 Wariancji dla parametrów typu ogólnego jest obsługiwana tylko dla typów odniesienia. Na przykład `DVariant(Of Int)`nie można niejawnie przekonwertować `DVariant(Of Object)` lub `DVariant(Of Long)`, ponieważ typ wartości jest liczbą całkowitą.  
  
 W poniższym przykładzie pokazano, że wariancji typu ogólnego parametrów nie jest obsługiwany dla typów wartości.  
  
```vb  
' The type T is covariant.  
Public Delegate Function DVariant(Of Out T)() As T  
' The type T is invariant.  
Public Delegate Function DInvariant(Of T)() As T  
Sub Test()  
    Dim i As Integer = 0  
    Dim dInt As DInvariant(Of Integer) = Function() i  
    Dim dVaraintInt As DVariant(Of Integer) = Function() i  
  
    ' All of the following statements generate a compiler error  
    ' because type variance in generic parameters is not supported  
    ' for value types, even if generic type parameters are declared variant.  
    ' Dim dObject As DInvariant(Of Object) = dInt  
    ' Dim dLong As DInvariant(Of Long) = dInt  
    ' Dim dVaraintObject As DInvariant(Of Object) = dInt  
    ' Dim dVaraintLong As DInvariant(Of Long) = dInt  
End Sub  
```  
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a>Swobodna konwersja delegatów w języku Visual Basic  
 Swobodna konwersja delegatów zapewnia większą elastyczność podczas dopasowywania podpisy metod z typów obiektów delegowanych. Na przykład umożliwia pominięcie specyfikacji parametrów i wartości zwracane przez funkcję, Pomiń podczas przypisywania metody do delegata. Aby uzyskać więcej informacji, zobacz [swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](~/docs/standard/generics/index.md)  
 [Korzystanie z wariancji dla Func i akcji Delegaty ogólne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
