---
title: Wariancja w delegatach (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: a65b2fb84e2eae57eecaf5307ca76fbce412d44c
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772042"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="b1e62-102">Wariancja w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="b1e62-102">Variance in Delegates (C#)</span></span>
<span data-ttu-id="b1e62-103">.NET Framework 3,5 wprowadzono obsługę wariancji dla pasujących sygnatur metod z typami delegatów we C#wszystkich delegatach w.</span><span class="sxs-lookup"><span data-stu-id="b1e62-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="b1e62-104">Oznacza to, że można przypisać do delegatów nie tylko metod, które mają pasujące podpisy, ale również metody, które zwracają więcej typów pochodnych (Kowariancja) lub akceptują parametry, które mają mniej pochodne typy (kontrawariancja) niż określone przez typ delegata .</span><span class="sxs-lookup"><span data-stu-id="b1e62-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="b1e62-105">Dotyczy to zarówno delegatów rodzajowych, jak i nieogólnych.</span><span class="sxs-lookup"><span data-stu-id="b1e62-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="b1e62-106">Rozważmy na przykład poniższy kod, który ma dwie klasy i dwa Delegaty: generyczne i nieogólne.</span><span class="sxs-lookup"><span data-stu-id="b1e62-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="b1e62-107">Podczas tworzenia delegatów typów `SampleDelegate` lub `SampleGenericDelegate<A, R>` można przypisać do tych delegatów jedną z następujących metod.</span><span class="sxs-lookup"><span data-stu-id="b1e62-107">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="b1e62-108">Poniższy przykład kodu ilustruje niejawną konwersję między sygnaturą metody a typem delegata.</span><span class="sxs-lookup"><span data-stu-id="b1e62-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="b1e62-109">Aby uzyskać więcej przykładów, zobacz [Korzystanie z wariancjiC#w delegatach ()](./using-variance-in-delegates.md) i [Używanie wariancji dla delegatów funkcji Func i Action (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="b1e62-109">For more examples, see [Using Variance in Delegates (C#)](./using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="b1e62-110">Wariancja w parametrach typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="b1e62-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="b1e62-111">W .NET Framework 4 lub nowszej można włączyć niejawną konwersję między delegatami, tak aby generyczne Delegaty mające różne typy określone przez parametry typu generycznego można przypisać do siebie nawzajem, jeśli typy są dziedziczone od siebie, zgodnie z wymaganiami względem.</span><span class="sxs-lookup"><span data-stu-id="b1e62-111">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="b1e62-112">Aby włączyć niejawną konwersję, należy jawnie zadeklarować parametry ogólne w delegatze jako współvariant lub kontrawariantne za pomocą słowa kluczowego `in` lub `out`.</span><span class="sxs-lookup"><span data-stu-id="b1e62-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="b1e62-113">Poniższy przykład kodu pokazuje, jak można utworzyć delegata, który ma parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b1e62-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="b1e62-114">Jeśli używasz tylko wariancji do dopasowania sygnatur metod z typami delegatów i nie używaj `in` i `out` słowa kluczowe, może się okazać, że czasami można utworzyć wystąpienia delegatów z identycznymi wyrażeniami lambda lub metodami, ale nie można przypisać jednej Deleguj do innego.</span><span class="sxs-lookup"><span data-stu-id="b1e62-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="b1e62-115">W poniższym przykładzie kodu `SampleGenericDelegate<String>` nie można jawnie przekonwertować na `SampleGenericDelegate<Object>`, chociaż `String` dziedziczy `Object`.</span><span class="sxs-lookup"><span data-stu-id="b1e62-115">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="b1e62-116">Możesz rozwiązać ten problem, zaznaczając parametr generyczny `T` za pomocą słowa kluczowego `out`.</span><span class="sxs-lookup"><span data-stu-id="b1e62-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="b1e62-117">Delegaty ogólne, które mają parametry typu Variant w .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b1e62-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="b1e62-118">.NET Framework 4 wprowadził obsługę wariancji dla parametrów typu ogólnego w kilku istniejących delegatach ogólnych:</span><span class="sxs-lookup"><span data-stu-id="b1e62-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
- <span data-ttu-id="b1e62-119">`Action` delegatów z przestrzeni nazw <xref:System>, na przykład <xref:System.Action%601> i <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="b1e62-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
- <span data-ttu-id="b1e62-120">`Func` delegatów z przestrzeni nazw <xref:System>, na przykład <xref:System.Func%601> i <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="b1e62-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
- <span data-ttu-id="b1e62-121">Delegat <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="b1e62-121">The <xref:System.Predicate%601> delegate</span></span>  
  
- <span data-ttu-id="b1e62-122">Delegat <xref:System.Comparison%601></span><span class="sxs-lookup"><span data-stu-id="b1e62-122">The <xref:System.Comparison%601> delegate</span></span>  
  
- <span data-ttu-id="b1e62-123">Delegat <xref:System.Converter%602></span><span class="sxs-lookup"><span data-stu-id="b1e62-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="b1e62-124">Aby uzyskać więcej informacji i przykładów, zobacz [Używanie wariancji dla delegatów ()C#funkcji Func i Action ()](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="b1e62-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="b1e62-125">Deklarowanie parametrów typu Variant w delegatach generycznych</span><span class="sxs-lookup"><span data-stu-id="b1e62-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="b1e62-126">Jeśli delegat generyczny ma parametry typu generycznego lub kontrawariantne, może być określany jako *Delegat generyczny elementu Variant*.</span><span class="sxs-lookup"><span data-stu-id="b1e62-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="b1e62-127">Za pomocą słowa kluczowego `out` można zadeklarować współwariant parametru typu ogólnego w delegatze ogólnym.</span><span class="sxs-lookup"><span data-stu-id="b1e62-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="b1e62-128">Typ współwariantu może być używany tylko jako zwracany typ metody, a nie jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="b1e62-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="b1e62-129">Poniższy przykład kodu pokazuje, jak zadeklarować delegata generycznego.</span><span class="sxs-lookup"><span data-stu-id="b1e62-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="b1e62-130">Parametry typu ogólnego kontrawariantne można zadeklarować w delegatze ogólnym za pomocą słowa kluczowego `in`.</span><span class="sxs-lookup"><span data-stu-id="b1e62-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="b1e62-131">Typ kontrawariantne może być używany tylko jako typ argumentów metody, a nie jako zwracany typ metody.</span><span class="sxs-lookup"><span data-stu-id="b1e62-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="b1e62-132">Poniższy przykład kodu pokazuje, jak zadeklarować delegata generycznego kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="b1e62-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="b1e62-133">parametrów `ref`, `in` i `out` w programie C# nie można oznaczyć jako VARIANT.</span><span class="sxs-lookup"><span data-stu-id="b1e62-133">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="b1e62-134">Istnieje również możliwość obsługi zarówno wariancji, jak i kowariancji w tym samym delegatze, ale dla różnych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="b1e62-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="b1e62-135">Pokazano to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b1e62-135">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="b1e62-136">Tworzenie wystąpień i wywoływanie delegatów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="b1e62-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="b1e62-137">Można tworzyć wystąpienia delegatów wariantów i wywoływać je tak samo jak w przypadku wystąpienia i wywoływać delegatów niezmiennej.</span><span class="sxs-lookup"><span data-stu-id="b1e62-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="b1e62-138">W poniższym przykładzie obiekt delegowany jest tworzone przez wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="b1e62-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="b1e62-139">Łączenie delegatów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="b1e62-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="b1e62-140">Nie należy łączyć delegatów wariantów.</span><span class="sxs-lookup"><span data-stu-id="b1e62-140">You should not combine variant delegates.</span></span> <span data-ttu-id="b1e62-141">Metoda <xref:System.Delegate.Combine%2A> nie obsługuje konwersji delegata typu Variant i oczekuje, że Delegaty będą dokładnie tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="b1e62-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="b1e62-142">Może to prowadzić do wyjątku czasu wykonywania podczas łączenia delegatów za pomocą metody <xref:System.Delegate.Combine%2A> lub przy użyciu operatora `+`, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="b1e62-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="b1e62-143">Wariancja w parametrach typu ogólnego dla typów wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="b1e62-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="b1e62-144">WARIANCJA dla parametrów typu ogólnego jest obsługiwana tylko w przypadku typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="b1e62-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="b1e62-145">Na przykład `DVariant<int>` nie może być niejawnie konwertowany na `DVariant<Object>` lub `DVariant<long>`, ponieważ liczba całkowita jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="b1e62-145">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="b1e62-146">W poniższym przykładzie pokazano, że Wariancja w parametrach typu ogólnego nie jest obsługiwana w przypadku typów wartości.</span><span class="sxs-lookup"><span data-stu-id="b1e62-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1e62-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1e62-147">See also</span></span>

- [<span data-ttu-id="b1e62-148">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="b1e62-148">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="b1e62-149">Korzystanie z wariancji dla delegatów dla funkcjiC#Func i Action ()</span><span class="sxs-lookup"><span data-stu-id="b1e62-149">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
- [<span data-ttu-id="b1e62-150">Instrukcje: łączenie delegatów (delegatów multiemisji)</span><span class="sxs-lookup"><span data-stu-id="b1e62-150">How to: Combine Delegates (Multicast Delegates)</span></span>](../../delegates/how-to-combine-delegates-multicast-delegates.md)
