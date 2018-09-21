---
title: Wariancje w Delegatach (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 3dabac4e532198871cf05d639aa692751ab17ae1
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540888"
---
# <a name="variance-in-delegates-c"></a>Wariancje w Delegatach (C#)
.NET framework 3.5 wprowadzono obsługę wariancji podpisów metod dopasowania z typów obiektów delegowanych w wszystkie obiekty delegowane w języku C#. Oznacza to, że można przypisać do deleguje nie tylko metody, które pasują do sygnatur, ale także metody, które zwracają więcej pochodne typy (korelacja) lub które przyjmują parametry, które mają mniej pochodne typy (kontrawariancja) niż określona przez typ delegata . Dotyczy to również delegatów ogólnych i nieogólnych.  
  
 Na przykład rozważmy następujący kod, który ma dwie klasy i dwa delegaty: ogólnych i nieogólnych.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 Po utworzeniu delegatów `SampleDelegate` lub `SampleGenericDelegate<A, R>` typów, w jednej z następujących metod można przypisać do tych obiektów delegowanych.  
  
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
  
 Poniższy przykład kodu ilustruje niejawna konwersja między podpis metody i typu delegata.  
  
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
  
 Aby uzyskać więcej przykładów, zobacz [przy użyciu wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) i [przy użyciu wariancji dla akcji delegatów ogólnych (C#) Func i](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Wariancji w parametrach typu ogólnego  
 W programie .NET Framework 4 lub nowszym można włączyć niejawna konwersja między elementem delegatów, dzięki czemu delegatów ogólnych, które mają różne typy określona przez parametry typu ogólnego mogą być przypisane do siebie nawzajem, jeśli typy są dziedziczone od siebie nawzajem, zgodnie z wymaganiami WARIANCJA.  
  
 Aby włączyć niejawną konwersję, musisz jawnie deklarować parametrów ogólnych w delegatów jako kowariantnych lub kontrawariantnych przy użyciu `in` lub `out` — słowo kluczowe.  
  
 Poniższy przykład kodu pokazuje, jak utworzyć obiekt delegowany mający parametr kowariantnego typu ogólnego.  
  
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
  
 Jeśli używasz obsługują tylko odchylenia do dopasowania podpisy metod ze typy delegatów i nie używaj `in` i `out` słów kluczowych, może się okazać, że czasami można utworzyć wystąpienie obiektów delegowanych z wyrażenia lambda identyczne lub metody, ale nie jest możliwe Przypisz jednego delegata do innego.  
  
 W poniższym przykładzie kodu `SampleGenericDelegate<String>` nie może być jawnie konwertowane na `SampleGenericDelegate<Object>`, mimo że `String` dziedziczy `Object`. Możesz rozwiązać ten problem, oznaczając parametru ogólnego `T` z `out` — słowo kluczowe.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>Parametry typu delegatów ogólnych, które mają typ Variant w .NET Framework  
 .NET framework 4 wprowadzono obsługę wariancji dla parametrów typu rodzajowego w kilku istniejących delegatów ogólnych:  
  
-   `Action` delegaty z <xref:System> przestrzeni nazw, na przykład <xref:System.Action%601> i <xref:System.Action%602>  
  
-   `Func` delegaty z <xref:System> przestrzeni nazw, na przykład <xref:System.Func%601> i <xref:System.Func%602>  
  
-   <xref:System.Predicate%601> Delegowanie  
  
-   <xref:System.Comparison%601> Delegowanie  
  
-   <xref:System.Converter%602> Delegowanie  
  
 Aby uzyskać więcej informacji i przykładów, zobacz [przy użyciu wariancji dla akcji delegatów ogólnych (C#) Func i](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Deklarowanie Wariantne parametry typu w delegatów ogólnych  
 Jeśli delegata ogólnego ma kowariantne i kontrawariantne parametry typu ogólnego, jego mogą być określane jako *variant Delegat ogólny*.  
  
 Można zadeklarować parametru typu generycznego kowariantne Delegat ogólny przy użyciu `out` — słowo kluczowe. Kowariantnego typu może służyć jedynie jako typ zwracany metody, a nie typu argumentów metody. Poniższy przykład kodu pokazuje sposób deklarowania kowariantne Delegat ogólny.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 Kontrawariantnego parametru typu ogólnego, Delegat ogólny może zadeklarować za pomocą `in` — słowo kluczowe. Typ kontrawariantne może służyć jedynie jako typów argumentów metody, a nie typem zwracanym metody. Poniższy przykład kodu pokazuje sposób deklarowania to delegat generyczny kontrawariantny.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  `ref`, `in`, i `out` parametrów w języku C# nie można oznaczyć jako wariant.  
  
 Istnieje również możliwość obsługi kowariancji i Wariancja w tym samym delegatów, ale w przypadku różnych typów parametrów. Jest to pokazane w poniższym przykładzie.  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Utworzenie wystąpienia i wywoływania wariantów ogólnych delegatów  
 Można utworzyć wystąpienia i wywoływać delegatów typu variant, tak samo, jak utworzyć wystąpienia i wywoływać delegatów niezmiennej. W poniższym przykładzie delegat jest tworzone przez wyrażenie lambda.  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>Łączenie delegatów ogólnych typu Variant  
 Nie należy łączyć wariantu delegatów. <xref:System.Delegate.Combine%2A> Metoda nie obsługuje konwersji typu variant delegata i oczekuje, że delegaty dokładnie tego samego typu. Może to prowadzić do wyjątku czasu wykonywania, podczas łączenia przy użyciu delegatów <xref:System.Delegate.Combine%2A> metody lub używając `+` operatora, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Wariancji w parametrach typu ogólnego dla wartości i typy odwołań  
 Wariancja dla parametrów typu ogólnego jest obsługiwana tylko dla typów odwołania. Na przykład `DVariant<int>` nie może być niejawnie konwertowane na `DVariant<Object>` lub `DVariant<long>`, ponieważ liczba całkowita jest typem wartości.  
  
 W poniższym przykładzie pokazano tej wariancji w typie ogólnym parametrów nie jest obsługiwana dla typów wartości.  
  
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

- [Typy ogólne](~/docs/standard/generics/index.md)  
- [Korzystanie z wariancji dla Func i akcji delegatów ogólnych (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)  
- [Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji)](../../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
