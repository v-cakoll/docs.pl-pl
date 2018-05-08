---
title: Wariancje w Delegatach (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 8b74c29d8d94a31d30408131009d92e2b2a4281c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="variance-in-delegates-c"></a>Wariancje w Delegatach (C#)
.NET framework 3.5 wprowadzono obsługę wariancję dopasowania podpisy metod typów delegata w wszystkich delegatów w języku C#. Oznacza to, że można przypisać do deleguje nie tylko metody, które pasują do podpisów, ale również metody, które zwracają więcej pochodnych typów (kowariancja) lub akceptujących parametrów, które mają mniej typów pochodnych (kontrawariancja) od określonej przez typ delegata . Dotyczy to również ogólne i inny niż ogólny delegatów.  
  
 Rozważmy na przykład następujący kod, który ma dwie klasy i delegaci dwóch: ogólne i inny niż ogólny.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 Podczas tworzenia delegatów `SampleDelegate` lub `SampleGenericDelegate<A, R>` typów, w jednej z następujących metod można przypisać do tych obiektów delegowanych.  
  
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
  
 Poniższy przykładowy kod przedstawia niejawna konwersja między podpis metody i typu delegowanego.  
  
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
  
 Aby uzyskać więcej przykładów, zobacz [przy użyciu wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) i [przy użyciu wariancję Func i akcji Delegaty ogólne (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Wariancje w parametry typu ogólnego  
 W programie .NET Framework 4 lub nowszym można włączyć niejawna konwersja między delegatów, dzięki czemu delegaty ogólne, które mają różne typy określona przez parametry typu ogólnego można przypisać do siebie, jeśli typy są dziedziczone z sobą zgodnie z wymaganiami WARIANCJA.  
  
 Aby włączyć niejawna konwersja, musisz jawnie zadeklarować parametry ogólne delegat jako kowariantnego lub kontrawariantnego przy użyciu `in` lub `out` — słowo kluczowe.  
  
 Poniższy przykład kodu pokazuje, jak można utworzyć delegata, który ma parametr typu kowariantnego ogólnego.  
  
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
  
 Jeśli używasz obsługują tylko wariancję odpowiadające podpisy metod z typów delegatów i nie używaj `in` i `out` słowa kluczowe, może się okazać, że czasami można utworzyć wystąpienia obiektów delegowanych z wyrażenia lambda identyczne lub metody, ale nie można wykonać Przypisz jednego delegata do innego.  
  
 W poniższym przykładzie kodu `SampleGenericDelegate<String>` nie można jawnie przekonwertować na `SampleGenericDelegate<Object>`, mimo że `String` dziedziczy `Object`. Można rozwiązać ten problem, oznaczając parametru ogólnego `T` z `out` — słowo kluczowe.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Delegaty ogólne, które mają typ Variant parametry typu w programie .NET Framework  
 .NET framework 4 wprowadzono obsługę wariancji dla parametrów typu ogólnego w kilka istniejących delegaty ogólne:  
  
-   `Action` deleguje z <xref:System> przestrzeni nazw, na przykład <xref:System.Action%601> i <xref:System.Action%602>  
  
-   `Func` deleguje z <xref:System> przestrzeni nazw, na przykład <xref:System.Func%601> i <xref:System.Func%602>  
  
-   <xref:System.Predicate%601> Delegowanie  
  
-   <xref:System.Comparison%601> Delegowanie  
  
-   <xref:System.Converter%602> Delegowanie  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [wariancji Func i akcji Delegaty ogólne (C#) przy użyciu](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarowanie parametrów typu Variant w Delegaty ogólne  
 Jeśli Delegat ogólny ma kowariantnego lub kontrawariantnego parametry typu ogólnego, ona może być określana jako *variant Delegat ogólny*.  
  
 Można zadeklarować parametru typu ogólnego kowariantnego Delegat ogólny przy użyciu `out` — słowo kluczowe. Kowariantnego typu może służyć jedynie jako zwracany typ metody, a nie typu argumenty metody. Poniższy przykład kodu pokazuje, jak można zadeklarować kowariantnego Delegat ogólny.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 Kontrawariantnego parametru typu ogólnego, Delegat ogólny można zadeklarować przy użyciu `in` — słowo kluczowe. Typ kontrawariantnego może służyć wyłącznie jako argumenty metody, a nie jako zwracany typ metody. Poniższy przykład kodu pokazuje, jak można zadeklarować kontrawariantnego Delegat ogólny.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  `ref`, `in`, i `out` parametrów w języku C# nie można oznaczyć jako typ variant.  
  
 Istnieje również możliwość do obsługi wariancji i Kowariancja w tego samego obiektu delegowanego, ale także dla parametrów innego typu. Przedstawiono to w poniższym przykładzie.  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Tworzenie wystąpień i powoływanie delegatów ogólnych typu Variant  
 Można utworzyć wystąpienia i wywołać variant delegatów tak samo, jak wystąpienia i wywoływać niezmiennej delegatów. W poniższym przykładzie delegat jest utworzone przez wyrażenie lambda.  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>Łączenie Variant Delegaty ogólne  
 Nie należy łączyć variant delegatów. <xref:System.Delegate.Combine%2A> — Metoda nie obsługuje konwersji typu variant delegata i oczekuje delegatów być tego samego typu. Może to spowodować wyjątek czasu wykonywania podczas łączenia delegaty przy użyciu <xref:System.Delegate.Combine%2A> metody lub używając `+` operatora, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Wariancje w parametry typu ogólnego dla wartości i typy referencyjne  
 Wariancji dla parametrów typu ogólnego jest obsługiwana tylko dla typów odniesienia. Na przykład `DVariant<int>` nie można niejawnie przekonwertować `DVariant<Object>` lub `DVariant<long>`, ponieważ typ wartości jest liczbą całkowitą.  
  
 W poniższym przykładzie pokazano, że wariancji typu ogólnego parametrów nie jest obsługiwany dla typów wartości.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Typy ogólne](~/docs/standard/generics/index.md)  
 [Korzystanie z wariancji dla Func i akcji Delegaty ogólne (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)  
 [Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji)](../../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
