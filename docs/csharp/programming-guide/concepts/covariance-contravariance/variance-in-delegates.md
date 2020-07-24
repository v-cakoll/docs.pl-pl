---
title: Wariancja w delegatach (C#)
description: Dowiedz się, jak obsługa wariancji w .NET Framework pozwala dopasować sygnatury metod z typami delegatów we wszystkich delegatach.
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: ef57a7fa7feaef98a47822e3f1c9242d0205932d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105653"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="7cb4c-103">Wariancja w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="7cb4c-103">Variance in Delegates (C#)</span></span>
<span data-ttu-id="7cb4c-104">.NET Framework 3,5 wprowadza obsługę wariancji dla pasujących sygnatur metod z typami delegatów we wszystkich delegatach w języku C#.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-104">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="7cb4c-105">Oznacza to, że można przypisać do delegatów nie tylko metod, które mają pasujące podpisy, ale również metody, które zwracają więcej typów pochodnych (Kowariancja) lub akceptują parametry, które mają mniej pochodne typy (kontrawariancja) niż określone przez typ delegata.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-105">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="7cb4c-106">Dotyczy to zarówno delegatów rodzajowych, jak i nieogólnych.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-106">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="7cb4c-107">Rozważmy na przykład poniższy kod, który ma dwie klasy i dwa Delegaty: generyczne i nieogólne.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-107">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="7cb4c-108">Podczas tworzenia delegatów `SampleDelegate` lub typów można `SampleGenericDelegate<A, R>` przypisać do tych delegatów jedną z następujących metod.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-108">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="7cb4c-109">Poniższy przykład kodu ilustruje niejawną konwersję między sygnaturą metody a typem delegata.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-109">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="7cb4c-110">Aby uzyskać więcej przykładów, zobacz [Korzystanie z wariancji w delegatach (c#)](./using-variance-in-delegates.md) i [Używanie wariancji dla delegatów funkcji Func i Action (c#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="7cb4c-110">For more examples, see [Using Variance in Delegates (C#)](./using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="7cb4c-111">Wariancja w parametrach typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="7cb4c-111">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="7cb4c-112">W .NET Framework 4 lub nowszej można włączyć niejawną konwersję między delegatami, tak aby generyczne Delegaty mające różne typy określone przez parametry typu generycznego można przypisać do siebie nawzajem, jeśli typy są dziedziczone od siebie, zgodnie z wymaganiami wariancji.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-112">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="7cb4c-113">Aby włączyć niejawną konwersję, należy jawnie zadeklarować parametry ogólne w delegatze jako współvariant lub kontrawariantne za pomocą `in` `out` słowa kluczowego or.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-113">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="7cb4c-114">Poniższy przykład kodu pokazuje, jak można utworzyć delegata, który ma parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-114">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="7cb4c-115">Jeśli używasz tylko wariancji do dopasowania sygnatur metod z typami delegatów i nie używaj `in` `out` słów kluczowych i, możesz się dowiedzieć, że czasami można utworzyć wystąpienia delegatów z identycznymi wyrażeniami lambda lub metodami, ale nie można przypisać jednego delegata do innego.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-115">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="7cb4c-116">W poniższym przykładzie kodu `SampleGenericDelegate<String>` nie można jawnie przekonwertować na `SampleGenericDelegate<Object>` , chociaż `String` dziedziczy `Object` .</span><span class="sxs-lookup"><span data-stu-id="7cb4c-116">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="7cb4c-117">Ten problem można rozwiązać przez oznaczenie parametru generycznego `T` `out` słowem kluczowym.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-117">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-net"></a><span data-ttu-id="7cb4c-118">Delegaty ogólne, które mają parametry typu Variant w programie .NET</span><span class="sxs-lookup"><span data-stu-id="7cb4c-118">Generic Delegates That Have Variant Type Parameters in .NET</span></span>

<span data-ttu-id="7cb4c-119">.NET Framework 4 wprowadził obsługę wariancji dla parametrów typu ogólnego w kilku istniejących delegatach ogólnych:</span><span class="sxs-lookup"><span data-stu-id="7cb4c-119">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
- <span data-ttu-id="7cb4c-120">`Action`deleguje z <xref:System> przestrzeni nazw, na przykład, <xref:System.Action%601> i<xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="7cb4c-120">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
- <span data-ttu-id="7cb4c-121">`Func`deleguje z <xref:System> przestrzeni nazw, na przykład, <xref:System.Func%601> i<xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="7cb4c-121">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
- <span data-ttu-id="7cb4c-122"><xref:System.Predicate%601>Obiekt delegowany</span><span class="sxs-lookup"><span data-stu-id="7cb4c-122">The <xref:System.Predicate%601> delegate</span></span>  
  
- <span data-ttu-id="7cb4c-123"><xref:System.Comparison%601>Obiekt delegowany</span><span class="sxs-lookup"><span data-stu-id="7cb4c-123">The <xref:System.Comparison%601> delegate</span></span>  
  
- <span data-ttu-id="7cb4c-124"><xref:System.Converter%602>Obiekt delegowany</span><span class="sxs-lookup"><span data-stu-id="7cb4c-124">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="7cb4c-125">Aby uzyskać więcej informacji i przykładów, zobacz [Używanie wariancji dla delegatów funkcji Func i Action (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="7cb4c-125">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="7cb4c-126">Deklarowanie parametrów typu Variant w delegatach generycznych</span><span class="sxs-lookup"><span data-stu-id="7cb4c-126">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="7cb4c-127">Jeśli delegat generyczny ma parametry typu generycznego lub kontrawariantne, może być określany jako *Delegat generyczny elementu Variant*.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-127">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="7cb4c-128">Za pomocą słowa kluczowego można zadeklarować współwariant parametru typu ogólnego w delegatze ogólnym `out` .</span><span class="sxs-lookup"><span data-stu-id="7cb4c-128">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="7cb4c-129">Typ współwariantu może być używany tylko jako zwracany typ metody, a nie jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-129">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="7cb4c-130">Poniższy przykład kodu pokazuje, jak zadeklarować delegata generycznego.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-130">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="7cb4c-131">Parametr typu ogólnego kontrawariantne można zadeklarować w delegatze ogólnym za pomocą `in` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-131">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="7cb4c-132">Typ kontrawariantne może być używany tylko jako typ argumentów metody, a nie jako zwracany typ metody.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-132">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="7cb4c-133">Poniższy przykład kodu pokazuje, jak zadeklarować delegata generycznego kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-133">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="7cb4c-134">`ref`, `in` , i `out` Parametry w języku C# nie mogą być oznaczone jako VARIANT.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-134">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="7cb4c-135">Istnieje również możliwość obsługi zarówno wariancji, jak i kowariancji w tym samym delegatze, ale dla różnych parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-135">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="7cb4c-136">Pokazano to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-136">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="7cb4c-137">Tworzenie wystąpień i wywoływanie delegatów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="7cb4c-137">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="7cb4c-138">Można tworzyć wystąpienia delegatów wariantów i wywoływać je tak samo jak w przypadku wystąpienia i wywoływać delegatów niezmiennej.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-138">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="7cb4c-139">W poniższym przykładzie obiekt delegowany jest tworzone przez wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-139">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="7cb4c-140">Łączenie delegatów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="7cb4c-140">Combining Variant Generic Delegates</span></span>  

<span data-ttu-id="7cb4c-141">Nie łącz delegatów wariantów.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-141">Don't combine variant delegates.</span></span> <span data-ttu-id="7cb4c-142"><xref:System.Delegate.Combine%2A>Metoda nie obsługuje konwersji delegata typu Variant i oczekuje, że Delegaty mają być dokładnie tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-142">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="7cb4c-143">Może to prowadzić do wyjątku czasu wykonywania podczas łączenia delegatów za pomocą <xref:System.Delegate.Combine%2A> metody lub przy użyciu `+` operatora, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-143">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="7cb4c-144">Wariancja w parametrach typu ogólnego dla typów wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="7cb4c-144">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="7cb4c-145">WARIANCJA dla parametrów typu ogólnego jest obsługiwana tylko w przypadku typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-145">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="7cb4c-146">Na przykład `DVariant<int>` nie można konwertować niejawnie na `DVariant<Object>` lub `DVariant<long>` , ponieważ liczba całkowita jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-146">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="7cb4c-147">W poniższym przykładzie pokazano, że Wariancja w parametrach typu ogólnego nie jest obsługiwana w przypadku typów wartości.</span><span class="sxs-lookup"><span data-stu-id="7cb4c-147">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7cb4c-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cb4c-148">See also</span></span>

- [<span data-ttu-id="7cb4c-149">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="7cb4c-149">Generics</span></span>](../../../../standard/generics/index.md)
- [<span data-ttu-id="7cb4c-150">Korzystanie z wariancji dla delegatów funkcji Func i Action (C#)</span><span class="sxs-lookup"><span data-stu-id="7cb4c-150">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
- [<span data-ttu-id="7cb4c-151">Jak łączyć delegatów (delegatów multiemisji)</span><span class="sxs-lookup"><span data-stu-id="7cb4c-151">How to combine delegates (Multicast Delegates)</span></span>](../../delegates/how-to-combine-delegates-multicast-delegates.md)
