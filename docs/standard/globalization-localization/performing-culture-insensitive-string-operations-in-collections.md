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
ms.openlocfilehash: 13a9f4896a37be4297f2a1a11435b85ade381c66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353675"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach

Istnieją klasy i elementy <xref:System.Collections> członkowskie w obszarze nazw, które domyślnie zapewniają zachowanie zależne od kultury. Konstruktory bezparametrów <xref:System.Collections.CaseInsensitiveComparer> dla <xref:System.Collections.CaseInsensitiveHashCodeProvider> i klas zainicjować nowe <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> wystąpienie przy użyciu właściwości. Wszystkie przeciążenia <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> metody utworzyć nowe <xref:System.Collections.Hashtable> wystąpienie klasy `Thread.CurrentCulture` przy użyciu właściwości domyślnie. Przeciążenia <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> metody wykonywania sortowania zależne `Thread.CurrentCulture`od kultury domyślnie przy użyciu . Sortowanie i odciąganie <xref:System.Collections.SortedList> w `Thread.CurrentCulture` a może mieć wpływ, gdy ciągi są używane jako klucze. Postępuj zgodnie z zaleceniami użycia podanymi w tej sekcji, aby `Collections` uzyskać wyniki niewrażliwe na kulturę z tych klas i metod w obszarze nazw.

> [!NOTE]
> Przekazywanie <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> do metody porównania wykonuje porównanie niewrażliwe na kulturę. Jednak nie powoduje porównania nielingwistycznego, na przykład dla ścieżek plików, kluczy rejestru i zmiennych środowiskowych. Nie obsługuje również decyzji dotyczących zabezpieczeń na podstawie wyniku porównania. W przypadku porównania nielingwistycznego lub obsługi decyzji dotyczących zabezpieczeń opartych na <xref:System.StringComparison> wynikach aplikacja powinna używać metody porównywania, która akceptuje wartość. Aplikacja powinna następnie <xref:System.StringComparison>przejść .

## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>Korzystanie z klas CaseInsensitiveComparer i CaseInsensitiveHashCodeProvider

Konstruktory bez `CaseInsensitiveHashCodeProvider` parametrów `CaseInsensitiveComparer` dla i zainicjować nowe wystąpienie `Thread.CurrentCulture`klasy przy użyciu , w wyniku zachowania zależne od kultury. Poniższy przykład kodu przedstawia konstruktora `Hashtable` dla, który jest zależny od kultury, `CaseInsensitiveHashCodeProvider` `CaseInsensitiveComparer`ponieważ używa konstruktorów bezparametrów dla i .

```vb
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)
```

```csharp
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);
```

Jeśli chcesz utworzyć kultury niewrażliwe `Hashtable` przy `CaseInsensitiveComparer` `CaseInsensitiveHashCodeProvider` użyciu i klas, zainicjować nowe wystąpienia tych klas przy `culture` użyciu konstruktorów, które akceptują parametr. Dla `culture` parametru <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>określ . Poniższy przykład kodu przedstawia konstruktora dla `Hashtable`kultury niewrażliwe .

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

## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>Korzystanie z metody CollectionsUtil.CreateCaseInsensitiveHashTable

Metoda `CollectionsUtil.CreateCaseInsensitiveHashTable` jest przydatnym skrótem do `Hashtable` tworzenia nowego wystąpienia klasy, która ignoruje przypadek ciągów. Jednak wszystkie przeciążenia `CollectionsUtil.CreateCaseInsensitiveHashTable` metody są zależne od `Thread.CurrentCulture` kultury, ponieważ używają właściwości. Nie można utworzyć kultury `Hashtable` niewrażliwe przy użyciu tej metody. Aby utworzyć niewrażliwe `Hashtable`na kulturę, należy użyć `Hashtable` konstruktora, który akceptuje `culture` parametr. Dla `culture` parametru `CultureInfo.InvariantCulture`określ . Poniższy przykład kodu przedstawia konstruktora dla `Hashtable`kultury niewrażliwe .

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

A `SortedList` reprezentuje kolekcję par klucz i wartość, które są sortowane według kluczy i są dostępne przez klucz i przez indeks. Korzystając z `SortedList` klawiszy where strings są klucze, sortowanie i `Thread.CurrentCulture` odciąganie może mieć wpływ właściwości. Aby uzyskać zachowanie niewrażliwe `SortedList`na kulturę z , należy utworzyć `SortedList` przy `comparer` użyciu jednego z konstruktorów, który akceptuje parametr. Parametr `comparer` określa <xref:System.Collections.IComparer> implementację do użycia podczas porównywania kluczy. Dla parametru określ klasę niestandardowego `CultureInfo.InvariantCulture` porównania, która używa do porównywania kluczy. W poniższym przykładzie przedstawiono klasę niewrażliwe kultury niewrażliwe klasy `comparer` porównania, `SortedList` który można określić jako parametr do konstruktora.

```vb
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

Ogólnie rzecz biorąc, `SortedList` jeśli używasz na ciągi bez określania niestandardowego `Thread.CurrentCulture` niezmiennego porównania, zmiana po wypełnieniu listy może unieważnić listę.

## <a name="using-the-arraylistsort-method"></a>Korzystanie z metody ArrayList.Sort

Przeciążenia `ArrayList.Sort` metody wykonywania sortowania zależne `Thread.CurrentCulture` od kultury domyślnie przy użyciu właściwości. Wyniki mogą się różnić w zależności od kultury ze względu na różne kolejność sortowania. Aby wyeliminować zachowanie zależne od kultury, należy użyć `IComparer` przeciążenia tej metody, które akceptują implementacji. Dla `comparer` parametru określ niestandardową klasę `CultureInfo.InvariantCulture`niezmiennego porównywarki, która używa . Przykład niezmiennej klasy porównania znajduje się w temacie [Korzystanie z klasy sortedlist.](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1)

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
