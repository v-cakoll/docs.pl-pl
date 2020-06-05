---
title: Wariancje w delegatach
ms.date: 07/20/2015
ms.assetid: 38e9353f-74f8-4211-a8f0-7a495414df4a
ms.openlocfilehash: 86ea9f3f744381bcff71a88e9d88485cafa4a568
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375619"
---
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="aae2d-102">Wariancja w delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aae2d-102">Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="aae2d-103">.NET Framework 3,5 wprowadza obsługę wariancji dla pasujących sygnatur metod z typami delegatów we wszystkich delegatach w C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="aae2d-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="aae2d-104">Oznacza to, że można przypisać do delegatów nie tylko metod, które mają pasujące podpisy, ale również metody, które zwracają więcej typów pochodnych (Kowariancja) lub akceptują parametry, które mają mniej pochodne typy (kontrawariancja) niż określone przez typ delegata.</span><span class="sxs-lookup"><span data-stu-id="aae2d-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="aae2d-105">Dotyczy to zarówno delegatów rodzajowych, jak i nieogólnych.</span><span class="sxs-lookup"><span data-stu-id="aae2d-105">This includes both generic and non-generic delegates.</span></span>

<span data-ttu-id="aae2d-106">Rozważmy na przykład poniższy kod, który ma dwie klasy i dwa Delegaty: generyczne i nieogólne.</span><span class="sxs-lookup"><span data-stu-id="aae2d-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>

```vb
Public Class First
End Class

Public Class Second
    Inherits First
End Class

Public Delegate Function SampleDelegate(ByVal a As Second) As First
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R
```

<span data-ttu-id="aae2d-107">Podczas tworzenia delegatów `SampleDelegate` lub typów można `SampleDelegate(Of A, R)` przypisać do tych delegatów jedną z następujących metod.</span><span class="sxs-lookup"><span data-stu-id="aae2d-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>

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

<span data-ttu-id="aae2d-108">Poniższy przykład kodu ilustruje niejawną konwersję między sygnaturą metody a typem delegata.</span><span class="sxs-lookup"><span data-stu-id="aae2d-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>

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

