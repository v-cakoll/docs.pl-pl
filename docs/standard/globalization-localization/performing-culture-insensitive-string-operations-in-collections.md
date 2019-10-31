---
title: Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CaseInsensitiveComparer class, using
- CollectionsUtil.CreateCaseInsensitiveHashtable method
- culture-insensitive string operations, collections
- collections [.NET Framework], culture-insensitive string operations
- CaseInsensitiveHashCodeProvider class, using
- ArrayList.Sort method
- SortedList class, culture-insensitive string operations
- culture parameter
ms.assetid: 5cdc9396-a64b-4615-a1cd-b605db4c5983
ms.openlocfilehash: 5bd6e49f23ca5b694664393f3eb18cc72ada7bdd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120813"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach

W przestrzeni nazw <xref:System.Collections> znajdują się klasy i elementy członkowskie, które domyślnie udostępniają zachowania zależne od kultury. Konstruktory bez parametrów dla klas <xref:System.Collections.CaseInsensitiveComparer> i <xref:System.Collections.CaseInsensitiveHashCodeProvider> inicjują nowe wystąpienie przy użyciu właściwości <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>. Wszystkie przeciążenia metody <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> tworzą nowe wystąpienie klasy <xref:System.Collections.Hashtable> domyślnie przy użyciu właściwości `Thread.CurrentCulture`. Przeciążenia metody <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> są wykonywane domyślnie przez `Thread.CurrentCulture`. `Thread.CurrentCulture`, gdy ciągi są używane jako klucze, można mieć wpływ na sortowanie i wyszukiwanie w <xref:System.Collections.SortedList>. Postępuj zgodnie z zaleceniami dotyczącymi użycia opisanymi w tej sekcji, aby uzyskać wyniki niewrażliwe na kulturę z tych klas i metod w przestrzeni nazw `Collections`.

> [!NOTE]
> Przekazywanie <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> do metody porównania wykonuje porównanie nieuwzględniające kulturę. Nie powoduje to jednak porównania w języku innym niż język, na przykład w przypadku ścieżek plików, kluczy rejestru i zmiennych środowiskowych. Żadna z tych funkcji nie wspiera podejmowania decyzji dotyczących zabezpieczeń w oparciu o wynik porównania. W przypadku niezgodności z językiem lub pomocy technicznej dla decyzji o zabezpieczeniach opartych na wynikach aplikacja powinna używać metody porównania, która akceptuje wartość <xref:System.StringComparison>. Aplikacja powinna następnie przekazać <xref:System.StringComparison>.

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>Korzystanie z klas CaseInsensitiveComparer i CaseInsensitiveHashCodeProvider

Konstruktory bez parametrów dla `CaseInsensitiveHashCodeProvider` i `CaseInsensitiveComparer` inicjują nowe wystąpienie klasy przy użyciu `Thread.CurrentCulture`, co wpływa na zachowanie kulturowe. Poniższy przykład kodu demonstruje konstruktora dla `Hashtable`, który jest wrażliwy na kulturę, ponieważ używa konstruktorów bez parametrów dla `CaseInsensitiveHashCodeProvider` i `CaseInsensitiveComparer`.

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

Jeśli chcesz utworzyć `Hashtable` bez uwzględniania kultur przy użyciu klas `CaseInsensitiveComparer` i `CaseInsensitiveHashCodeProvider`, zainicjuj nowe wystąpienia tych klas przy użyciu konstruktorów, które akceptują parametr `culture`. Dla parametru `culture` Określ <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Poniższy przykład kodu demonstruje konstruktora dla `Hashtable`niewrażliwych na kulturę.

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>Korzystanie z metody CollectionsUtil. CreateCaseInsensitiveHashTable

Metoda `CollectionsUtil.CreateCaseInsensitiveHashTable` jest użytecznym skrótem do tworzenia nowego wystąpienia klasy `Hashtable`, która ignoruje wielkość liter w ciągach. Jednak wszystkie przeciążenia metody `CollectionsUtil.CreateCaseInsensitiveHashTable` są zależne od kultury, ponieważ używają właściwości `Thread.CurrentCulture`. Nie można utworzyć `Hashtable` bez uwzględniania kultur przy użyciu tej metody. Aby utworzyć `Hashtable`bez uwzględniania kultur, należy użyć konstruktora `Hashtable`, który akceptuje parametr `culture`. Dla parametru `culture` Określ `CultureInfo.InvariantCulture`. Poniższy przykład kodu demonstruje konstruktora dla `Hashtable`niewrażliwych na kulturę.

