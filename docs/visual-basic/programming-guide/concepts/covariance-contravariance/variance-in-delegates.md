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
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="188cc-102">Wariancje w Delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="188cc-102">Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="188cc-103">.NET framework 3.5 wprowadzono obsługę wariancji podpisów metod dopasowania z typów obiektów delegowanych w wszystkie obiekty delegowane w C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="188cc-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="188cc-104">Oznacza to, że można przypisać do deleguje nie tylko metody, które pasują do sygnatur, ale także metody, które zwracają więcej pochodne typy (korelacja) lub które przyjmują parametry, które mają mniej pochodne typy (kontrawariancja) niż określona przez typ delegata .</span><span class="sxs-lookup"><span data-stu-id="188cc-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="188cc-105">Dotyczy to również delegatów ogólnych i nieogólnych.</span><span class="sxs-lookup"><span data-stu-id="188cc-105">This includes both generic and non-generic delegates.</span></span>

<span data-ttu-id="188cc-106">Na przykład rozważmy następujący kod, który ma dwie klasy i dwa delegaty: ogólnych i nieogólnych.</span><span class="sxs-lookup"><span data-stu-id="188cc-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

<span data-ttu-id="188cc-107">Po utworzeniu delegatów `SampleDelegate` lub `SampleDelegate(Of A, R)` typów, w jednej z następujących metod można przypisać do tych obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="188cc-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>

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

<span data-ttu-id="188cc-108">Poniższy przykład kodu ilustruje niejawna konwersja między podpis metody i typu delegata.</span><span class="sxs-lookup"><span data-stu-id="188cc-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>

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

