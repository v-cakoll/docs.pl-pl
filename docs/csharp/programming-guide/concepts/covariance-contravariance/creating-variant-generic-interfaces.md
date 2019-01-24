---
title: Tworzenie interfejsów typu Variant (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 5ae3b309282712e3441b53ea4cfc316be3ca92d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614683"
---
# <a name="creating-variant-generic-interfaces-c"></a>Tworzenie interfejsów typu Variant (C#)
Możesz deklarować parametry typu ogólnego w interfejsach jako kowariantny lub kontrawariantny. *Kowariancja* umożliwia metod interfejsu do mają bardziej pochodne typy zwracane niż określone przez parametry typu ogólnego. *Kontrawariancja* umożliwia metod interfejsu mieć typy argumentów, które są mniej pochodnego niż określona przez parametry ogólne. Ogólny interfejs, który ma kowariantne i kontrawariantne parametry typu ogólnego jest nazywany *wariant*.  
  
> [!NOTE]
>  .NET framework 4 wprowadzono wariancji obsługę kilka istniejących interfejsów ogólnych. Aby uzyskać listę interfejsów typu variant w programie .NET Framework, zobacz [wariancje w interfejsach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="declaring-variant-generic-interfaces"></a>Deklarujący interfejsów ogólnych typu Variant  
 Można zadeklarować interfejsów ogólnych typu variant, za pomocą `in` i `out` słowa kluczowe dla parametrów typu genetycznego.  
  
> [!IMPORTANT]
>  `ref`, `in`, i `out` parametrów w języku C# nie może być typ variant. Typy wartości nie obsługują także wariancji.  
  
 Można zadeklarować parametru typu generycznego kowariantne przy użyciu `out` — słowo kluczowe. Kowariantnego typu musi spełniać następujące warunki:  
  
-   Typ jest używany tylko jako zwracany typ metody interfejsu i nie jest używany jako typ argumentów metody. Jest to zilustrowane w poniższym przykładzie, w którym typ `R` jest zadeklarowany jako kowariantny.  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        R GetSomething();  
        // The following statement generates a compiler error.  
        // void SetSometing(R sampleArg);  
  
    }  
    ```  
  
     Istnieje jeden wyjątek od tej reguły. Jeśli Delegat ogólny kontrawariantny, jako parametru metody, można użyć typu co parametr typu ogólnego, dla delegata. Jest to zilustrowane przez typ `R` w poniższym przykładzie. Aby uzyskać więcej informacji, zobacz [wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancji dla akcji delegatów ogólnych (C#) Func i](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        void DoSomething(Action<R> callback);  
    }  
    ```  
  
-   Typ nie jest używany jako ograniczenia typu ogólnego dla metod interfejsu. Jest to zilustrowane w poniższym kodzie.  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        // The following statement generates a compiler error  
        // because you can use only contravariant or invariant types  
        // in generic contstraints.  
        // void DoSomething<T>() where T : R;  
    }  
    ```  
  
 Można zadeklarować kontrawariantnego parametru typu ogólnego przy użyciu `in` — słowo kluczowe. Typ kontrawariantne może służyć jedynie jako typów argumentów metody, a nie typu zwracanego metody interfejsu. Można także kontrawariantnego typu dla ograniczenia ogólne. Poniższy kod przedstawia sposób deklarowania interfejsu kontrawariantnego i na użytek ograniczenie generyczne jednej z jego metod.  
  
```csharp  
interface IContravariant<in A>  
{  
    void SetSomething(A sampleArg);  
    void DoSomething<T>() where T : A;  
    // The following statement generates a compiler error.  
    // A GetSomething();              
}  
```  
  
 Istnieje również możliwość obsługuje zarówno kowariancji i kontrawariancji w ten sam interfejs, ale dla parametrów innego typu, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
interface IVariant<out R, in A>  
{  
    R GetSomething();  
    void SetSomething(A sampleArg);  
    R GetSetSometings(A sampleArg);  
}  
```  
  
## <a name="implementing-variant-generic-interfaces"></a>Implementowanie interfejsów ogólnych typu Variant  
 Możesz zaimplementować interfejsów ogólnych typu variant klas przy użyciu składni, która jest używana niezmienna interfejsów. Poniższy przykład kodu pokazuje sposób implementacji kowariantne interfejsu w klasie ogólnej.  
  
