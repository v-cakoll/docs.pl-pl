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
# <a name="variance-in-delegates-visual-basic"></a><span data-ttu-id="6f55a-102">Wariancje w Delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f55a-102">Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="6f55a-103">.NET framework 3.5 wprowadzono obsługę wariancję dopasowania podpisy metod typów delegata w wszystkich delegatów w języku C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6f55a-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C# and Visual Basic.</span></span> <span data-ttu-id="6f55a-104">Oznacza to, że można przypisać do deleguje nie tylko metody, które pasują do podpisów, ale również metody, które zwracają więcej pochodnych typów (kowariancja) lub akceptujących parametrów, które mają mniej typów pochodnych (kontrawariancja) od określonej przez typ delegata .</span><span class="sxs-lookup"><span data-stu-id="6f55a-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="6f55a-105">Dotyczy to również ogólne i inny niż ogólny delegatów.</span><span class="sxs-lookup"><span data-stu-id="6f55a-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="6f55a-106">Rozważmy na przykład następujący kod, który ma dwie klasy i delegaci dwóch: ogólne i inny niż ogólny.</span><span class="sxs-lookup"><span data-stu-id="6f55a-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```vb  
Public Class First  
End Class  
  
Public Class Second  
    Inherits First  
End Class  
  
Public Delegate Function SampleDelegate(ByVal a As Second) As First  
Public Delegate Function SampleGenericDelegate(Of A, R)(ByVal a As A) As R  
```  
  
 <span data-ttu-id="6f55a-107">Podczas tworzenia delegatów `SampleDelegate` lub `SampleDelegate(Of A, R)` typów, w jednej z następujących metod można przypisać do tych obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="6f55a-107">When you create delegates of the `SampleDelegate` or `SampleDelegate(Of A, R)` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="6f55a-108">Poniższy przykładowy kod przedstawia niejawna konwersja między podpis metody i typu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="6f55a-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="6f55a-109">Aby uzyskać więcej przykładów, zobacz [przy użyciu wariancji w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) i [przy użyciu wariancję Func i akcji Delegaty ogólne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="6f55a-109">For more examples, see [Using Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="6f55a-110">Wariancje w parametry typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="6f55a-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="6f55a-111">W programie .NET Framework 4 lub nowszym można włączyć niejawna konwersja między delegatów, dzięki czemu delegaty ogólne, które mają różne typy określona przez parametry typu ogólnego można przypisać do siebie, jeśli typy są dziedziczone od siebie, co jest wymagane przez WARIANCJA.</span><span class="sxs-lookup"><span data-stu-id="6f55a-111">In .NET Framework 4 and later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="6f55a-112">Aby włączyć niejawna konwersja, musisz jawnie zadeklarować parametry ogólne delegat jako kowariantnego lub kontrawariantnego przy użyciu `in` lub `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="6f55a-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="6f55a-113">Poniższy przykład kodu pokazuje, jak można utworzyć delegata, który ma parametr typu kowariantnego ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6f55a-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="6f55a-114">Jeśli używasz obsługują tylko wariancję odpowiadające podpisy metod z typów delegatów i nie używaj `in` i `out` słowa kluczowe, może się okazać, że czasami można utworzyć wystąpienia obiektów delegowanych z wyrażenia lambda identyczne lub metody, ale nie można wykonać Przypisz jednego delegata do innego.</span><span class="sxs-lookup"><span data-stu-id="6f55a-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="6f55a-115">W poniższym przykładzie kodu `SampleGenericDelegate(Of String)` nie można jawnie przekonwertować na `SampleGenericDelegate(Of Object)`, mimo że `String` dziedziczy `Object`.</span><span class="sxs-lookup"><span data-stu-id="6f55a-115">In the following code example, `SampleGenericDelegate(Of String)` can't be explicitly converted to `SampleGenericDelegate(Of Object)`, although `String` inherits `Object`.</span></span> <span data-ttu-id="6f55a-116">Można rozwiązać ten problem, oznaczając parametru ogólnego `T` z `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="6f55a-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="6f55a-117">Delegaty ogólne, które mają typ Variant parametry typu w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f55a-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="6f55a-118">.NET framework 4 wprowadzono obsługę wariancji dla parametrów typu ogólnego w kilka istniejących delegaty ogólne:</span><span class="sxs-lookup"><span data-stu-id="6f55a-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="6f55a-119">`Action` deleguje z <xref:System> przestrzeni nazw, na przykład <xref:System.Action%601> i <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="6f55a-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="6f55a-120">`Func` deleguje z <xref:System> przestrzeni nazw, na przykład <xref:System.Func%601> i <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="6f55a-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="6f55a-121"><xref:System.Predicate%601> Delegowanie</span><span class="sxs-lookup"><span data-stu-id="6f55a-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="6f55a-122"><xref:System.Comparison%601> Delegowanie</span><span class="sxs-lookup"><span data-stu-id="6f55a-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="6f55a-123"><xref:System.Converter%602> Delegowanie</span><span class="sxs-lookup"><span data-stu-id="6f55a-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="6f55a-124">Aby uzyskać dodatkowe informacje i przykłady, zobacz [wariancji Func i akcji Delegaty ogólne (Visual Basic) przy użyciu](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="6f55a-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="6f55a-125">Deklarowanie parametrów typu Variant w Delegaty ogólne</span><span class="sxs-lookup"><span data-stu-id="6f55a-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="6f55a-126">Jeśli Delegat ogólny ma kowariantnego lub kontrawariantnego parametry typu ogólnego, ona może być określana jako *variant Delegat ogólny*.</span><span class="sxs-lookup"><span data-stu-id="6f55a-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="6f55a-127">Można zadeklarować parametru typu ogólnego kowariantnego Delegat ogólny przy użyciu `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="6f55a-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="6f55a-128">Kowariantnego typu może służyć jedynie jako zwracany typ metody, a nie typu argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="6f55a-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="6f55a-129">Poniższy przykład kodu pokazuje, jak można zadeklarować kowariantnego Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="6f55a-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```vb  