<span data-ttu-id="aae2d-109">Aby uzyskać więcej przykładów, zobacz [Korzystanie z wariancji w delegatach (Visual Basic)](using-variance-in-delegates.md) i [Używanie wariancji dla delegatów funkcji Func i Action (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="aae2d-109">For more examples, see [Using Variance in Delegates (Visual Basic)](using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span></span>

## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="aae2d-110">Wariancja w parametrach typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="aae2d-110">Variance in Generic Type Parameters</span></span>

<span data-ttu-id="aae2d-111">W .NET Framework 4 i nowszych można włączyć niejawną konwersję między delegatami, tak aby generyczne Delegaty, które mają różne typy określone przez parametry typu generycznego, można przypisać do siebie nawzajem, jeśli typy są dziedziczone od siebie jako wymagane przez wariancję.</span><span class="sxs-lookup"><span data-stu-id="aae2d-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>

<span data-ttu-id="aae2d-112">Aby włączyć niejawną konwersję, należy jawnie zadeklarować parametry ogólne w delegatze jako współvariant lub kontrawariantne za pomocą `in` `out` słowa kluczowego or.</span><span class="sxs-lookup"><span data-stu-id="aae2d-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>

<span data-ttu-id="aae2d-113">Poniższy przykład kodu pokazuje, jak można utworzyć delegata, który ma parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="aae2d-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>

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

<span data-ttu-id="aae2d-114">Jeśli używasz tylko wariancji do dopasowania sygnatur metod z typami delegatów i nie używaj `in` `out` słów kluczowych i, możesz się dowiedzieć, że czasami można utworzyć wystąpienia delegatów z identycznymi wyrażeniami lambda lub metodami, ale nie można przypisać jednego delegata do innego.</span><span class="sxs-lookup"><span data-stu-id="aae2d-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>

<span data-ttu-id="aae2d-115">W poniższym przykładzie kodu nie można `SampleGenericDelegate(Of String)` jawnie przekonwertować na `SampleGenericDelegate(Of Object)` , chociaż `String` dziedziczy `Object` .</span><span class="sxs-lookup"><span data-stu-id="aae2d-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="aae2d-116">Ten problem można rozwiązać przez oznaczenie parametru generycznego `T` `out` słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="aae2d-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>

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

### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="aae2d-117">Delegaty ogólne, które mają parametry typu Variant w .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aae2d-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>

<span data-ttu-id="aae2d-118">.NET Framework 4 wprowadził obsługę wariancji dla parametrów typu ogólnego w kilku istniejących delegatach ogólnych:</span><span class="sxs-lookup"><span data-stu-id="aae2d-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>

- <span data-ttu-id="aae2d-119">`Action`deleguje z <xref:System> przestrzeni nazw, na przykład, <xref:System.Action%601> i<xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="aae2d-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>

- <span data-ttu-id="aae2d-120">`Func`deleguje z <xref:System> przestrzeni nazw, na przykład, <xref:System.Func%601> i<xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="aae2d-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>

- <span data-ttu-id="aae2d-121"><xref:System.Predicate%601>Obiekt delegowany</span><span class="sxs-lookup"><span data-stu-id="aae2d-121">The <xref:System.Predicate%601> delegate</span></span>

- <span data-ttu-id="aae2d-122"><xref:System.Comparison%601>Obiekt delegowany</span><span class="sxs-lookup"><span data-stu-id="aae2d-122">The <xref:System.Comparison%601> delegate</span></span>

- <span data-ttu-id="aae2d-123"><xref:System.Converter%602>Obiekt delegowany</span><span class="sxs-lookup"><span data-stu-id="aae2d-123">The <xref:System.Converter%602> delegate</span></span>

<span data-ttu-id="aae2d-124">Aby uzyskać więcej informacji i zapoznać się z przykładami, zobacz [using WARIANCJA dla delegatów "Func" i "Akcja" (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="aae2d-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](using-variance-for-func-and-action-generic-delegates.md).</span></span>

### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="aae2d-125">Deklarowanie parametrów typu Variant w delegatach generycznych</span><span class="sxs-lookup"><span data-stu-id="aae2d-125">Declaring Variant Type Parameters in Generic Delegates</span></span>

<span data-ttu-id="aae2d-126">Jeśli delegat generyczny ma parametry typu generycznego lub kontrawariantne, może być określany jako *Delegat generyczny elementu Variant*.</span><span class="sxs-lookup"><span data-stu-id="aae2d-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>

<span data-ttu-id="aae2d-127">Za pomocą słowa kluczowego można zadeklarować współwariant parametru typu ogólnego w delegatze ogólnym `out` .</span><span class="sxs-lookup"><span data-stu-id="aae2d-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="aae2d-128">Typ współwariantu może być używany tylko jako zwracany typ metody, a nie jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="aae2d-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="aae2d-129">Poniższy przykład kodu pokazuje, jak zadeklarować delegata generycznego.</span><span class="sxs-lookup"><span data-stu-id="aae2d-129">The following code example shows how to declare a covariant generic delegate.</span></span>

```vb
Public Delegate Function DCovariant(Of Out R)() As R
```

<span data-ttu-id="aae2d-130">Parametr typu ogólnego kontrawariantne można zadeklarować w delegatze ogólnym za pomocą `in` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="aae2d-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="aae2d-131">Typ kontrawariantne może być używany tylko jako typ argumentów metody, a nie jako zwracany typ metody.</span><span class="sxs-lookup"><span data-stu-id="aae2d-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="aae2d-132">Poniższy przykład kodu pokazuje, jak zadeklarować delegata generycznego kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="aae2d-132">The following code example shows how to declare a contravariant generic delegate.</span></span>

```vb
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)
```

> [!IMPORTANT]
> <span data-ttu-id="aae2d-133">`ByRef`parametrów w Visual Basic nie można oznaczyć jako VARIANT.</span><span class="sxs-lookup"><span data-stu-id="aae2d-133">`ByRef` parameters in Visual Basic can't be marked as variant.</span></span>

<span data-ttu-id="aae2d-134">Istnieje również możliwość obsługi zarówno wariancji, jak i kowariancji w tym samym delegatze, ale dla różnych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="aae2d-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="aae2d-135">Pokazano to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="aae2d-135">This is shown in the following example.</span></span>

```vb
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R
```

### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="aae2d-136">Tworzenie wystąpień i wywoływanie delegatów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="aae2d-136">Instantiating and Invoking Variant Generic Delegates</span></span>

<span data-ttu-id="aae2d-137">Można tworzyć wystąpienia delegatów wariantów i wywoływać je tak samo jak w przypadku wystąpienia i wywoływać delegatów niezmiennej.</span><span class="sxs-lookup"><span data-stu-id="aae2d-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="aae2d-138">W poniższym przykładzie obiekt delegowany jest tworzone przez wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="aae2d-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>

```vb
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "
dvariant("test")
```

### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="aae2d-139">Łączenie delegatów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="aae2d-139">Combining Variant Generic Delegates</span></span>

<span data-ttu-id="aae2d-140">Nie należy łączyć delegatów wariantów.</span><span class="sxs-lookup"><span data-stu-id="aae2d-140">You should not combine variant delegates.</span></span> <span data-ttu-id="aae2d-141"><xref:System.Delegate.Combine%2A>Metoda nie obsługuje konwersji delegata typu Variant i oczekuje, że Delegaty mają być dokładnie tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="aae2d-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="aae2d-142">Może to prowadzić do wyjątku czasu wykonywania podczas łączenia delegatów za pomocą <xref:System.Delegate.Combine%2A> metody (w języku C# i Visual Basic) lub za pomocą `+` operatora (w języku c#), jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="aae2d-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>

```vb
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)

' The following statement throws an exception at run time.
' Dim actCombine = [Delegate].Combine(actStr, actObj)
```

## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="aae2d-143">Wariancja w parametrach typu ogólnego dla typów wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="aae2d-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>

<span data-ttu-id="aae2d-144">WARIANCJA dla parametrów typu ogólnego jest obsługiwana tylko w przypadku typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="aae2d-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="aae2d-145">Na przykład `DVariant(Of Int)` nie można konwertować niejawnie na `DVariant(Of Object)` lub `DVariant(Of Long)` , ponieważ liczba całkowita jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="aae2d-145">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>

<span data-ttu-id="aae2d-146">W poniższym przykładzie pokazano, że Wariancja w parametrach typu ogólnego nie jest obsługiwana w przypadku typów wartości.</span><span class="sxs-lookup"><span data-stu-id="aae2d-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>

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

## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="aae2d-147">Swobodna konwersja delegata w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aae2d-147">Relaxed Delegate Conversion in Visual Basic</span></span>

<span data-ttu-id="aae2d-148">Swobodna konwersja delegatów umożliwia większą elastyczność w dopasowaniu sygnatur metod z typami delegatów.</span><span class="sxs-lookup"><span data-stu-id="aae2d-148">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="aae2d-149">Na przykład pozwala pominąć specyfikacje parametrów i pomijać wartości zwracane przez funkcję przy przypisywaniu metody do delegata.</span><span class="sxs-lookup"><span data-stu-id="aae2d-149">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="aae2d-150">Aby uzyskać więcej informacji, zobacz [Swobodna konwersja delegata](../../language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="aae2d-150">For more information, see [Relaxed Delegate Conversion](../../language-features/delegates/relaxed-delegate-conversion.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aae2d-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aae2d-151">See also</span></span>

- [<span data-ttu-id="aae2d-152">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="aae2d-152">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="aae2d-153">Korzystanie z wariancji dla delegatów "Func" i "Action Generic" (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aae2d-153">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](using-variance-for-func-and-action-generic-delegates.md)
