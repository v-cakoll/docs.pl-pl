---
title: Wariancja w delegatach (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: fd1b4824dc3d8f12347e01b804a6e39fe2e086c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169717"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="22a3c-102">Wariancja w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="22a3c-102">Variance in Delegates (C#)</span></span>
<span data-ttu-id="22a3c-103">.NET Framework 3.5 wprowadzono obsługę wariancji dla podpisów metod dopasowywania z typami delegatów we wszystkich delegatach w języku C#.</span><span class="sxs-lookup"><span data-stu-id="22a3c-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="22a3c-104">Oznacza to, że można przypisać do delegatów nie tylko metody, które mają pasujące podpisy, ale także metody, które zwracają więcej typów pochodnych (kowariancja) lub które akceptują parametry, które mają mniej pochodnych typów (contravariance) niż określone przez typ delegata .</span><span class="sxs-lookup"><span data-stu-id="22a3c-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="22a3c-105">Obejmuje to zarówno delegatów ogólnych i nieogólnych.</span><span class="sxs-lookup"><span data-stu-id="22a3c-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="22a3c-106">Rozważmy na przykład następujący kod, który ma dwie klasy i dwie delegatów: ogólny i nierodzajowy.</span><span class="sxs-lookup"><span data-stu-id="22a3c-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="22a3c-107">Podczas tworzenia delegatów `SampleDelegate` `SampleGenericDelegate<A, R>` lub typów, można przypisać jedną z następujących metod do tych delegatów.</span><span class="sxs-lookup"><span data-stu-id="22a3c-107">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second second)  
{ return new First(); }  
  
// The return type is more derived.  
public static Second ASecondRSecond(Second second)  
{ return new Second(); }  
  
// The argument type is less derived.  
public static First AFirstRFirst(First first)  
{ return new First(); }  
  
// The return type is more derived
// and the argument type is less derived.  
public static Second AFirstRSecond(First first)  
{ return new Second(); }  
```  
  
 <span data-ttu-id="22a3c-108">Poniższy przykład kodu ilustruje niejawną konwersję między podpisem metody a typem delegata.</span><span class="sxs-lookup"><span data-stu-id="22a3c-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
```csharp  
// Assigning a method with a matching signature
// to a non-generic delegate. No conversion is necessary.  
SampleDelegate dNonGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a non-generic delegate.  
// The implicit conversion is used.  
SampleDelegate dNonGenericConversion = AFirstRSecond;  
  
// Assigning a method with a matching signature to a generic delegate.  
// No conversion is necessary.  
SampleGenericDelegate<Second, First> dGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type
// and less derived argument type to a generic delegate.  
// The implicit conversion is used.  
SampleGenericDelegate<Second, First> dGenericConversion = AFirstRSecond;  
```  
  
 <span data-ttu-id="22a3c-109">Aby uzyskać więcej przykładów, zobacz [Używanie wariancji w delegatach (C#)](./using-variance-in-delegates.md) i [używanie wariancji dla delegatów ogólnych akcji i akcji (C#).](./using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="22a3c-109">For more examples, see [Using Variance in Delegates (C#)](./using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="22a3c-110">Wariancja w parametrach typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="22a3c-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="22a3c-111">W .NET Framework 4 lub nowszej można włączyć niejawną konwersję między delegatami, dzięki czemu delegaci ogólni, którzy mają różne typy określone przez parametry typu ogólnego, mogą być przypisane do siebie, jeśli typy są dziedziczone od siebie zgodnie z wymaganiami Wariancji.</span><span class="sxs-lookup"><span data-stu-id="22a3c-111">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="22a3c-112">Aby włączyć konwersję niejawną, należy jawnie zadeklarować parametry ogólne w pełnomocnika jako kowariantylub kontrawariantny przy użyciu słowa kluczowego `in` lub. `out`</span><span class="sxs-lookup"><span data-stu-id="22a3c-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="22a3c-113">W poniższym przykładzie kodu pokazano, jak można utworzyć pełnomocnika, który ma kowariantyczny parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="22a3c-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
```csharp  
// Type T is declared covariant by using the out keyword.  
public delegate T SampleGenericDelegate <out T>();  
  
public static void Test()  
{  
    SampleGenericDelegate <String> dString = () => " ";  
  
    // You can assign delegates to each other,  
    // because the type T is declared covariant.  
    SampleGenericDelegate <Object> dObject = dString;
}  
```  
  
 <span data-ttu-id="22a3c-114">Jeśli używasz tylko obsługi wariancji, aby dopasować podpisy metody `in` do `out` typów delegatów i nie używać słów kluczowych i, może się okazać, że czasami można utworzyć wystąpienia delegatów z identycznych wyrażeń lambda lub metod, ale nie można przypisać jednego pełnomocnika do innego.</span><span class="sxs-lookup"><span data-stu-id="22a3c-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="22a3c-115">W poniższym przykładzie `SampleGenericDelegate<String>` kodu nie można `SampleGenericDelegate<Object>`jawnie `String` przekonwertować na , chociaż dziedziczy `Object`.</span><span class="sxs-lookup"><span data-stu-id="22a3c-115">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="22a3c-116">Ten problem można rozwiązać, oznaczając `T` `out` parametr ogólny słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="22a3c-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
```csharp  
public delegate T SampleGenericDelegate<T>();  
  
public static void Test()  
{  
    SampleGenericDelegate<String> dString = () => " ";  
  
    // You can assign the dObject delegate  
    // to the same lambda expression as dString delegate  
    // because of the variance support for
    // matching method signatures with delegate types.  
    SampleGenericDelegate<Object> dObject = () => " ";  
  
    // The following statement generates a compiler error  
    // because the generic type T is not marked as covariant.  
    // SampleGenericDelegate <Object> dObject = dString;  
  
}  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="22a3c-117">Delegaci ogólni, którzy mają parametry typu wariantu w ramach .NET Framework</span><span class="sxs-lookup"><span data-stu-id="22a3c-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="22a3c-118">.NET Framework 4 wprowadził obsługę wariancji dla parametrów typu ogólnego w kilku istniejących delegatów ogólnych:</span><span class="sxs-lookup"><span data-stu-id="22a3c-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
- <span data-ttu-id="22a3c-119">`Action`delegatów <xref:System> z obszaru nazw, <xref:System.Action%601> na przykład, i<xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="22a3c-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
- <span data-ttu-id="22a3c-120">`Func`delegatów <xref:System> z obszaru nazw, <xref:System.Func%601> na przykład, i<xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="22a3c-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
- <span data-ttu-id="22a3c-121">Pełnomocnik <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="22a3c-121">The <xref:System.Predicate%601> delegate</span></span>  
  
- <span data-ttu-id="22a3c-122">Pełnomocnik <xref:System.Comparison%601></span><span class="sxs-lookup"><span data-stu-id="22a3c-122">The <xref:System.Comparison%601> delegate</span></span>  
  
- <span data-ttu-id="22a3c-123">Pełnomocnik <xref:System.Converter%602></span><span class="sxs-lookup"><span data-stu-id="22a3c-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="22a3c-124">Aby uzyskać więcej informacji i przykładów, zobacz [Korzystanie z wariancji dla Func i akcji ogólnych delegatów (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="22a3c-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="22a3c-125">Deklarowanie parametrów typu wariantu w pełnomocnikach ogólnych</span><span class="sxs-lookup"><span data-stu-id="22a3c-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="22a3c-126">Jeśli delegat rodzajowy ma kowariantne lub przeciwwariantne parametry typu ogólnego, może być określany jako *wariant delegata ogólnego*.</span><span class="sxs-lookup"><span data-stu-id="22a3c-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="22a3c-127">Można zadeklarować covariant parametr urodzajny parametr u `out` rodzajowy delegata przy użyciu słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="22a3c-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="22a3c-128">Typ kowariantywny może służyć tylko jako typ zwracany metody, a nie jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="22a3c-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="22a3c-129">W poniższym przykładzie kodu pokazano, jak zadeklarować współwariantowego delegata ogólnego.</span><span class="sxs-lookup"><span data-stu-id="22a3c-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="22a3c-130">Można zadeklarować kontrawarianty parametru typu ogólnego w `in` delegacie rodzajowym za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="22a3c-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="22a3c-131">Typ przeciwwariantny może służyć tylko jako typ argumentów metody, a nie jako typ zwracany metody.</span><span class="sxs-lookup"><span data-stu-id="22a3c-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="22a3c-132">W poniższym przykładzie kodu pokazano, jak zadeklarować kontrataki delegata ogólnego.</span><span class="sxs-lookup"><span data-stu-id="22a3c-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="22a3c-133">`ref`, `in`a `out` parametry w języku C# nie mogą być oznaczone jako wariant.</span><span class="sxs-lookup"><span data-stu-id="22a3c-133">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="22a3c-134">Możliwe jest również obsługa wariancji i kowariancji w tym samym delegata, ale dla różnych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="22a3c-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="22a3c-135">Jest to pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="22a3c-135">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="22a3c-136">Tworzenie wystąpienia i wywoływanie delegatów ogólnych wariantów</span><span class="sxs-lookup"><span data-stu-id="22a3c-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="22a3c-137">Można utworzyć wystąpienia i wywołać delegatów warianttak jak wystąpienia i wywołać delegatów niezmienne.</span><span class="sxs-lookup"><span data-stu-id="22a3c-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="22a3c-138">W poniższym przykładzie delegat akcjonorpii jest tworzone przez wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="22a3c-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="22a3c-139">Łączenie delegatów ogólnych wariantów</span><span class="sxs-lookup"><span data-stu-id="22a3c-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="22a3c-140">Nie należy łączyć delegatów wariantu.</span><span class="sxs-lookup"><span data-stu-id="22a3c-140">You should not combine variant delegates.</span></span> <span data-ttu-id="22a3c-141">Metoda <xref:System.Delegate.Combine%2A> nie obsługuje konwersji delegata wariantu i oczekuje delegatów, które mają być dokładnie tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="22a3c-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="22a3c-142">Może to prowadzić do wyjątku w czasie wykonywania <xref:System.Delegate.Combine%2A> podczas łączenia `+` delegatów za pomocą metody lub za pomocą operatora, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="22a3c-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="22a3c-143">Wariancja w parametrach typu ogólnego dla typów wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="22a3c-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="22a3c-144">Odchylenie dla parametrów typu ogólnego jest obsługiwane tylko dla typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="22a3c-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="22a3c-145">Na przykład `DVariant<int>` nie można niejawnie `DVariant<Object>` przekonwertować na lub `DVariant<long>`, ponieważ liczba całkowita jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="22a3c-145">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="22a3c-146">W poniższym przykładzie pokazano, że wariancja w parametrach typu ogólnego nie jest obsługiwana dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="22a3c-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
```csharp  
// The type T is covariant.  
public delegate T DVariant<out T>();  
  
// The type T is invariant.  
public delegate T DInvariant<T>();  
  
public static void Test()  
{  
    int i = 0;  
    DInvariant<int> dInt = () => i;  
    DVariant<int> dVariantInt = () => i;  
  
    // All of the following statements generate a compiler error  
    // because type variance in generic parameters is not supported  
    // for value types, even if generic type parameters are declared variant.  
    // DInvariant<Object> dObject = dInt;  
    // DInvariant<long> dLong = dInt;  
    // DVariant<Object> dVariantObject = dVariantInt;  
    // DVariant<long> dVariantLong = dVariantInt;
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="22a3c-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22a3c-147">See also</span></span>

- [<span data-ttu-id="22a3c-148">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="22a3c-148">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="22a3c-149">Używanie wariancji dla delegatów ogólnych akcji i akcji (C#)</span><span class="sxs-lookup"><span data-stu-id="22a3c-149">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
- [<span data-ttu-id="22a3c-150">Jak połączyć delegatów (delegatów multiemisji)</span><span class="sxs-lookup"><span data-stu-id="22a3c-150">How to combine delegates (Multicast Delegates)</span></span>](../../delegates/how-to-combine-delegates-multicast-delegates.md)