```vb
internalHashtable = New Hashtable(New
    CaseInsensitiveHashCodeProvider(CultureInfo.InvariantCulture),
    New CaseInsensitiveComparer(CultureInfo.InvariantCulture))
```

```csharp
internalHashtable = new Hashtable(new CaseInsensitiveHashCodeProvider
    (CultureInfo.InvariantCulture),
    new CaseInsensitiveComparer(CultureInfo.InvariantCulture));
```

<a name="cpconperformingculture-insensitivestringoperationsincollectionsanchor1"></a>

## <a name="using-the-sortedlist-class"></a>Korzystanie z klasy SortedList

`SortedList` reprezentuje kolekcję par klucz-wartość, które są sortowane według kluczy i są dostępne dla klucza i według indeksu. W przypadku używania `SortedList`, w którym ciągi są kluczami, właściwość `Thread.CurrentCulture` może mieć wpływ na sortowanie i wyszukiwanie. Aby uzyskać zachowanie niewrażliwe na kulturę z `SortedList`, Utwórz `SortedList` przy użyciu jednego z konstruktorów, które akceptują parametr `comparer`. `comparer` parametr określa implementację <xref:System.Collections.IComparer> do użycia podczas porównywania kluczy. Dla parametru Określ niestandardową klasę porównującą, która używa `CultureInfo.InvariantCulture` do porównywania kluczy. Poniższy przykład ilustruje niestandardową klasę niezależną od kultury, którą można określić jako parametr `comparer` konstruktora `SortedList`.

```vb
Imports System
Imports System.Collections
Imports System.Globalization

Friend Class InvariantComparer
    Implements IComparer
    Private m_compareInfo As CompareInfo
    Friend Shared [Default] As New InvariantComparer()

    Friend Sub New()
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo
    End Sub

    Public Function Compare(a As Object, b As Object) As Integer _
            Implements IComparer.Compare
        Dim sa As String = CType(a, String)
        Dim sb As String = CType(b, String)
        If Not (sa Is Nothing) And Not (sb Is Nothing) Then
            Return m_compareInfo.Compare(sa, sb)
        Else
            Return Comparer.Default.Compare(a, b)
        End If
    End Function
End Class
```

```csharp
using System;
using System.Collections;
using System.Globalization;

internal class InvariantComparer : IComparer
{
    private CompareInfo m_compareInfo;
    internal static readonly InvariantComparer Default = new
        InvariantComparer();

    internal InvariantComparer()
    {
        m_compareInfo = CultureInfo.InvariantCulture.CompareInfo;
    }

    public int Compare(Object a, Object b)
    {
        String sa = a as String;
        String sb = b as String;
        if (sa != null && sb != null)
            return m_compareInfo.Compare(sa, sb);
        else
            return Comparer.Default.Compare(a,b);
    }
}
```

Ogólnie rzecz biorąc, jeśli używasz `SortedList` na ciągach bez określenia niestandardowej niezmiennej niezmiennej, zmiana na `Thread.CurrentCulture` po wypełnieniu listy może unieważnić listę.

## <a name="using-the-arraylistsort-method"></a>Korzystanie z metody ArrayList. Sort

Przeciążenia metody `ArrayList.Sort` wykonują domyślnie sortowanie zależne od kultury przy użyciu właściwości `Thread.CurrentCulture`. Wyniki mogą się różnić w zależności od różnych kolejności sortowania. Aby wyeliminować zachowanie wrażliwe na kulturę, Użyj przeciążenia tej metody, która akceptuje implementację `IComparer`. Dla parametru `comparer` Określ niestandardową klasę niezmiennej porównującej, która używa `CultureInfo.InvariantCulture`. Przykład niestandardowej klasy niezmiennej porównującej znajduje się w temacie [using klasy SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) .

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
