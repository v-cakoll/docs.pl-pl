---
title: Tworzenie wariantowych interfejsów ogólnych (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 4ba72f28cd2ddd800f169387cc2c742159d4cb1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595310"
---
# <a name="creating-variant-generic-interfaces-c"></a>Tworzenie wariantowych interfejsów ogólnych (C#)

Można zadeklarować ogólne parametry typu w interfejsach jako kowariantne lub kontrawariantne. *Kowariancja* umożliwia metody interfejsu mają więcej pochodnych typów zwracanych niż zdefiniowane przez parametry typu ogólnego. *Contravariance* umożliwia metody interfejsu mają typy argumentów, które są mniej pochodne niż określone przez parametry ogólne. Ogólny interfejs, który ma kowariantne lub kontrawariantne parametry typu ogólnego, jest nazywany *wariantem*.

> [!NOTE]
> .NET Framework 4 wprowadzono obsługę wariancji dla kilku istniejących interfejsów ogólnych. Aby uzyskać listę interfejsów wariantów w platformie .NET Framework, zobacz [Wariancja w interfejsach ogólnych (C#).](./variance-in-generic-interfaces.md)

## <a name="declaring-variant-generic-interfaces"></a>Deklarowanie wariantowych interfejsów ogólnych

Można zadeklarować wariant ogólnych `in` interfejsów przy użyciu i `out` słów kluczowych dla parametrów typu ogólnego.

> [!IMPORTANT]
> `ref`, `in`a `out` parametry w języku C# nie mogą być wariantowe. Typy wartości również nie obsługują wariancji.

Można zadeklarować covariant parametru typu `out` ogólnego przy użyciu słowa kluczowego. Typ kowariantny musi spełniać następujące warunki:

- Typ jest używany tylko jako zwracany typ metod interfejsu i nie jest używany jako typ argumentów metody. Jest to zilustrowane w poniższym przykładzie, w którym typ `R` jest zadeklarowany covariant.

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    Istnieje jeden wyjątek od tej reguły. Jeśli jako parametr metody masz kontrataki ogólny, możesz użyć tego typu jako parametru typu ogólnego dla pełnomocnika. Jest to zilustrowane `R` przez typ w poniższym przykładzie. Aby uzyskać więcej informacji, zobacz [Wariancja w delegatach (C#)](./variance-in-delegates.md) i [Korzystanie z wariancji dla func i akcji ogólnych delegatów (C#)](./using-variance-for-func-and-action-generic-delegates.md).

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- Typ nie jest używany jako ogólne ograniczenie dla metod interfejsu. Jest to zilustrowane w poniższym kodzie.

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

Można zadeklarować kontrawarianty parametru typu `in` ogólnego za pomocą słowa kluczowego. Typ kontrawariantny może służyć tylko jako typ argumentów metody, a nie jako zwracany typ metod interfejsu. Typ kontrawariantny może być również używany dla ograniczeń ogólnych. Poniższy kod pokazuje, jak zadeklarować interfejs kontrawariantny i użyć ograniczenia ogólnego dla jednej z jego metod.

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

Możliwe jest również obsługa zarówno kowariancji, jak i kontrawaracji w tym samym interfejsie, ale dla różnych parametrów typu, jak pokazano w poniższym przykładzie kodu.

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a>Implementowanie wariantowych interfejsów ogólnych

Implementowanie wariantu interfejsów ogólnych w klasach przy użyciu tej samej składni, która jest używana dla interfejsów niezmiennych. W poniższym przykładzie kodu pokazano, jak zaimplementować interfejs kowariantny w klasie ogólnej.

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

Klasy implementują interfejsy wariantowe są niezmienne. Rozważmy na przykład następujący kod.

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

## <a name="extending-variant-generic-interfaces"></a>Rozszerzanie wariantowych interfejsów ogólnych

Po rozszerzeniu wariantu ogólny interfejs, `in` należy `out` użyć i słowa kluczowe jawnie określić, czy interfejs pochodny obsługuje wariancji. Kompilator nie wywnioskować wariancji z interfejsu, który jest rozszerzony. Rozważmy na przykład następujące interfejsy.

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

W `IInvariant<T>` interfejsie parametr `T` typu ogólnego jest niezmienny, podczas gdy w `IExtCovariant<out T>` parametrze typu jest kowariantny, chociaż oba interfejsy rozszerzają ten sam interfejs. Ta sama reguła jest stosowana do przeciwwariantnych parametrów typu ogólnego.

Można utworzyć interfejs, który rozszerza zarówno interfejs, `T` w którym parametr typu ogólnego jest kowariantny, jak i `T` interfejs, w którym jest kontrawariantny, jeśli w interfejsie rozszerzającym parametr typu ogólnego jest niezmienny. Jest to zilustrowane w poniższym przykładzie kodu.

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

Jednak jeśli parametr `T` typu ogólnego jest zadeklarowany covariant w jednym interfejsie, nie można zadeklarować, że jest to kontrawarianty w interfejsie rozszerzającym lub odwrotnie. Jest to zilustrowane w poniższym przykładzie kodu.

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a>Unikanie niejednoznaczności

Podczas implementowania wariantu interfejsów ogólnych wariancja może czasami prowadzić do niejednoznaczności. Należy tego unikać.

Na przykład jeśli jawnie zaimplementujesz ten sam wariant ogólny interfejs z różnymi parametrami typu ogólnego w jednej klasie, można utworzyć niejednoznaczności. Kompilator nie generuje błąd w tym przypadku, ale nie określono, która implementacja interfejsu zostanie wybrana w czasie wykonywania. Może to prowadzić do subtelnych błędów w kodzie. Spójrz na poniższy przykład kodu.

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

W tym przykładzie nie określono, `pets.GetEnumerator` w jaki `Cat` sposób `Dog`metoda wybiera między i . Może to spowodować problemy w kodzie.

## <a name="see-also"></a>Zobacz też

- [Wariancja w interfejsach ogólnych (C#)](./variance-in-generic-interfaces.md)
- [Używanie wariancji dla delegatów ogólnych akcji i akcji (C#)](./using-variance-for-func-and-action-generic-delegates.md)