<span data-ttu-id="188cc-109">Aby uzyskać więcej przykładów, zobacz [przy użyciu wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) i [przy użyciu wariancji dla akcji delegatów ogólnych (Visual Basic) Func i](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="188cc-109">For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="188cc-110">Wariancji w parametrach typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="188cc-110">Variance in Generic Type Parameters</span></span>

<span data-ttu-id="188cc-111">W programie .NET Framework 4 lub nowszym można włączyć niejawna konwersja między elementem delegatów, dzięki czemu delegatów ogólnych, które mają różne typy określona przez parametry typu ogólnego mogą być przypisane do siebie nawzajem, jeśli typy są dziedziczone od siebie nawzajem, zgodnie z wymaganiami WARIANCJA.</span><span class="sxs-lookup"><span data-stu-id="188cc-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>

<span data-ttu-id="188cc-112">Aby włączyć niejawną konwersję, musisz jawnie deklarować parametrów ogólnych w delegatów jako kowariantnych lub kontrawariantnych przy użyciu `in` lub `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="188cc-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>

<span data-ttu-id="188cc-113">Poniższy przykład kodu pokazuje, jak utworzyć obiekt delegowany mający parametr kowariantnego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="188cc-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>

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

<span data-ttu-id="188cc-114">Jeśli używasz obsługują tylko odchylenia do dopasowania podpisy metod ze typy delegatów i nie używaj `in` i `out` słów kluczowych, może się okazać, że czasami można utworzyć wystąpienie obiektów delegowanych z wyrażenia lambda identyczne lub metody, ale nie jest możliwe Przypisz jednego delegata do innego.</span><span class="sxs-lookup"><span data-stu-id="188cc-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>

<span data-ttu-id="188cc-115">W poniższym przykładzie kodu `SampleGenericDelegate(Of String)` nie może być jawnie konwertowane na `SampleGenericDelegate(Of Object)`, mimo że `String` dziedziczy `Object`.</span><span class="sxs-lookup"><span data-stu-id="188cc-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="188cc-116">Możesz rozwiązać ten problem, oznaczając parametru ogólnego `T` z `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="188cc-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>

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

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="188cc-117">Parametry typu delegatów ogólnych, które mają typ Variant w .NET Framework</span><span class="sxs-lookup"><span data-stu-id="188cc-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>

<span data-ttu-id="188cc-118">.NET framework 4 wprowadzono obsługę wariancji dla parametrów typu rodzajowego w kilku istniejących delegatów ogólnych:</span><span class="sxs-lookup"><span data-stu-id="188cc-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>

- <span data-ttu-id="188cc-119">`Action` delegaty z <xref:System> przestrzeni nazw, na przykład <xref:System.Action%601> i <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="188cc-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>

- <span data-ttu-id="188cc-120">`Func` delegaty z <xref:System> przestrzeni nazw, na przykład <xref:System.Func%601> i <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="188cc-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>

- <span data-ttu-id="188cc-121"><xref:System.Predicate%601> Delegowanie</span><span class="sxs-lookup"><span data-stu-id="188cc-121">The <xref:System.Predicate%601> delegate</span></span>

- <span data-ttu-id="188cc-122"><xref:System.Comparison%601> Delegowanie</span><span class="sxs-lookup"><span data-stu-id="188cc-122">The <xref:System.Comparison%601> delegate</span></span>

- <span data-ttu-id="188cc-123"><xref:System.Converter%602> Delegowanie</span><span class="sxs-lookup"><span data-stu-id="188cc-123">The <xref:System.Converter%602> delegate</span></span>

<span data-ttu-id="188cc-124">Aby uzyskać więcej informacji i przykładów, zobacz [przy użyciu wariancji dla akcji delegatów ogólnych (Visual Basic) Func i](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="188cc-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="188cc-125">Deklarowanie Wariantne parametry typu w delegatów ogólnych</span><span class="sxs-lookup"><span data-stu-id="188cc-125">Declaring Variant Type Parameters in Generic Delegates</span></span>

<span data-ttu-id="188cc-126">Jeśli delegata ogólnego ma kowariantne i kontrawariantne parametry typu ogólnego, jego mogą być określane jako *variant Delegat ogólny*.</span><span class="sxs-lookup"><span data-stu-id="188cc-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>

<span data-ttu-id="188cc-127">Można zadeklarować parametru typu generycznego kowariantne Delegat ogólny przy użyciu `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="188cc-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="188cc-128">Kowariantnego typu może służyć jedynie jako typ zwracany metody, a nie typu argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="188cc-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="188cc-129">Poniższy przykład kodu pokazuje sposób deklarowania kowariantne Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="188cc-129">The following code example shows how to declare a covariant generic delegate.</span></span>

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

<span data-ttu-id="188cc-130">Kontrawariantnego parametru typu ogólnego, Delegat ogólny może zadeklarować za pomocą `in` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="188cc-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="188cc-131">Typ kontrawariantne może służyć jedynie jako typów argumentów metody, a nie typem zwracanym metody.</span><span class="sxs-lookup"><span data-stu-id="188cc-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="188cc-132">Poniższy przykład kodu pokazuje sposób deklarowania to delegat generyczny kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="188cc-132">The following code example shows how to declare a contravariant generic delegate.</span></span>

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> <span data-ttu-id="188cc-133">`ByRef` w języku Visual Basic nie można oznaczyć jako wariant.</span><span class="sxs-lookup"><span data-stu-id="188cc-133">`ByRef` parameters in Visual Basic can't be marked as variant.</span></span>

<span data-ttu-id="188cc-134">Istnieje również możliwość obsługi kowariancji i Wariancja w tym samym delegatów, ale w przypadku różnych typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="188cc-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="188cc-135">Jest to pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="188cc-135">This is shown in the following example.</span></span>

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="188cc-136">Utworzenie wystąpienia i wywoływania wariantów ogólnych delegatów</span><span class="sxs-lookup"><span data-stu-id="188cc-136">Instantiating and Invoking Variant Generic Delegates</span></span>

<span data-ttu-id="188cc-137">Można utworzyć wystąpienia i wywoływać delegatów typu variant, tak samo, jak utworzyć wystąpienia i wywoływać delegatów niezmiennej.</span><span class="sxs-lookup"><span data-stu-id="188cc-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="188cc-138">W poniższym przykładzie delegat jest tworzone przez wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="188cc-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="188cc-139">Łączenie delegatów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="188cc-139">Combining Variant Generic Delegates</span></span>

<span data-ttu-id="188cc-140">Nie należy łączyć wariantu delegatów.</span><span class="sxs-lookup"><span data-stu-id="188cc-140">You should not combine variant delegates.</span></span> <span data-ttu-id="188cc-141"><xref:System.Delegate.Combine%2A> Metoda nie obsługuje konwersji typu variant delegata i oczekuje, że delegaty dokładnie tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="188cc-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="188cc-142">Może to prowadzić do wyjątku czasu wykonywania, podczas łączenia przy użyciu delegatów <xref:System.Delegate.Combine%2A> — metoda (w C# i Visual Basic) lub za pomocą `+` — operator (w C#), jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="188cc-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="188cc-143">Wariancji w parametrach typu ogólnego dla wartości i typy odwołań</span><span class="sxs-lookup"><span data-stu-id="188cc-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>

<span data-ttu-id="188cc-144">Wariancja dla parametrów typu ogólnego jest obsługiwana tylko dla typów odwołania.</span><span class="sxs-lookup"><span data-stu-id="188cc-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="188cc-145">Na przykład `DVariant(Of Int)`nie może być niejawnie konwertowane na `DVariant(Of Object)` lub `DVariant(Of Long)`, ponieważ liczba całkowita jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="188cc-145">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>

<span data-ttu-id="188cc-146">W poniższym przykładzie pokazano tej wariancji w typie ogólnym parametrów nie jest obsługiwana dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="188cc-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>

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

## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="188cc-147">Swobodna konwersja delegatów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="188cc-147">Relaxed Delegate Conversion in Visual Basic</span></span>

<span data-ttu-id="188cc-148">Swobodna konwersja delegatów umożliwia większą elastyczność w podpisów metod dopasowania z typów obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="188cc-148">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="188cc-149">Na przykład dzięki temu można pominąć parametr specyfikacji i pominięto wartości zwracane przez funkcję, gdy przypiszemy metodę do delegata.</span><span class="sxs-lookup"><span data-stu-id="188cc-149">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="188cc-150">Aby uzyskać więcej informacji, zobacz [swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="188cc-150">For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="188cc-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="188cc-151">See also</span></span>

- [<span data-ttu-id="188cc-152">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="188cc-152">Generics</span></span>](~/docs/standard/generics/index.md)
- [<span data-ttu-id="188cc-153">Korzystanie z wariancji dla Func i akcji delegatów ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="188cc-153">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
