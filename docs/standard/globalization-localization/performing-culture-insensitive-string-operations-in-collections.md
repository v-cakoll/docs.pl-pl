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
ms.openlocfilehash: ae1e5c89676eaebfed5bbcae76048c7c48db5a18
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779946"
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach
Brak klas i składowych w <xref:System.Collections> przestrzeni nazw, która zapewnia zachowanie wrażliwość na ustawienia kulturowe domyślnie. Konstruktorów bez parametrów dla <xref:System.Collections.CaseInsensitiveComparer> i <xref:System.Collections.CaseInsensitiveHashCodeProvider> klasy zainicjować nowe wystąpienie, używając <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości. Wszystkie przeciążenia <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> metoda Utwórz nowe wystąpienie klasy <xref:System.Collections.Hashtable> przy użyciu `Thread.CurrentCulture` właściwości domyślnie. Przeciążenia <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> metoda wykonanie kultury sortowania przy użyciu domyślnego `Thread.CurrentCulture`. Sortowanie i wyszukiwanie w <xref:System.Collections.SortedList> mogą mieć wpływ `Thread.CurrentCulture` Jeśli ciągi są używane jako klucze. Postępuj zgodnie z zaleceniami użycia podane w tej sekcji w celu uzyskania wyników niezależnych od kultury z tych klas i metod w `Collections` przestrzeni nazw.  
  
 **Uwaga** przekazywanie <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> do porównania metoda wykonać porównanie niezależnych od kultury. Jednak nie spowoduje nielingwistyczne porównania, na przykład ścieżki do plików, kluczy rejestru i zmiennych środowiskowych. Żadna z nich nie jest obsługiwany decyzje dotyczące bezpieczeństwa, w oparciu o wyniki porównania. Dla porównania nielingwistyczne lub pomocy technicznej dla decyzji dotyczących zabezpieczeń opartych na wynik, aplikacja powinna użyć metody porównania, która akceptuje <xref:System.StringComparison> wartość. Aplikacja powinna następnie przekazać <xref:System.StringComparison>.  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>Przy użyciu caseinsensitivecomparer — i caseinsensitivehashcodeprovider — klasy  
 Konstruktorów bez parametrów dla `CaseInsensitiveHashCodeProvider` i `CaseInsensitiveComparer` inicjuje nowe wystąpienie klasy za pomocą `Thread.CurrentCulture`, dając w zachowaniu zależne od kultury. Poniższy przykład kodu pokazuje konstruktora dla `Hashtable` to wrażliwość na ustawienia kulturowe, ponieważ używa ona konstruktorów bez parametrów dla `CaseInsensitiveHashCodeProvider` i `CaseInsensitiveComparer`.  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 Jeśli chcesz tworzyć niewrażliwość na ustawienia kulturowe `Hashtable` przy użyciu `CaseInsensitiveComparer` i `CaseInsensitiveHashCodeProvider` klasy, zainicjować nowe wystąpienia w ramach tych zajęć, za pomocą konstruktorów, które akceptują `culture` parametru. Aby uzyskać `culture` parametru, określ <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Poniższy przykład kodu pokazuje konstruktora dla niewrażliwość na ustawienia kulturowe `Hashtable`.  
  
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
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>Za pomocą collectionsutil.createcaseinsensitivehashtable — metoda  
 `CollectionsUtil.CreateCaseInsensitiveHashTable` Metodą jest przydatny skrót do tworzenia nowego wystąpienia klasy `Hashtable` klasy, które ignoruje wielkość liter ciągów. Jednak wszystkie przeciążenia `CollectionsUtil.CreateCaseInsensitiveHashTable` metody są zależne od kultury, ponieważ używają one `Thread.CurrentCulture` właściwości. Nie można utworzyć niewrażliwość na ustawienia kulturowe `Hashtable` przy użyciu tej metody. Aby utworzyć niewrażliwość na ustawienia kulturowe `Hashtable`, użyj `Hashtable` Konstruktor, który akceptuje `culture` parametru. Aby uzyskać `culture` parametru, określ `CultureInfo.InvariantCulture`. Poniższy przykład kodu pokazuje konstruktora dla niewrażliwość na ustawienia kulturowe `Hashtable`.  
  
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
## <a name="using-the-sortedlist-class"></a>Za pomocą SortedList — klasa  
 A `SortedList` reprezentuje kolekcję par kluczy i wartości, są sortowane według kluczy, które są dostępne przez klucz i za pomocą indeksu. Kiedy używasz `SortedList` gdzie parametry są klucze, sortowania i wyszukiwania mogą mieć wpływ `Thread.CurrentCulture` właściwości. Uzyskanie niewrażliwość na ustawienia kulturowe zachowanie z `SortedList`, Utwórz `SortedList` przy użyciu jednego z konstruktorów, które akceptuje `comparer` parametru. `comparer` Parametr określa <xref:System.Collections.IComparer> wdrożenia do użycia podczas porównywania kluczy. Dla parametru należy określić klasę niestandardowej funkcji porównującej, która używa `CultureInfo.InvariantCulture` do porównywania kluczy. W poniższym przykładzie pokazano klasę niestandardowego modułu porównującego niewrażliwość na ustawienia kulturowe, można określić jako `comparer` parametr `SortedList` konstruktora.  
  
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
  
 Ogólnie rzecz biorąc, jeśli używasz `SortedList` na ciągi bez określenia niestandardowego niezmiennej modułu porównującego, zmiana `Thread.CurrentCulture` po wprowadzeniu listy mogą nie spełniać ścisłych listy.  
  
## <a name="using-the-arraylistsort-method"></a>Za pomocą ArrayList.sort — metoda  
 Przeciążenia `ArrayList.Sort` metoda wykonanie kultury sortowania przy użyciu domyślnego `Thread.CurrentCulture` właściwości. Wyniki mogą się różnić kultury ze względu na poszczególnych kolejności sortowania. Aby wyeliminować wrażliwość na ustawienia kulturowe zachowanie, użyj przeciążenia tej metody, które akceptują `IComparer` implementacji. Dla `comparer` parametru, określ klasę niestandardowego modułu porównującego niezmiennej, która używa `CultureInfo.InvariantCulture`. Przykład klasy niestandardowej funkcji porównującej niezmiennej znajduje się w [przy użyciu SortedList — klasa](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) tematu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.CaseInsensitiveComparer>
- <xref:System.Collections.CaseInsensitiveHashCodeProvider>
- <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>
- <xref:System.Collections.SortedList>
- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IComparer>
- [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