```csharp  
interface ICovariant<out R>  
{  
    R GetSomething();  
}  
class SampleImplementation<R> : ICovariant<R>  
{  
    public R GetSomething()  
    {  
        // Some code.  
        return default(R);  
    }  
}  
```  
  
 Klasy, które implementują interfejsów typu variant są niezmienne. Rozważmy na przykład, poniższy kod.  
  
```csharp  
// The interface is covariant.  
ICovariant<Button> ibutton = new SampleImplementation<Button>();  
ICovariant<Object> iobj = ibutton;  
  
// The class is invariant.  
SampleImplementation<Button> button = new SampleImplementation<Button>();  
// The following statement generates a compiler error  
// because classes are invariant.  
// SampleImplementation<Object> obj = button;  
```  
  
## <a name="extending-variant-generic-interfaces"></a>Rozszerzanie interfejsów ogólnych typu Variant  
 Podczas rozszerzania typu variant interfejs ogólny, trzeba użyć `in` i `out` słów kluczowych, aby jawnie określić, czy interfejsu pochodnego obsługuje wariancji. Kompilator nie są rozpoznawane przez odchylenie od interfejsu, który jest rozszerzany. Na przykład należy wziąć pod uwagę następujące interfejsy.  
  
```csharp  
interface ICovariant<out T> { }  
interface IInvariant<T> : ICovariant<T> { }  
interface IExtCovariant<out T> : ICovariant<T> { }  
```  
  
 W `IInvariant<T>` interfejsu, parametr typu ogólnego `T` jest niezmienny, natomiast w `IExtCovariant<out T>` parametr typu jest kowariantny, mimo że oba interfejsy rozszerzyć ten sam interfejs. Ta sama zasada dotyczy kontrawariantne parametry typu ogólnego.  
  
 Można utworzyć interfejsu, który rozszerza interfejs gdzie parametr typu ogólnego `T` jest kowariantny interfejs, w której jest kontrawariantny w rozszerzanie interfejsu parametr typu ogólnego i `T` jest niezmienny. Jest to zilustrowane w poniższym przykładzie kodu.  
  
```csharp  
interface ICovariant<out T> { }  
interface IContravariant<in T> { }  
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }  
```  
  
 Jednak jeśli parametr typu ogólnego `T` jest kowariantny zadeklarowana w ramach jednego interfejsu, nie można zadeklarować je kontrawariantnego w interfejsie rozszerzanie lub na odwrót. Jest to zilustrowane w poniższym przykładzie kodu.  
  
```csharp  
interface ICovariant<out T> { }  
// The following statement generates a compiler error.  
// interface ICoContraVariant<in T> : ICovariant<T> { }  
```  
  
### <a name="avoiding-ambiguity"></a>Unikanie niejednoznaczności  
 Podczas implementowania interfejsów ogólnych typu variant wariancji czasami może prowadzić do niejednoznaczności. Należy ich unikać.  
  
 Na przykład w przypadku zastosowania jawnie tego samego typu variant ogólny interfejs z parametrami typu rodzajowego różnych w jednej klasie, można utworzyć niejednoznaczności. Kompilator generuje błąd w takiej sytuacji, ale nie zostanie określony, zostanie wybrany co do implementacji interfejsu w czasie wykonywania. Może to prowadzić do subtelnych błędów w kodzie. Rozważmy następujący przykład kodu.  
  
```csharp  
// Simple class hierarchy.  
class Animal { }  
class Cat : Animal { }  
class Dog : Animal { }  
  
// This class introduces ambiguity  
// because IEnumerable<out T> is covariant.  
class Pets : IEnumerable<Cat>, IEnumerable<Dog>  
{  
    IEnumerator<Cat> IEnumerable<Cat>.GetEnumerator()  
    {  
        Console.WriteLine("Cat");  
        // Some code.  
        return null;  
    }  
  
    IEnumerator IEnumerable.GetEnumerator()  
    {  
        // Some code.  
        return null;  
    }  
  
    IEnumerator<Dog> IEnumerable<Dog>.GetEnumerator()  
    {  
        Console.WriteLine("Dog");  
        // Some code.  
        return null;  
    }  
}  
class Program  
{  
    public static void Test()  
    {  
        IEnumerable<Animal> pets = new Pets();  
        pets.GetEnumerator();  
    }  
}  
```  
  
 W tym przykładzie jest nieokreślona sposób, w jaki `pets.GetEnumerator` metoda wybiera między `Cat` i `Dog`. Może to spowodować problemy w kodzie.  
  
## <a name="see-also"></a>Zobacz także

- [Wariancje w interfejsach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Korzystanie z wariancji dla Func i akcji delegatów ogólnych (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
