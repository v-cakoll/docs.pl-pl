---
title: Wariancja w interfejsachC#ogólnych ()
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 12a8b58983256be0ca2b56ea6ed09e724e0814c8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595164"
---
# <a name="variance-in-generic-interfaces-c"></a>Wariancja w interfejsachC#ogólnych ()

.NET Framework 4 wprowadziła obsługę wariancji dla kilku istniejących interfejsów ogólnych. Obsługa wariancji umożliwia niejawną konwersję klas implementujących te interfejsy. 

Gwiazdki z .NET Framework 4, następujące interfejsy są wariantem:

- <xref:System.Collections.Generic.IEnumerable%601>(T jest współwariantem)

- <xref:System.Collections.Generic.IEnumerator%601>(T jest współwariantem)

- <xref:System.Linq.IQueryable%601>(T jest współwariantem)

- <xref:System.Linq.IGrouping%602>(`TKey` i`TElement` są współwariantowe)

- <xref:System.Collections.Generic.IComparer%601>(T jest kontrawariantne)

- <xref:System.Collections.Generic.IEqualityComparer%601>(T jest kontrawariantne)

- <xref:System.IComparable%601>(T jest kontrawariantne)

Począwszy od .NET Framework 4,5, następujące interfejsy są wariantem:

- <xref:System.Collections.Generic.IReadOnlyList%601>(T jest współwariantem)

- <xref:System.Collections.Generic.IReadOnlyCollection%601>(T jest współwariantem)

Kowariancja zezwala metodzie na bardziej pochodny typ zwracany niż zdefiniowany przez parametr typu ogólnego interfejsu. Aby zilustrować funkcję kowariancji, należy wziąć pod uwagę następujące interfejsy ogólne `IEnumerable<Object>` : `IEnumerable<String>`i. `IEnumerable<String>` Interfejs nie`IEnumerable<Object>` dziedziczy interfejsu. `String` Jednak Typ`Object` dziedziczy typ, a w niektórych przypadkach może być konieczne przypisanie obiektów do tych interfejsów. Jest to pokazane w poniższym przykładzie kodu.

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

We wcześniejszych wersjach .NET Framework ten kod powoduje błąd kompilacji w C# i, jeśli `Option Strict` znajduje się w Visual Basic. Ale teraz można użyć `strings` `objects`zamiast, jak pokazano w <xref:System.Collections.Generic.IEnumerable%601> poprzednim przykładzie, ponieważ interfejs jest współwariantem.

Kontrawariancja umożliwia metodzie posiadanie typów argumentów, które są mniej pochodne niż określone przez parametr generyczny interfejsu. Aby zilustrować kontrawariancja, założono, że utworzono `BaseComparer` klasę, aby porównać wystąpienia `BaseClass` klasy. `BaseComparer` Klasa`IEqualityComparer<BaseClass>` implementuje interfejs. Ponieważ interfejs jest teraz kontrawariantne, można go użyć `BaseComparer` do porównania wystąpień klas, które dziedziczą `BaseClass` klasę. <xref:System.Collections.Generic.IEqualityComparer%601> Jest to pokazane w poniższym przykładzie kodu.

```csharp
// Simple hierarchy of classes.
class BaseClass { }
class DerivedClass : BaseClass { }

// Comparer class.
class BaseComparer : IEqualityComparer<BaseClass>
{
    public int GetHashCode(BaseClass baseInstance)
    {
        return baseInstance.GetHashCode();
    }
    public bool Equals(BaseClass x, BaseClass y)
    {
        return x == y;
    }
}
class Program
{
    static void Test()
    {
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();

        // Implicit conversion of IEqualityComparer<BaseClass> to
        // IEqualityComparer<DerivedClass>.
        IEqualityComparer<DerivedClass> childComparer = baseComparer;
    }
}
```

Aby uzyskać więcej przykładów, zobacz [Używanie wariancji w interfejsach dlaC#kolekcji ogólnych ()](./using-variance-in-interfaces-for-generic-collections.md).

Wariancja w interfejsach ogólnych jest obsługiwana tylko w przypadku typów referencyjnych. Typy wartości nie obsługują wariancji. Na przykład `IEnumerable<int>` nie można konwertować niejawnie na `IEnumerable<object>`, ponieważ liczby całkowite są reprezentowane przez typ wartości.

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

Należy również pamiętać, że klasy, które implementują interfejsy wariantów, są nadal niezmienne. Na przykład, chociaż <xref:System.Collections.Generic.List%601> implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601>współwariantu, nie można jawnie skonwertować `List<String>` do `List<Object>`. Jest to zilustrowane w poniższym przykładzie kodu.

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a>Zobacz także

- [Korzystanie z wariancji w interfejsach dlaC#kolekcji ogólnych ()](./using-variance-in-interfaces-for-generic-collections.md)
- [Tworzenie interfejsów ogólnych typu VariantC#()](./creating-variant-generic-interfaces.md)
- [Interfejsy ogólne](../../../../standard/generics/interfaces.md)
- [Wariancja w delegatach (C#)](./variance-in-delegates.md)
