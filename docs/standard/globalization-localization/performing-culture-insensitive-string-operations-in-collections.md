---
title: "Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b84f25aa2470104be98b9f3858091c44f40ba6a7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-string-operations-in-collections"></a>Wykonywanie niezależnych od kultury operacji na ciągach w kolekcjach
Brak klas i członków w <xref:System.Collections> przestrzeni nazw, która zapewniają zależne od kultury zachowanie domyślne. Konstruktory domyślne <xref:System.Collections.CaseInsensitiveComparer> i <xref:System.Collections.CaseInsensitiveHashCodeProvider> klasy zainicjować nowego wystąpienia przy użyciu <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości. Skompilowanie wszystkich przeciążeń <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> metody Utwórz nowe wystąpienie klasy <xref:System.Collections.Hashtable> przy użyciu `Thread.CurrentCulture` właściwość domyślnie. Overloads z <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> metody wykonanie zależne od kultury sortowania przy użyciu domyślnego `Thread.CurrentCulture`. Sortowanie i wyszukiwanie w <xref:System.Collections.SortedList> mogą mieć wpływ `Thread.CurrentCulture` Jeśli ciągi są używane jako klucze. Postępować zgodnie z zaleceniami użycia podane w tej sekcji można uzyskać niezależne od kultury wyniki z tych klas i metod w `Collections` przestrzeni nazw.  
  
 **Uwaga** przekazywanie <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> do porównania metody przeprowadzenia porównania niezależnych od kultury. Jednak go nie powoduje-językowe porównania, na przykład ścieżki do plików, kluczy rejestru i zmiennych środowiskowych. Nie obsługuje zabezpieczeń decyzje na podstawie wyniku porównania. Dla porównania językowe lub obsługę decyzje na podstawie wyniku zabezpieczeń, aplikacja powinna używać metody porównania, która akceptuje <xref:System.StringComparison> wartość. Następnie należy przekazać aplikacji <xref:System.StringComparison>.  
  
## <a name="using-the-caseinsensitivecomparer-and-caseinsensitivehashcodeprovider-classes"></a>Przy użyciu caseinsensitivecomparer — i caseinsensitivehashcodeprovider — klasy  
 Konstruktory domyślne `CaseInsensitiveHashCodeProvider` i `CaseInsensitiveComparer` zainicjować nowe wystąpienie klasy przy użyciu `Thread.CurrentCulture`, co działanie zależne od kultury. Poniższy przykład kodu pokazuje Konstruktor `Hashtable` to zależne od kultury, ponieważ używa domyślnych konstruktorów dla `CaseInsensitiveHashCodeProvider` i `CaseInsensitiveComparer`.  
  
```vb  
internalHashtable = New Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default)  
```  
  
```csharp  
internalHashtable = new Hashtable(CaseInsensitiveHashCodeProvider.Default, CaseInsensitiveComparer.Default);  
```  
  
 Jeśli chcesz utworzyć niezależnych od kultury `Hashtable` przy użyciu `CaseInsensitiveComparer` i `CaseInsensitiveHashCodeProvider` klas, zainicjować nowego wystąpienia tych klas używanie konstruktorów, które akceptują `culture` parametru. Aby uzyskać `culture` parametru, określ <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Poniższy przykład kodu pokazuje konstruktora dla kultury niewrażliwe `Hashtable`.  
  
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
  
## <a name="using-the-collectionsutilcreatecaseinsensitivehashtable-method"></a>Przy użyciu CollectionsUtil.CreateCaseInsensitiveHashTable — metoda  
 `CollectionsUtil.CreateCaseInsensitiveHashTable` Metoda jest przydatna skrót do tworzenia nowego wystąpienia klasy `Hashtable` klasy, która ignoruje wielkość liter ciągów. Jednak wszystkie overloads z `CollectionsUtil.CreateCaseInsensitiveHashTable` metody są zależne od kultury, ponieważ używają one `Thread.CurrentCulture` właściwości. Nie można utworzyć niezależnych od kultury `Hashtable` za pomocą tej metody. Aby utworzyć niezależnych od kultury `Hashtable`, użyj `Hashtable` konstruktora akceptującego `culture` parametru. Aby uzyskać `culture` parametru, określ `CultureInfo.InvariantCulture`. Poniższy przykład kodu pokazuje konstruktora dla kultury niewrażliwe `Hashtable`.  
  
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
## <a name="using-the-sortedlist-class"></a>Przy użyciu SortedList — klasa  
 A `SortedList` reprezentuje kolekcję par klucz wartość są sortowane według kluczy i są dostępne za pomocą klucza i indeksu. Jeśli używasz `SortedList` Jeśli ciągi są klucze, sortowanie i wyszukiwanie mogą mieć wpływ `Thread.CurrentCulture` właściwości. Aby uzyskać niezależne od kultury zachowanie z `SortedList`, Utwórz `SortedList` przy użyciu jednego z konstruktorów, które akceptuje `comparer` parametru. `comparer` Określa parametr <xref:System.Collections.IComparer> implementacji do używania przy porównywaniu kluczy. W przypadku parametru określić klasy niestandardowej funkcji porównującej, która używa `CultureInfo.InvariantCulture` do porównania kluczy. Poniższy przykład przedstawia klasę Niestandardowa funkcja porównująca niezależnych od kultury, która może służyć jako `comparer` parametr `SortedList` konstruktora.  
  
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
  
 Ogólnie, jeśli używasz `SortedList` na ciągi bez określania niestandardowych porównania niezmiennej zmianę `Thread.CurrentCulture` po wypełnione listy może unieważnić listy.  
  
## <a name="using-the-arraylistsort-method"></a>Przy użyciu ArrayList.Sort — metoda  
 Overloads z `ArrayList.Sort` metody wykonanie zależne od kultury sortowania przy użyciu domyślnego `Thread.CurrentCulture` właściwości. Wyniki można różnią się zależnie od kultury z powodu innego sortowania. Aby wyeliminować zachowanie zależne od kultury, użyj przeciążenie tej metody, które akceptują `IComparer` implementacji. Dla `comparer` parametru, określ klasy niestandardowej funkcji porównującej niezmienna, która używa `CultureInfo.InvariantCulture`. Przykład klasy niestandardowej funkcji porównującej niezmiennej znajduje się w [za pomocą klasy SortedList](#cpconperformingculture-insensitivestringoperationsincollectionsanchor1) tematu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.CaseInsensitiveComparer>  
 <xref:System.Collections.CaseInsensitiveHashCodeProvider>  
 <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Collections.SortedList>  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IComparer>  
 [Wykonywanie niezależnych od kultury operacji na ciągach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)  
 <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType>
