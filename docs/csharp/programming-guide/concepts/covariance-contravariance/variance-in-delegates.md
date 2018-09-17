---
title: Wariancje w Delegatach (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 3dabac4e532198871cf05d639aa692751ab17ae1
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746994"
---
# <a name="variance-in-delegates-c"></a><span data-ttu-id="6f363-102">Wariancje w Delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="6f363-102">Variance in Delegates (C#)</span></span>
<span data-ttu-id="6f363-103">.NET framework 3.5 wprowadzono obsługę wariancji podpisów metod dopasowania z typów obiektów delegowanych w wszystkie obiekty delegowane w języku C#.</span><span class="sxs-lookup"><span data-stu-id="6f363-103">.NET Framework 3.5 introduced variance support for matching method signatures with delegate types in all delegates in C#.</span></span> <span data-ttu-id="6f363-104">Oznacza to, że można przypisać do deleguje nie tylko metody, które pasują do sygnatur, ale także metody, które zwracają więcej pochodne typy (korelacja) lub które przyjmują parametry, które mają mniej pochodne typy (kontrawariancja) niż określona przez typ delegata .</span><span class="sxs-lookup"><span data-stu-id="6f363-104">This means that you can assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="6f363-105">Dotyczy to również delegatów ogólnych i nieogólnych.</span><span class="sxs-lookup"><span data-stu-id="6f363-105">This includes both generic and non-generic delegates.</span></span>  
  
 <span data-ttu-id="6f363-106">Na przykład rozważmy następujący kod, który ma dwie klasy i dwa delegaty: ogólnych i nieogólnych.</span><span class="sxs-lookup"><span data-stu-id="6f363-106">For example, consider the following code, which has two classes and two delegates: generic and non-generic.</span></span>  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 <span data-ttu-id="6f363-107">Po utworzeniu delegatów `SampleDelegate` lub `SampleGenericDelegate<A, R>` typów, w jednej z następujących metod można przypisać do tych obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="6f363-107">When you create delegates of the `SampleDelegate` or `SampleGenericDelegate<A, R>` types, you can assign any one of the following methods to those delegates.</span></span>  
  
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
  
 <span data-ttu-id="6f363-108">Poniższy przykład kodu ilustruje niejawna konwersja między podpis metody i typu delegata.</span><span class="sxs-lookup"><span data-stu-id="6f363-108">The following code example illustrates the implicit conversion between the method signature and the delegate type.</span></span>  
  
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
  
 <span data-ttu-id="6f363-109">Aby uzyskać więcej przykładów, zobacz [przy użyciu wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) i [przy użyciu wariancji dla akcji delegatów ogólnych (C#) Func i](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="6f363-109">For more examples, see [Using Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
## <a name="variance-in-generic-type-parameters"></a><span data-ttu-id="6f363-110">Wariancji w parametrach typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="6f363-110">Variance in Generic Type Parameters</span></span>  
 <span data-ttu-id="6f363-111">W programie .NET Framework 4 lub nowszym można włączyć niejawna konwersja między elementem delegatów, dzięki czemu delegatów ogólnych, które mają różne typy określona przez parametry typu ogólnego mogą być przypisane do siebie nawzajem, jeśli typy są dziedziczone od siebie nawzajem, zgodnie z wymaganiami WARIANCJA.</span><span class="sxs-lookup"><span data-stu-id="6f363-111">In .NET Framework 4 or later you can enable implicit conversion between delegates, so that generic delegates that have different types specified by generic type parameters can be assigned to each other, if the types are inherited from each other as required by variance.</span></span>  
  
 <span data-ttu-id="6f363-112">Aby włączyć niejawną konwersję, musisz jawnie deklarować parametrów ogólnych w delegatów jako kowariantnych lub kontrawariantnych przy użyciu `in` lub `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="6f363-112">To enable implicit conversion, you must explicitly declare generic parameters in a delegate as covariant or contravariant by using the `in` or `out` keyword.</span></span>  
  
 <span data-ttu-id="6f363-113">Poniższy przykład kodu pokazuje, jak utworzyć obiekt delegowany mający parametr kowariantnego typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="6f363-113">The following code example shows how you can create a delegate that has a covariant generic type parameter.</span></span>  
  
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
  
 <span data-ttu-id="6f363-114">Jeśli używasz obsługują tylko odchylenia do dopasowania podpisy metod ze typy delegatów i nie używaj `in` i `out` słów kluczowych, może się okazać, że czasami można utworzyć wystąpienie obiektów delegowanych z wyrażenia lambda identyczne lub metody, ale nie jest możliwe Przypisz jednego delegata do innego.</span><span class="sxs-lookup"><span data-stu-id="6f363-114">If you use only variance support to match method signatures with delegate types and do not use the `in` and `out` keywords, you may find that sometimes you can instantiate delegates with identical lambda expressions or methods, but you cannot assign one delegate to another.</span></span>  
  
 <span data-ttu-id="6f363-115">W poniższym przykładzie kodu `SampleGenericDelegate<String>` nie może być jawnie konwertowane na `SampleGenericDelegate<Object>`, mimo że `String` dziedziczy `Object`.</span><span class="sxs-lookup"><span data-stu-id="6f363-115">In the following code example, `SampleGenericDelegate<String>` cannot be explicitly converted to `SampleGenericDelegate<Object>`, although `String` inherits `Object`.</span></span> <span data-ttu-id="6f363-116">Możesz rozwiązać ten problem, oznaczając parametru ogólnego `T` z `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="6f363-116">You can fix this problem by marking the generic parameter `T` with the `out` keyword.</span></span>  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a><span data-ttu-id="6f363-117">Parametry typu delegatów ogólnych, które mają typ Variant w .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f363-117">Generic Delegates That Have Variant Type Parameters in the .NET Framework</span></span>  
 <span data-ttu-id="6f363-118">.NET framework 4 wprowadzono obsługę wariancji dla parametrów typu rodzajowego w kilku istniejących delegatów ogólnych:</span><span class="sxs-lookup"><span data-stu-id="6f363-118">.NET Framework 4 introduced variance support for generic type parameters in several existing generic delegates:</span></span>  
  
-   <span data-ttu-id="6f363-119">`Action` delegaty z <xref:System> przestrzeni nazw, na przykład <xref:System.Action%601> i <xref:System.Action%602></span><span class="sxs-lookup"><span data-stu-id="6f363-119">`Action` delegates from the <xref:System> namespace, for example, <xref:System.Action%601> and <xref:System.Action%602></span></span>  
  
-   <span data-ttu-id="6f363-120">`Func` delegaty z <xref:System> przestrzeni nazw, na przykład <xref:System.Func%601> i <xref:System.Func%602></span><span class="sxs-lookup"><span data-stu-id="6f363-120">`Func` delegates from the <xref:System> namespace, for example, <xref:System.Func%601> and <xref:System.Func%602></span></span>  
  
-   <span data-ttu-id="6f363-121"><xref:System.Predicate%601> Delegowanie</span><span class="sxs-lookup"><span data-stu-id="6f363-121">The <xref:System.Predicate%601> delegate</span></span>  
  
-   <span data-ttu-id="6f363-122"><xref:System.Comparison%601> Delegowanie</span><span class="sxs-lookup"><span data-stu-id="6f363-122">The <xref:System.Comparison%601> delegate</span></span>  
  
-   <span data-ttu-id="6f363-123"><xref:System.Converter%602> Delegowanie</span><span class="sxs-lookup"><span data-stu-id="6f363-123">The <xref:System.Converter%602> delegate</span></span>  
  
 <span data-ttu-id="6f363-124">Aby uzyskać więcej informacji i przykładów, zobacz [przy użyciu wariancji dla akcji delegatów ogólnych (C#) Func i](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="6f363-124">For more information and examples, see [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a><span data-ttu-id="6f363-125">Deklarowanie Wariantne parametry typu w delegatów ogólnych</span><span class="sxs-lookup"><span data-stu-id="6f363-125">Declaring Variant Type Parameters in Generic Delegates</span></span>  
 <span data-ttu-id="6f363-126">Jeśli delegata ogólnego ma kowariantne i kontrawariantne parametry typu ogólnego, jego mogą być określane jako *variant Delegat ogólny*.</span><span class="sxs-lookup"><span data-stu-id="6f363-126">If a generic delegate has covariant or contravariant generic type parameters, it can be referred to as a *variant generic delegate*.</span></span>  
  
 <span data-ttu-id="6f363-127">Można zadeklarować parametru typu generycznego kowariantne Delegat ogólny przy użyciu `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="6f363-127">You can declare a generic type parameter covariant in a generic delegate by using the `out` keyword.</span></span> <span data-ttu-id="6f363-128">Kowariantnego typu może służyć jedynie jako typ zwracany metody, a nie typu argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="6f363-128">The covariant type can be used only as a method return type and not as a type of method arguments.</span></span> <span data-ttu-id="6f363-129">Poniższy przykład kodu pokazuje sposób deklarowania kowariantne Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="6f363-129">The following code example shows how to declare a covariant generic delegate.</span></span>  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 <span data-ttu-id="6f363-130">Kontrawariantnego parametru typu ogólnego, Delegat ogólny może zadeklarować za pomocą `in` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="6f363-130">You can declare a generic type parameter contravariant in a generic delegate by using the `in` keyword.</span></span> <span data-ttu-id="6f363-131">Typ kontrawariantne może służyć jedynie jako typów argumentów metody, a nie typem zwracanym metody.</span><span class="sxs-lookup"><span data-stu-id="6f363-131">The contravariant type can be used only as a type of method arguments and not as a method return type.</span></span> <span data-ttu-id="6f363-132">Poniższy przykład kodu pokazuje sposób deklarowania to delegat generyczny kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="6f363-132">The following code example shows how to declare a contravariant generic delegate.</span></span>  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="6f363-133">`ref`, `in`, i `out` parametrów w języku C# nie można oznaczyć jako wariant.</span><span class="sxs-lookup"><span data-stu-id="6f363-133">`ref`, `in`, and `out` parameters in C# can't be marked as variant.</span></span>  
  
 <span data-ttu-id="6f363-134">Istnieje również możliwość obsługi kowariancji i Wariancja w tym samym delegatów, ale w przypadku różnych typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="6f363-134">It is also possible to support both variance and covariance in the same delegate, but for different type parameters.</span></span> <span data-ttu-id="6f363-135">Jest to pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6f363-135">This is shown in the following example.</span></span>  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a><span data-ttu-id="6f363-136">Utworzenie wystąpienia i wywoływania wariantów ogólnych delegatów</span><span class="sxs-lookup"><span data-stu-id="6f363-136">Instantiating and Invoking Variant Generic Delegates</span></span>  
 <span data-ttu-id="6f363-137">Można utworzyć wystąpienia i wywoływać delegatów typu variant, tak samo, jak utworzyć wystąpienia i wywoływać delegatów niezmiennej.</span><span class="sxs-lookup"><span data-stu-id="6f363-137">You can instantiate and invoke variant delegates just as you instantiate and invoke invariant delegates.</span></span> <span data-ttu-id="6f363-138">W poniższym przykładzie delegat jest tworzone przez wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="6f363-138">In the following example, the delegate is instantiated by a lambda expression.</span></span>  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a><span data-ttu-id="6f363-139">Łączenie delegatów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="6f363-139">Combining Variant Generic Delegates</span></span>  
 <span data-ttu-id="6f363-140">Nie należy łączyć wariantu delegatów.</span><span class="sxs-lookup"><span data-stu-id="6f363-140">You should not combine variant delegates.</span></span> <span data-ttu-id="6f363-141"><xref:System.Delegate.Combine%2A> Metoda nie obsługuje konwersji typu variant delegata i oczekuje, że delegaty dokładnie tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="6f363-141">The <xref:System.Delegate.Combine%2A> method does not support variant delegate conversion and expects delegates to be of exactly the same type.</span></span> <span data-ttu-id="6f363-142">Może to prowadzić do wyjątku czasu wykonywania, podczas łączenia przy użyciu delegatów <xref:System.Delegate.Combine%2A> metody lub używając `+` operatora, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="6f363-142">This can lead to a run-time exception when you combine delegates either by using the <xref:System.Delegate.Combine%2A> method or by using the `+` operator, as shown in the following code example.</span></span>  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a><span data-ttu-id="6f363-143">Wariancji w parametrach typu ogólnego dla wartości i typy odwołań</span><span class="sxs-lookup"><span data-stu-id="6f363-143">Variance in Generic Type Parameters for Value and Reference Types</span></span>  
 <span data-ttu-id="6f363-144">Wariancja dla parametrów typu ogólnego jest obsługiwana tylko dla typów odwołania.</span><span class="sxs-lookup"><span data-stu-id="6f363-144">Variance for generic type parameters is supported for reference types only.</span></span> <span data-ttu-id="6f363-145">Na przykład `DVariant<int>` nie może być niejawnie konwertowane na `DVariant<Object>` lub `DVariant<long>`, ponieważ liczba całkowita jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="6f363-145">For example, `DVariant<int>` can't be implicitly converted to `DVariant<Object>` or `DVariant<long>`, because integer is a value type.</span></span>  
  
 <span data-ttu-id="6f363-146">W poniższym przykładzie pokazano tej wariancji w typie ogólnym parametrów nie jest obsługiwana dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="6f363-146">The following example demonstrates that variance in generic type parameters is not supported for value types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f363-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f363-147">See Also</span></span>

- [<span data-ttu-id="6f363-148">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="6f363-148">Generics</span></span>](~/docs/standard/generics/index.md)  
- [<span data-ttu-id="6f363-149">Korzystanie z wariancji dla Func i akcji delegatów ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="6f363-149">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)  
- [<span data-ttu-id="6f363-150">Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji)</span><span class="sxs-lookup"><span data-stu-id="6f363-150">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
