---
title: Tworzenie interfejsów ogólnych typu Variant (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 882bd0aa4497a99b2cf80e96f13f433ae74aad59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323742"
---
# <a name="creating-variant-generic-interfaces-c"></a>Tworzenie interfejsów ogólnych typu Variant (C#)
Można zadeklarować parametry typu ogólnego w interfejsach jako kowariantnego lub kontrawariantnego. *Kowariancja* umożliwia metod interfejsu do bardziej pochodnego zwracanych typów niż określone przez parametry typu ogólnego. *Kontrawariancja* umożliwia metod interfejsu do typy argumentu są mniej pochodnego od określonej przez parametry ogólne. Ogólny interfejs, który ma kowariantnego lub kontrawariantnego parametry typu ogólnego jest nazywany *variant*.  
  
> [!NOTE]
>  .NET framework 4 wprowadzono obsługę wariancji w kilku interfejsach istniejących. Aby uzyskać listę interfejsów typu variant w programie .NET Framework, zobacz [wariancje w interfejsach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="declaring-variant-generic-interfaces"></a>Deklarujący interfejsów ogólnych typu Variant  
 Interfejsów ogólnych typu variant można zadeklarować przy użyciu `in` i `out` słowa kluczowe dla parametrów typu ogólnego.  
  
> [!IMPORTANT]
>  `ref`, `in`, i `out` parametrów w języku C# nie może być wariantem. Typy wartości nie obsługują również wariancji.  
  
 Można zadeklarować parametru typu ogólnego kowariantnego przy użyciu `out` — słowo kluczowe. Kowariantnego typu muszą spełniać następujące warunki:  
  
-   Typ jest używany tylko jako typ zwracany metody interfejsu i nie jest używany jako typ argumentów metody. Jest to zilustrowane w poniższym przykładzie, w którym typ `R` zadeklarowano kowariantny.  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        R GetSomething();  
        // The following statement generates a compiler error.  
        // void SetSometing(R sampleArg);  
  
    }  
    ```  
  
     Istnieje jeden wyjątek od tej reguły. Jeśli masz to delegat generyczny kontrawariantnego jako parametr metody dla obiekt delegowany mogą używać typu co parametr typu ogólnego. Jest to zilustrowane przez typ `R` w poniższym przykładzie. Aby uzyskać więcej informacji, zobacz [wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [wariancji Func i akcji Delegaty ogólne (C#) przy użyciu](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        void DoSomething(Action<R> callback);  
    }  
    ```  
  
-   Typ nie jest używany jako ogólne ograniczenia dla metod interfejsu. Jest to zilustrowane w poniższym kodzie.  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        // The following statement generates a compiler error  
        // because you can use only contravariant or invariant types  
        // in generic contstraints.  
        // void DoSomething<T>() where T : R;  
    }  
    ```  
  
 Można zadeklarować kontrawariantnego parametru typu ogólnego przy użyciu `in` — słowo kluczowe. Typ kontrawariantnego może służyć jedynie jako typ argumenty metody, a nie typu zwracanego metody interfejsu. Można także kontrawariantnego typu dla ograniczenia ogólne. Poniższy kod przedstawia sposób zadeklarować interfejsu kontrawariantnego i użyć ogólne ograniczenia dla jednej z metod.  
  
```csharp  
interface IContravariant<in A>  
{  
    void SetSomething(A sampleArg);  
    void DoSomething<T>() where T : A;  
    // The following statement generates a compiler error.  
    // A GetSomething();              
}  
```  
  
 Istnieje również możliwość obsługuje zarówno Kowariancja i kontrawariancja w ten sam interfejs, ale dla różnych typów parametrów, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
interface IVariant<out R, in A>  
{  
    R GetSomething();  
    void SetSomething(A sampleArg);  
    R GetSetSometings(A sampleArg);  
}  
```  
  
## <a name="implementing-variant-generic-interfaces"></a>Implementującej interfejsów ogólnych typu Variant  
 Zaimplementowanie interfejsów ogólnych typu variant w klasach przy użyciu składni, która jest używana dla niezmiennej interfejsów. Poniższy przykład kodu pokazuje, jak do zaimplementowania w klasie rodzajowej kowariantnego interfejsu.  
  
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
  
 Klasy, które implementują interfejsów typu variant są niezmienne. Rozważmy na przykład następujący kod.  
  
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
 Podczas rozszerzania typu variant interfejs ogólny, należy użyć `in` i `out` słów kluczowych, aby jawnie określić, czy interfejsu pochodnego obsługuje wariancji. Kompilator wariancję z interfejsu, który zostanie rozszerzone nie są rozpoznawane. Na przykład należy wziąć pod uwagę następujące interfejsy.  
  
```csharp  
interface ICovariant<out T> { }  
interface IInvariant<T> : ICovariant<T> { }  
interface IExtCovariant<out T> : ICovariant<T> { }  
```  
  
 W `IInvariant<T>` interfejsu, parametru typu ogólnego `T` jest niezmienne, natomiast w `IExtCovariant<out T>` parametr typu jest kowariantny, mimo że oba interfejsy rozszerzenia tego samego interfejsu. Ta zasada dotyczy kontrawariantnego parametry typu ogólnego.  
  
 Można utworzyć interfejs, który rozszerza interfejs gdzie parametr typu ogólnego `T` jest kowariantny i interfejsu, w której jest kontrawariantny Jeśli rozszerzenie interfejsu parametr typu ogólnego `T` jest niezmienne. Jest to zilustrowane w poniższym przykładzie kodu.  
  
```csharp  
interface ICovariant<out T> { }  
interface IContravariant<in T> { }  
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }  
```  
  
 Jednak jeśli parametr typu ogólnego `T` jest zadeklarowana kowariantnego w jeden interfejs, nie można zadeklarować go kontrawariantnego w interfejsie rozszerzanie lub na odwrót. Jest to zilustrowane w poniższym przykładzie kodu.  
  
```csharp  
interface ICovariant<out T> { }  
// The following statement generates a compiler error.  
// interface ICoContraVariant<in T> : ICovariant<T> { }  
```  
  
### <a name="avoiding-ambiguity"></a>Unikanie niejednoznaczności  
 Podczas implementowania interfejsów ogólnych typu variant wariancję czasami może prowadzić do niejednoznaczności. Należy unikać to.  
  
 Na przykład jawnie w przypadku zastosowania tego samego typu variant interfejsu ogólne z parametrami innego typu ogólnego w jedną klasę, można utworzyć niejednoznaczności. Kompilator nie tworzy w tym przypadku błąd, ale nie określono implementacji interfejsu, który zostanie wybrany w czasie wykonywania. Może to prowadzić do subtelnych błędów w kodzie. Rozważmy poniższy przykład kodu.  
  
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
  
 W tym przykładzie jest nieokreślony sposób `pets.GetEnumerator` metody wybierze między `Cat` i `Dog`. Może to spowodować problemy w kodzie.  
  
## <a name="see-also"></a>Zobacz też  
 [Wariancje w interfejsach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [Korzystanie z wariancji dla Func i akcji Delegaty ogólne (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