Public Delegate Function DCovariant(Of Out R)() As R  
```  
  
 <span data-ttu-id="6f55a-130">Kontrawariantnego parametru typu ogólnego, Delegat ogólny można zadeklarować przy użyciu `in` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="6f55a-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="6f55a-131">Typ kontrawariantnego może służyć wyłącznie jako argumenty metody, a nie jako zwracany typ metody.</span><span class="sxs-lookup"><span data-stu-id="6f55a-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="6f55a-132">Poniższy przykład kodu pokazuje, jak można zadeklarować kontrawariantnego Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="6f55a-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```vb  
Public Delegate Sub DContravariant(Of In A)(ByVal a As A)  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="6f55a-133">`ByRef` Parametry w języku Visual Basic nie można oznaczyć jako typ variant.</span><span class="sxs-lookup"><span data-stu-id="6f55a-133">`ByRef` parameters in Visual Basic can't be marked as variant.</span></span>  
  
 <span data-ttu-id="6f55a-134">Istnieje również możliwość do obsługi wariancji i Kowariancja w tego samego obiektu delegowanego, ale także dla parametrów innego typu.</span><span class="sxs-lookup"><span data-stu-id="6f55a-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="6f55a-135">Przedstawiono to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6f55a-135">This is shown in the following example.</span></span>  
  
```vb  
Public Delegate Function DVariant(Of In A, Out R)(ByVal a As A) As R  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="6f55a-136">Tworzenie wystąpień i powoływanie delegatów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="6f55a-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="6f55a-137">Można utworzyć wystąpienia i wywołać variant delegatów tak samo, jak wystąpienia i wywoływać niezmiennej delegatów.</span><span class="sxs-lookup"><span data-stu-id="6f55a-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="6f55a-138">W poniższym przykładzie delegat jest utworzone przez wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="6f55a-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```vb  
Dim dvariant As DVariant(Of String, String) = Function(str) str + " "  
dvariant("test")  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="6f55a-139">Łączenie Variant Delegaty ogólne</span><span class="sxs-lookup"><span data-stu-id="6f55a-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="6f55a-140">Nie należy łączyć variant delegatów.</span><span class="sxs-lookup"><span data-stu-id="6f55a-140">You should not combine variant delegates.</span></span> <span data-ttu-id="6f55a-141"><xref:System.Delegate.Combine%2A> — Metoda nie obsługuje konwersji typu variant delegata i oczekuje delegatów być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="6f55a-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="6f55a-142">Może to spowodować wyjątek czasu wykonywania podczas łączenia delegaty przy użyciu <xref:System.Delegate.Combine%2A> — metoda (w języku C# i Visual Basic) lub za pomocą `+` — operator (w języku C#), jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="6f55a-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method (in C# and Visual Basic) or by using the `+` operator (in C#), as shown in the following code example.</span></span>  
  
```vb  
Dim actObj As Action(Of Object) = Sub(x) Console.WriteLine("object: {0}", x)  
Dim actStr As Action(Of String) = Sub(x) Console.WriteLine("string: {0}", x)  
  
' The following statement throws an exception at run time.  
' Dim actCombine = [Delegate].Combine(actStr, actObj)  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="6f55a-143">Wariancje w parametry typu ogólnego dla wartości i typy referencyjne</span><span class="sxs-lookup"><span data-stu-id="6f55a-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="6f55a-144">Wariancji dla parametrów typu ogólnego jest obsługiwana tylko dla typów odniesienia.</span><span class="sxs-lookup"><span data-stu-id="6f55a-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="6f55a-145">Na przykład `DVariant(Of Int)`nie można niejawnie przekonwertować `DVariant(Of Object)` lub `DVariant(Of Long)`, ponieważ typ wartości jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="6f55a-145">For example, `DVariant(Of Int)`can't be implicitly converted to `DVariant(Of Object)` or `DVariant(Of Long)`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="6f55a-146">W poniższym przykładzie pokazano, że wariancji typu ogólnego parametrów nie jest obsługiwany dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="6f55a-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="relaxed-delegate-conversion-in-visual-basic"></a><span data-ttu-id="6f55a-147">Swobodna konwersja delegatów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6f55a-147">Relaxed Delegate Conversion in Visual Basic</span></span>  
 <span data-ttu-id="6f55a-148">Swobodna konwersja delegatów zapewnia większą elastyczność podczas dopasowywania podpisy metod z typów obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="6f55a-148">Relaxed delegate conversion enables more flexibility in matching method signatures with delegate types.</span></span> <span data-ttu-id="6f55a-149">Na przykład umożliwia pominięcie specyfikacji parametrów i wartości zwracane przez funkcję, Pomiń podczas przypisywania metody do delegata.</span><span class="sxs-lookup"><span data-stu-id="6f55a-149">For example, it lets you omit parameter specifications and omit function return values when you assign a method to a delegate.</span></span> <span data-ttu-id="6f55a-150">Aby uzyskać więcej informacji, zobacz [swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="6f55a-150">For more information, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f55a-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f55a-151">See Also</span></span>  
 [<span data-ttu-id="6f55a-152">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="6f55a-152">Generics</span></span>](~/docs/standard/generics/index.md)  
 [<span data-ttu-id="6f55a-153">Korzystanie z wariancji dla Func i akcji Delegaty ogólne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f55a-153">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
