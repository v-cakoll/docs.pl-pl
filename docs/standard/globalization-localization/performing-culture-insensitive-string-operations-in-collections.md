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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 222376e220bf74274082dfc6b76dc861d4f8ddc5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855985"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach

Istnieją klasy i elementy członkowskie w <xref:System.Collections> przestrzeni nazw, które domyślnie udostępniają zachowania zależne od kultury. Konstruktory bez parametrów dla <xref:System.Collections.CaseInsensitiveComparer> klas i <xref:System.Collections.CaseInsensitiveHashCodeProvider> inicjują nowe wystąpienie przy użyciu <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości. Wszystkie przeciążenia <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> metody tworzą nowe wystąpienie <xref:System.Collections.Hashtable> klasy przy użyciu `Thread.CurrentCulture` domyślnie właściwości. Przeciążenia metody domyślnie wykonują sortowanie zależne od kultury przy użyciu `Thread.CurrentCulture`. <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> W <xref:System.Collections.SortedList> `Thread.CurrentCulture` przypadku, gdy ciągi są używane jako klucze, można mieć wpływ na sortowanie i wyszukiwanie. Postępuj zgodnie z zaleceniami dotyczącymi użycia opisanymi w tej sekcji, aby uzyskać wyniki niewrażliwe na `Collections` kulturę z tych klas i metod w przestrzeni nazw.

> [!NOTE]
> Przekazywanie <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> do metody porównania wykonuje porównanie nieuwzględniające kulturę. Nie powoduje to jednak porównania w języku innym niż język, na przykład w przypadku ścieżek plików, kluczy rejestru i zmiennych środowiskowych. Żadna z tych funkcji nie wspiera podejmowania decyzji dotyczących zabezpieczeń w oparciu o wynik porównania. W przypadku niezgodności z językiem lub pomocy technicznej dla decyzji o zabezpieczeniach opartych na wynikach aplikacja powinna używać metody porównania, <xref:System.StringComparison> która akceptuje wartość. Aplikacja powinna następnie przejść <xref:System.StringComparison>.

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>Korzystanie z klas CaseInsensitiveComparer i CaseInsensitiveHashCodeProvider

Konstruktory bez parametrów dla `CaseInsensitiveHashCodeProvider` i `CaseInsensitiveComparer` inicjują nowe wystąpienie klasy przy użyciu `Thread.CurrentCulture`, w wyniku zachowania wrażliwego na kulturę. Poniższy przykład kodu demonstruje Konstruktor dla `Hashtable` , który jest wrażliwy na kulturę, ponieważ używa konstruktorów bez parametrów dla `CaseInsensitiveHashCodeProvider` i. `CaseInsensitiveComparer`

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

Jeśli chcesz utworzyć `Hashtable` niezależną od `CaseInsensitiveComparer` kultury przy użyciu klas i `CaseInsensitiveHashCodeProvider` , zainicjuj nowe wystąpienia `culture` tych klas przy użyciu konstruktorów, które akceptują parametr. Dla parametru `culture` Określ <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>wartość. Poniższy przykład kodu demonstruje konstruktora dla niezależnych `Hashtable`od kultury.

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

Metoda jest użytecznym skrótem do tworzenia nowego wystąpienia `Hashtable` klasy, które ignoruje wielkość liter. `CollectionsUtil.CreateCaseInsensitiveHashTable` Jednak wszystkie przeciążenia `CollectionsUtil.CreateCaseInsensitiveHashTable` metody są zależne od kultury, `Thread.CurrentCulture` ponieważ używają właściwości. Nie można utworzyć bez uwzględniania `Hashtable` kultury przy użyciu tej metody. Aby utworzyć niezależną `Hashtable`od kultury, `Hashtable` Użyj konstruktora, który akceptuje `culture` parametr. Dla parametru `culture` Określ `CultureInfo.InvariantCulture`wartość. Poniższy przykład kodu demonstruje konstruktora dla niezależnych `Hashtable`od kultury.

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

`SortedList` Reprezentuje kolekcję par klucz-wartość, które są sortowane według kluczy i są dostępne dla klucza i według indeksu. W przypadku korzystania z `SortedList` ciągów gdzie są klucze, `Thread.CurrentCulture` właściwość może mieć wpływ na sortowanie i wyszukiwanie. Aby uzyskać zachowanie niewrażliwe na kulturę `SortedList`z, należy `SortedList` utworzyć przy użyciu jeden z konstruktorów akceptujących `comparer` parametr. `comparer` Parametr<xref:System.Collections.IComparer> określa implementację do użycia podczas porównywania kluczy. Dla parametru Określ niestandardową klasę porównującą używaną `CultureInfo.InvariantCulture` do porównywania kluczy. Poniższy przykład ilustruje niestandardową klasę niezależną od kultury, którą można określić jako `comparer` parametr `SortedList` konstruktora.

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

Ogólnie rzecz biorąc, jeśli `SortedList` używasz w ciągach bez określania niestandardowej niezmiennej modułu porównującego, `Thread.CurrentCulture` zmiana po wypełnieniu listy może unieważnić listę.

## <a name="using-the-arraylistsort-method"></a>Korzystanie z metody ArrayList. Sort

Przeciążenia metody domyślnie wykonują sortowanie zależne od kultury `Thread.CurrentCulture` przy użyciu właściwości. `ArrayList.Sort` Wyniki mogą się różnić w zależności od różnych kolejności sortowania. Aby wyeliminować zachowanie wrażliwe na kulturę, Użyj przeciążenia tej metody, która akceptuje `IComparer` implementację. Dla parametru należy określić niestandardową klasę niezmiennej porównującej, `CultureInfo.InvariantCulture`która używa. `comparer` Przykład niestandardowej klasy niezmiennej porównującej znajduje się w temacie [using klasy SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) .

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
