---
title: Wariancja w interfejsach ogólnych (C#)
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 2020ea54734724de775192a1a438413a73003d17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169665"
---
# <a name="variance-in-generic-interfaces-c"></a>Wariancja w interfejsach ogólnych (C#)

.NET Framework 4 wprowadzono obsługę wariancji dla kilku istniejących interfejsów ogólnych. Obsługa wariancji umożliwia niejawną konwersję klas, które implementują te interfejsy.

Począwszy od .NET Framework 4, następujące interfejsy są wariantowe:

- <xref:System.Collections.Generic.IEnumerable%601>(T jest kowariant)

- <xref:System.Collections.Generic.IEnumerator%601>(T jest kowariant)

- <xref:System.Linq.IQueryable%601>(T jest kowariant)

- <xref:System.Linq.IGrouping%602>(`TKey` `TElement` i są kowariantne)

- <xref:System.Collections.Generic.IComparer%601>(T jest kontrawariantne)

- <xref:System.Collections.Generic.IEqualityComparer%601>(T jest kontrawariantne)

- <xref:System.IComparable%601>(T jest kontrawariantne)

Począwszy od .NET Framework 4.5, następujące interfejsy są wariantowe:

- <xref:System.Collections.Generic.IReadOnlyList%601>(T jest kowariant)

- <xref:System.Collections.Generic.IReadOnlyCollection%601>(T jest kowariant)

Kowariancja pozwala metody mieć bardziej pochodny typ zwracany niż zdefiniowany przez parametr typu ogólnego interfejsu. Aby zilustrować funkcję kowariancji, należy `IEnumerable<Object>` wziąć `IEnumerable<String>`pod uwagę te interfejsy ogólne: i . Interfejs `IEnumerable<String>` nie dziedziczy `IEnumerable<Object>` interfejsu. Jednak `String` typ dziedziczy `Object` typ, aw niektórych przypadkach można przypisać obiekty tych interfejsów do siebie. Jest to pokazane w poniższym przykładzie kodu.

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

We wcześniejszych wersjach programu .NET Framework ten kod powoduje błąd `Option Strict` kompilacji w języku C# i, jeśli jest włączony, w języku Visual Basic. Ale teraz można `strings` użyć `objects`zamiast , jak pokazano <xref:System.Collections.Generic.IEnumerable%601> w poprzednim przykładzie, ponieważ interfejs jest kowariant.

Contravariance pozwala metody mieć typy argumentów, które są mniej pochodne niż określone przez parametr ogólny interfejsu. Aby zilustrować contravariance, załóżmy, że utworzono `BaseComparer` klasę, aby porównać wystąpienia `BaseClass` klasy. Klasa `BaseComparer` implementuje interfejs `IEqualityComparer<BaseClass>`. Ponieważ <xref:System.Collections.Generic.IEqualityComparer%601> interfejs jest teraz kontrawariantny, `BaseComparer` można porównać wystąpienia klas, `BaseClass` które dziedziczą klasę. Jest to pokazane w poniższym przykładzie kodu.

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

Aby uzyskać więcej przykładów, zobacz [Używanie wariancji w interfejsach dla kolekcji ogólnych (C#)](./using-variance-in-interfaces-for-generic-collections.md).

Odchylenie w interfejsach ogólnych jest obsługiwane tylko dla typów referencyjnych. Typy wartości nie obsługują wariancji. Na przykład `IEnumerable<int>` nie można niejawnie przekonwertować na `IEnumerable<object>`, ponieważ liczby całkowite są reprezentowane przez typ wartości.

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

Należy również pamiętać, że klasy implementują interfejsy wariantowe są nadal niezmienne. Na przykład <xref:System.Collections.Generic.List%601> mimo implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601>kowariantny , `List<String>` `List<Object>`nie można niejawnie konwertować do . Jest to zilustrowane w poniższym przykładzie kodu.

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a>Zobacz też

- [Używanie wariancji w interfejsach dla kolekcji ogólnych (C#)](./using-variance-in-interfaces-for-generic-collections.md)
- [Tworzenie wariantowych interfejsów ogólnych (C#)](./creating-variant-generic-interfaces.md)
- [Interfejsy ogólne](../../../../standard/generics/interfaces.md)
- [Wariancja w delegatach (C#)](./variance-in-delegates.md)
