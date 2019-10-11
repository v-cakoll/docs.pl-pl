---
title: Wariancja w interfejsachC#ogólnych ()
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 71225814a11074f52e4937dec88ca5e27114d6c7
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179061"
---
# <a name="variance-in-generic-interfaces-c"></a>Wariancja w interfejsachC#ogólnych ()

.NET Framework 4 wprowadziła obsługę wariancji dla kilku istniejących interfejsów ogólnych. Obsługa wariancji umożliwia niejawną konwersję klas implementujących te interfejsy. 

Począwszy od .NET Framework 4, następujące interfejsy są wariantem:

- <xref:System.Collections.Generic.IEnumerable%601> (T jest współwariantem)

- <xref:System.Collections.Generic.IEnumerator%601> (T jest współwariantem)

- <xref:System.Linq.IQueryable%601> (T jest współwariantem)

- <xref:System.Linq.IGrouping%602> (`TKey` i `TElement` są współwariantem)

- <xref:System.Collections.Generic.IComparer%601> (T to kontrawariantne)

- <xref:System.Collections.Generic.IEqualityComparer%601> (T to kontrawariantne)

- <xref:System.IComparable%601> (T to kontrawariantne)

Począwszy od .NET Framework 4,5, następujące interfejsy są wariantem:

- <xref:System.Collections.Generic.IReadOnlyList%601> (T jest współwariantem)

- <xref:System.Collections.Generic.IReadOnlyCollection%601> (T jest współwariantem)

Kowariancja zezwala metodzie na bardziej pochodny typ zwracany niż zdefiniowany przez parametr typu ogólnego interfejsu. Aby zilustrować funkcję kowariancji, należy wziąć pod uwagę następujące interfejsy ogólne: `IEnumerable<Object>` i `IEnumerable<String>`. Interfejs `IEnumerable<String>` nie dziedziczy interfejsu `IEnumerable<Object>`. Jednak typ `String` dziedziczy typ `Object`, a w niektórych przypadkach może być konieczne przypisanie obiektów do obu tych interfejsów. Jest to pokazane w poniższym przykładzie kodu.

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

We wcześniejszych wersjach .NET Framework ten kod powoduje błąd kompilacji w C# i, jeśli `Option Strict` jest włączona, w Visual Basic. Teraz można użyć `strings` zamiast `objects`, jak pokazano w poprzednim przykładzie, ponieważ interfejs <xref:System.Collections.Generic.IEnumerable%601> jest niezmienny.

Kontrawariancja umożliwia metodzie posiadanie typów argumentów, które są mniej pochodne niż określone przez parametr generyczny interfejsu. Aby zilustrować kontrawariancja, założono, że utworzono klasę `BaseComparer` w celu porównania wystąpień klasy `BaseClass`. Klasa `BaseComparer` implementuje interfejs `IEqualityComparer<BaseClass>`. Ponieważ interfejs <xref:System.Collections.Generic.IEqualityComparer%601> jest teraz kontrawariantne, można użyć `BaseComparer` do porównania wystąpień klas, które dziedziczą klasę `BaseClass`. Jest to pokazane w poniższym przykładzie kodu.

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

Wariancja w interfejsach ogólnych jest obsługiwana tylko w przypadku typów referencyjnych. Typy wartości nie obsługują wariancji. Na przykład `IEnumerable<int>` nie może być niejawnie konwertowany do `IEnumerable<object>`, ponieważ liczby całkowite są reprezentowane przez typ wartości.

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

Należy również pamiętać, że klasy, które implementują interfejsy wariantów, są nadal niezmienne. Na przykład mimo że <xref:System.Collections.Generic.List%601> implementuje interfejs współwariantowy <xref:System.Collections.Generic.IEnumerable%601>, nie można niejawnie skonwertować `List<String>` na `List<Object>`. Jest to zilustrowane w poniższym przykładzie kodu.

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
