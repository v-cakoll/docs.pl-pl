---
title: Wariancja w delegatach (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 0a77c4abe8f2540e4b3b33d2cf99a20c3c2fa942
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659939"
---
# <a name="variance-in-delegates-c"></a>Wariancja w delegatach (C#)
.NET Framework 3,5 wprowadzono obsługę wariancji dla pasujących sygnatur metod z typami delegatów we C#wszystkich delegatach w. Oznacza to, że można przypisać do delegatów nie tylko metod, które mają pasujące podpisy, ale również metody, które zwracają więcej typów pochodnych (Kowariancja) lub akceptują parametry, które mają mniej pochodne typy (kontrawariancja) niż określone przez typ delegata . Dotyczy to zarówno delegatów rodzajowych, jak i nieogólnych.  
  
 Rozważmy na przykład poniższy kod, który ma dwie klasy i dwa Delegaty: generyczne i nieogólne.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 Podczas tworzenia delegatów `SampleDelegate` lub `SampleGenericDelegate<A, R>` typów można przypisać do tych delegatów jedną z następujących metod.  
  
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
  
 Poniższy przykład kodu ilustruje niejawną konwersję między sygnaturą metody a typem delegata.  
  
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
  
 Aby uzyskać więcej przykładów, zobacz [Korzystanie z wariancjiC#w delegatach ()](./using-variance-in-delegates.md) i [Używanie wariancji dla delegatów funkcji Func i ActionC#()](./using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Wariancja w parametrach typu ogólnego  
 W .NET Framework 4 lub nowszej można włączyć niejawną konwersję między delegatami, tak aby generyczne Delegaty mające różne typy określone przez parametry typu generycznego można przypisać do siebie nawzajem, jeśli typy są dziedziczone od siebie, zgodnie z wymaganiami względem.  
  
 Aby włączyć niejawną konwersję, należy jawnie zadeklarować parametry ogólne w delegatze jako współvariant lub kontrawariantne `in` za `out` pomocą słowa kluczowego or.  
  
 Poniższy przykład kodu pokazuje, jak można utworzyć delegata, który ma parametr typu ogólnego.  
  
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
  
 Jeśli używasz tylko wariancji do dopasowania sygnatur metod z typami delegatów i nie używaj `in` słów kluczowych i `out` , może się okazać, że czasami można utworzyć wystąpienia delegatów z identycznymi wyrażeniami lub metodami lambda, ale nie można Przypisz jednego delegata do innego.  
  
 W poniższym przykładzie `SampleGenericDelegate<String>` kodu nie można jawnie przekonwertować na `SampleGenericDelegate<Object>`, chociaż `String` dziedziczy `Object`. Ten problem można rozwiązać przez oznaczenie parametru `T` `out` generycznego słowem kluczowym.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Delegaty ogólne, które mają parametry typu Variant w .NET Framework  
 .NET Framework 4 wprowadził obsługę wariancji dla parametrów typu ogólnego w kilku istniejących delegatach ogólnych:  
  
- `Action`deleguje z <xref:System> przestrzeni nazw, na przykład, <xref:System.Action%601> i<xref:System.Action%602>  
  
- `Func`deleguje z <xref:System> przestrzeni nazw, na przykład, <xref:System.Func%601> i<xref:System.Func%602>  
  
- <xref:System.Predicate%601> Obiekt delegowany  
  
- <xref:System.Comparison%601> Obiekt delegowany  
  
- <xref:System.Converter%602> Obiekt delegowany  
  
 Aby uzyskać więcej informacji i przykładów, zobacz [Używanie wariancji dla delegatów ()C#funkcji Func i Action ()](./using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarowanie parametrów typu Variant w delegatach generycznych  
 Jeśli delegat generyczny ma parametry typu generycznego lub kontrawariantne, może być określany jako *Delegat generyczny elementu Variant*.  
  
 Za pomocą `out` słowa kluczowego można zadeklarować współwariant parametru typu ogólnego w delegatze ogólnym. Typ współwariantu może być używany tylko jako zwracany typ metody, a nie jako typ argumentów metody. Poniższy przykład kodu pokazuje, jak zadeklarować delegata generycznego.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 Parametr typu ogólnego kontrawariantne można zadeklarować w delegatze ogólnym za pomocą `in` słowa kluczowego. Typ kontrawariantne może być używany tylko jako typ argumentów metody, a nie jako zwracany typ metody. Poniższy przykład kodu pokazuje, jak zadeklarować delegata generycznego kontrawariantne.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  `ref`, `in`, i `out` parametry w C# nie mogą być oznaczone jako VARIANT.  
  
 Istnieje również możliwość obsługi zarówno wariancji, jak i kowariancji w tym samym delegatze, ale dla różnych parametrów typu. Pokazano to w poniższym przykładzie.  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Tworzenie wystąpień i wywoływanie delegatów ogólnych typu Variant  
 Można tworzyć wystąpienia delegatów wariantów i wywoływać je tak samo jak w przypadku wystąpienia i wywoływać delegatów niezmiennej. W poniższym przykładzie obiekt delegowany jest tworzone przez wyrażenie lambda.  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>Łączenie delegatów ogólnych typu Variant  
 Nie należy łączyć delegatów wariantów. <xref:System.Delegate.Combine%2A> Metoda nie obsługuje konwersji delegata typu Variant i oczekuje, że Delegaty mają być dokładnie tego samego typu. Może to prowadzić do wyjątku czasu wykonywania podczas łączenia delegatów za pomocą <xref:System.Delegate.Combine%2A> metody lub przy `+` użyciu operatora, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Wariancja w parametrach typu ogólnego dla typów wartości i odwołań  
 WARIANCJA dla parametrów typu ogólnego jest obsługiwana tylko w przypadku typów referencyjnych. Na przykład `DVariant<int>` nie można konwertować niejawnie na `DVariant<Object>` lub `DVariant<long>`, ponieważ liczba całkowita jest typem wartości.  
  
 W poniższym przykładzie pokazano, że Wariancja w parametrach typu ogólnego nie jest obsługiwana w przypadku typów wartości.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Typy ogólne](../../../../standard/generics/index.md)
- [Korzystanie z wariancji dla delegatów dla funkcjiC#Func i Action ()](./using-variance-for-func-and-action-generic-delegates.md)
- [Instrukcje: Łączenie delegatów (delegatów multiemisji)](../../delegates/how-to-combine-delegates-multicast-delegates.md)
