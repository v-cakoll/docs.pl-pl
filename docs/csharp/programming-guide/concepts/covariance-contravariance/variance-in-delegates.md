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
# <a name="variance-in-delegates-c"></a>Wariancja w delegatach (C#)
.NET Framework 3.5 wprowadzono obsługę wariancji dla podpisów metod dopasowywania z typami delegatów we wszystkich delegatach w języku C#. Oznacza to, że można przypisać do delegatów nie tylko metody, które mają pasujące podpisy, ale także metody, które zwracają więcej typów pochodnych (kowariancja) lub które akceptują parametry, które mają mniej pochodnych typów (contravariance) niż określone przez typ delegata . Obejmuje to zarówno delegatów ogólnych i nieogólnych.  
  
 Rozważmy na przykład następujący kod, który ma dwie klasy i dwie delegatów: ogólny i nierodzajowy.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 Podczas tworzenia delegatów `SampleDelegate` `SampleGenericDelegate<A, R>` lub typów, można przypisać jedną z następujących metod do tych delegatów.  
  
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
  
 Poniższy przykład kodu ilustruje niejawną konwersję między podpisem metody a typem delegata.  
  
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
  
 Aby uzyskać więcej przykładów, zobacz [Używanie wariancji w delegatach (C#)](./using-variance-in-delegates.md) i [używanie wariancji dla delegatów ogólnych akcji i akcji (C#).](./using-variance-for-func-and-action-generic-delegates.md)  
  
## <a name="variance-in-generic-type-parameters"></a>Wariancja w parametrach typu ogólnego  
 W .NET Framework 4 lub nowszej można włączyć niejawną konwersję między delegatami, dzięki czemu delegaci ogólni, którzy mają różne typy określone przez parametry typu ogólnego, mogą być przypisane do siebie, jeśli typy są dziedziczone od siebie zgodnie z wymaganiami Wariancji.  
  
 Aby włączyć konwersję niejawną, należy jawnie zadeklarować parametry ogólne w pełnomocnika jako kowariantylub kontrawariantny przy użyciu słowa kluczowego `in` lub. `out`  
  
 W poniższym przykładzie kodu pokazano, jak można utworzyć pełnomocnika, który ma kowariantyczny parametr typu ogólnego.  
  
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
  
 Jeśli używasz tylko obsługi wariancji, aby dopasować podpisy metody `in` do `out` typów delegatów i nie używać słów kluczowych i, może się okazać, że czasami można utworzyć wystąpienia delegatów z identycznych wyrażeń lambda lub metod, ale nie można przypisać jednego pełnomocnika do innego.  
  
 W poniższym przykładzie `SampleGenericDelegate<String>` kodu nie można `SampleGenericDelegate<Object>`jawnie `String` przekonwertować na , chociaż dziedziczy `Object`. Ten problem można rozwiązać, oznaczając `T` `out` parametr ogólny słowem kluczowym.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Delegaci ogólni, którzy mają parametry typu wariantu w ramach .NET Framework  
 .NET Framework 4 wprowadził obsługę wariancji dla parametrów typu ogólnego w kilku istniejących delegatów ogólnych:  
  
- `Action`delegatów <xref:System> z obszaru nazw, <xref:System.Action%601> na przykład, i<xref:System.Action%602>  
  
- `Func`delegatów <xref:System> z obszaru nazw, <xref:System.Func%601> na przykład, i<xref:System.Func%602>  
  
- Pełnomocnik <xref:System.Predicate%601>  
  
- Pełnomocnik <xref:System.Comparison%601>  
  
- Pełnomocnik <xref:System.Converter%602>  
  
 Aby uzyskać więcej informacji i przykładów, zobacz [Korzystanie z wariancji dla Func i akcji ogólnych delegatów (C#)](./using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarowanie parametrów typu wariantu w pełnomocnikach ogólnych  
 Jeśli delegat rodzajowy ma kowariantne lub przeciwwariantne parametry typu ogólnego, może być określany jako *wariant delegata ogólnego*.  
  
 Można zadeklarować covariant parametr urodzajny parametr u `out` rodzajowy delegata przy użyciu słowa kluczowego. Typ kowariantywny może służyć tylko jako typ zwracany metody, a nie jako typ argumentów metody. W poniższym przykładzie kodu pokazano, jak zadeklarować współwariantowego delegata ogólnego.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 Można zadeklarować kontrawarianty parametru typu ogólnego w `in` delegacie rodzajowym za pomocą słowa kluczowego. Typ przeciwwariantny może służyć tylko jako typ argumentów metody, a nie jako typ zwracany metody. W poniższym przykładzie kodu pokazano, jak zadeklarować kontrataki delegata ogólnego.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> `ref`, `in`a `out` parametry w języku C# nie mogą być oznaczone jako wariant.  
  
 Możliwe jest również obsługa wariancji i kowariancji w tym samym delegata, ale dla różnych parametrów typu. Jest to pokazane w poniższym przykładzie.  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Tworzenie wystąpienia i wywoływanie delegatów ogólnych wariantów  
 Można utworzyć wystąpienia i wywołać delegatów warianttak jak wystąpienia i wywołać delegatów niezmienne. W poniższym przykładzie delegat akcjonorpii jest tworzone przez wyrażenie lambda.  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>Łączenie delegatów ogólnych wariantów  
 Nie należy łączyć delegatów wariantu. Metoda <xref:System.Delegate.Combine%2A> nie obsługuje konwersji delegata wariantu i oczekuje delegatów, które mają być dokładnie tego samego typu. Może to prowadzić do wyjątku w czasie wykonywania <xref:System.Delegate.Combine%2A> podczas łączenia `+` delegatów za pomocą metody lub za pomocą operatora, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Wariancja w parametrach typu ogólnego dla typów wartości i odwołań  
 Odchylenie dla parametrów typu ogólnego jest obsługiwane tylko dla typów referencyjnych. Na przykład `DVariant<int>` nie można niejawnie `DVariant<Object>` przekonwertować na lub `DVariant<long>`, ponieważ liczba całkowita jest typem wartości.  
  
 W poniższym przykładzie pokazano, że wariancja w parametrach typu ogólnego nie jest obsługiwana dla typów wartości.  
  
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

- [Typy ogólne](../../../../standard/generics/index.md)
- [Używanie wariancji dla delegatów ogólnych akcji i akcji (C#)](./using-variance-for-func-and-action-generic-delegates.md)
- [Jak połączyć delegatów (delegatów multiemisji)](../../delegates/how-to-combine-delegates-multicast-delegates.md)
