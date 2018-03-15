---
title: Wariancje w Delegatach (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c29d4ddbf5f1f9ae80535a8a97651b296f3c1fb3
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="9175d-102">Wariancje w Delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="9175d-102">Variance in Delegates (C#)</span></span>
<span data-ttu-id="9175d-103">.NET framework 3.5 wprowadzono obsługę wariancję dopasowania podpisy metod typów delegata w wszystkich delegatów w języku C#.</span><span class="sxs-lookup"><span data-stu-id="9175d-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="9175d-104">Oznacza to, że można przypisać do deleguje nie tylko metody, które pasują do podpisów, ale również metody, które zwracają więcej pochodnych typów (kowariancja) lub akceptujących parametrów, które mają mniej typów pochodnych (kontrawariancja) od określonej przez typ delegata .</span><span class="sxs-lookup"><span data-stu-id="9175d-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="9175d-105">Dotyczy to również ogólne i inny niż ogólny delegatów.</span><span class="sxs-lookup"><span data-stu-id="9175d-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="9175d-106">Rozważmy na przykład następujący kod, który ma dwie klasy i delegaci dwóch: ogólne i inny niż ogólny.</span><span class="sxs-lookup"><span data-stu-id="9175d-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="9175d-107">Podczas tworzenia delegatów `SampleDelegate` lub `SampleGenericDelegate<A, R>` typów, w jednej z następujących metod można przypisać do tych obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="9175d-107">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second first)  
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
  
 <span data-ttu-id="9175d-108">Poniższy przykładowy kod przedstawia niejawna konwersja między podpis metody i typu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="9175d-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="9175d-109">Aby uzyskać więcej przykładów, zobacz [przy użyciu wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) i [przy użyciu wariancję Func i akcji Delegaty ogólne (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="9175d-109">For more examples, see [Using Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="9175d-110">Wariancje w parametry typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="9175d-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="9175d-111">W programie .NET Framework 4 lub nowszym można włączyć niejawna konwersja między delegatów, dzięki czemu delegaty ogólne, które mają różne typy określona przez parametry typu ogólnego można przypisać do siebie, jeśli typy są dziedziczone z sobą zgodnie z wymaganiami WARIANCJA.</span><span class="sxs-lookup"><span data-stu-id="9175d-111">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="9175d-112">Aby włączyć niejawna konwersja, musisz jawnie zadeklarować parametry ogólne delegat jako kowariantnego lub kontrawariantnego przy użyciu `in` lub `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="9175d-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="9175d-113">Poniższy przykład kodu pokazuje, jak można utworzyć delegata, który ma parametr typu kowariantnego ogólnego.</span><span class="sxs-lookup"><span data-stu-id="9175d-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="9175d-114">Jeśli używasz obsługują tylko wariancję odpowiadające podpisy metod z typów delegatów i nie używaj `in` i `out` słowa kluczowe, może się okazać, że czasami można utworzyć wystąpienia obiektów delegowanych z wyrażenia lambda identyczne lub metody, ale nie można wykonać Przypisz jednego delegata do innego.</span><span class="sxs-lookup"><span data-stu-id="9175d-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="9175d-115">W poniższym przykładzie kodu `SampleGenericDelegate<String>` nie można jawnie przekonwertować na `SampleGenericDelegate<Object>`, mimo że `String` dziedziczy `Object`.</span><span class="sxs-lookup"><span data-stu-id="9175d-115">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="9175d-116">Można rozwiązać ten problem, oznaczając parametru ogólnego `T` z `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="9175d-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="9175d-117">Delegaty ogólne, które mają typ Variant parametry typu w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9175d-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="9175d-118">.NET framework 4 wprowadzono obsługę wariancji dla parametrów typu ogólnego w kilka istniejących delegaty ogólne:</span><span class="sxs-lookup"><span data-stu-id="9175d-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="9175d-119">`Action` deleguje z <xref:System> przestrzeni nazw, na przykład <xref:System.Action%601> i <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="9175d-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="9175d-120">`Func` deleguje z <xref:System> przestrzeni nazw, na przykład <xref:System.Func%601> i <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="9175d-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="9175d-121"><xref:System.Predicate%601> Delegowanie</span><span class="sxs-lookup"><span data-stu-id="9175d-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="9175d-122"><xref:System.Comparison%601> Delegowanie</span><span class="sxs-lookup"><span data-stu-id="9175d-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="9175d-123"><xref:System.Converter%602> Delegowanie</span><span class="sxs-lookup"><span data-stu-id="9175d-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="9175d-124">Aby uzyskać dodatkowe informacje i przykłady, zobacz [wariancji Func i akcji Delegaty ogólne (C#) przy użyciu](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="9175d-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="9175d-125">Deklarowanie parametrów typu Variant w Delegaty ogólne</span><span class="sxs-lookup"><span data-stu-id="9175d-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="9175d-126">Jeśli Delegat ogólny ma kowariantnego lub kontrawariantnego parametry typu ogólnego, ona może być określana jako *variant Delegat ogólny*.</span><span class="sxs-lookup"><span data-stu-id="9175d-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="9175d-127">Można zadeklarować parametru typu ogólnego kowariantnego Delegat ogólny przy użyciu `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="9175d-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="9175d-128">Kowariantnego typu może służyć jedynie jako zwracany typ metody, a nie typu argumenty metody.</span><span class="sxs-lookup"><span data-stu-id="9175d-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="9175d-129">Poniższy przykład kodu pokazuje, jak można zadeklarować kowariantnego Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="9175d-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="9175d-130">Kontrawariantnego parametru typu ogólnego, Delegat ogólny można zadeklarować przy użyciu `in` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="9175d-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="9175d-131">Typ kontrawariantnego może służyć wyłącznie jako argumenty metody, a nie jako zwracany typ metody.</span><span class="sxs-lookup"><span data-stu-id="9175d-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="9175d-132">Poniższy przykład kodu pokazuje, jak można zadeklarować kontrawariantnego Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="9175d-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="9175d-133">`ref`, `in`, i `out` parametrów w języku C# nie można oznaczyć jako typ variant.</span><span class="sxs-lookup"><span data-stu-id="9175d-133">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="9175d-134">Istnieje również możliwość do obsługi wariancji i Kowariancja w tego samego obiektu delegowanego, ale także dla parametrów innego typu.</span><span class="sxs-lookup"><span data-stu-id="9175d-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="9175d-135">Przedstawiono to w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9175d-135">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="9175d-136">Tworzenie wystąpień i powoływanie delegatów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="9175d-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="9175d-137">Można utworzyć wystąpienia i wywołać variant delegatów tak samo, jak wystąpienia i wywoływać niezmiennej delegatów.</span><span class="sxs-lookup"><span data-stu-id="9175d-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="9175d-138">W poniższym przykładzie delegat jest utworzone przez wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="9175d-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="9175d-139">Łączenie Variant Delegaty ogólne</span><span class="sxs-lookup"><span data-stu-id="9175d-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="9175d-140">Nie należy łączyć variant delegatów.</span><span class="sxs-lookup"><span data-stu-id="9175d-140">You should not combine variant delegates.</span></span> <span data-ttu-id="9175d-141"><xref:System.Delegate.Combine%2A> — Metoda nie obsługuje konwersji typu variant delegata i oczekuje delegatów być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="9175d-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="9175d-142">Może to spowodować wyjątek czasu wykonywania podczas łączenia delegaty przy użyciu <xref:System.Delegate.Combine%2A> metody lub używając `+` operatora, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="9175d-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="9175d-143">Wariancje w parametry typu ogólnego dla wartości i typy referencyjne</span><span class="sxs-lookup"><span data-stu-id="9175d-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="9175d-144">Wariancji dla parametrów typu ogólnego jest obsługiwana tylko dla typów odniesienia.</span><span class="sxs-lookup"><span data-stu-id="9175d-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="9175d-145">Na przykład `DVariant<int>` nie można niejawnie przekonwertować `DVariant<Object>` lub `DVariant<long>`, ponieważ typ wartości jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="9175d-145">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="9175d-146">W poniższym przykładzie pokazano, że wariancji typu ogólnego parametrów nie jest obsługiwany dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="9175d-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9175d-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9175d-147">See Also</span></span>  
 [<span data-ttu-id="9175d-148">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="9175d-148">Generics</span></span>](~/docs/standard/generics/index.md)  
 [<span data-ttu-id="9175d-149">Korzystanie z wariancji dla Func i akcji Delegaty ogólne (C#)</span><span class="sxs-lookup"><span data-stu-id="9175d-149">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)  
 [<span data-ttu-id="9175d-150">Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji)</span><span class="sxs-lookup"><span data-stu-id="9175d-150">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
