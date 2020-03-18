---
title: Często używane typy kolekcji
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- objects [.NET Framework], grouping in collections
- generics [.NET Framework], collections
- IList interface, grouping data in collections
- IDictionary interface, grouping data in collections
- grouping data in collections, generic collection types
- Collections classes
- generic collections
ms.assetid: f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55
ms.openlocfilehash: 1004a2f9a0594d9150d147dec1e16b56205e0d13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711405"
---
# <a name="commonly-used-collection-types"></a>Często używane typy kolekcji
Typy kolekcji są typowe odmiany kolekcji danych, takich jak tabele mieszania, kolejki, stosy, torby, słowniki i listy.  
  
 Kolekcje są <xref:System.Collections.ICollection> oparte na <xref:System.Collections.IList> interfejsie, interfejsie, interfejsie <xref:System.Collections.IDictionary> lub ich ogólnych odpowiednikach. Interfejs <xref:System.Collections.IList> i <xref:System.Collections.IDictionary> interfejs są uzyskiwane <xref:System.Collections.ICollection> z interfejsu; w związku z tym <xref:System.Collections.ICollection> wszystkie kolekcje są oparte na interfejsie bezpośrednio lub pośrednio. W kolekcjach <xref:System.Collections.IList> opartych na <xref:System.Array> <xref:System.Collections.ArrayList>interfejsie <xref:System.Collections.Generic.List%601>(np. <xref:System.Collections.ICollection> , lub <xref:System.Collections.Queue>) <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Stack>lub <xref:System.Collections.Concurrent.ConcurrentStack%601> bezpośrednio na interfejsie (np. , , lub <xref:System.Collections.Generic.LinkedList%601>), każdy element zawiera tylko wartość. W kolekcjach <xref:System.Collections.IDictionary> opartych na <xref:System.Collections.Hashtable> interfejsie (takich jak i <xref:System.Collections.SortedList> klas, <xref:System.Collections.Generic.Dictionary%602> klas <xref:System.Collections.Generic.SortedList%602> <xref:System.Collections.Concurrent.ConcurrentDictionary%602> ogólnych i ogólnych) lub klas, każdy element zawiera zarówno klucz, jak i wartość.  Klasa <xref:System.Collections.ObjectModel.KeyedCollection%602> jest unikatowa, ponieważ jest to lista wartości z kluczami osadzonymi w wartościach i dlatego zachowuje się jak lista i jak słownik.  
  
 Kolekcje ogólne są najlepszym rozwiązaniem do silnego pisania. Jednak jeśli język nie obsługuje typów <xref:System.Collections> ogólnych, obszar nazw <xref:System.Collections.CollectionBase>zawiera <xref:System.Collections.ReadOnlyCollectionBase>kolekcje podstawowe, takie jak , , i <xref:System.Collections.DictionaryBase>, które są abstrakcyjne klasy podstawowe, które mogą być rozszerzone do tworzenia klas kolekcji, które są silnie typowane. Gdy wymagany jest wydajny dostęp do kolekcji wielowątkowej, <xref:System.Collections.Concurrent> należy użyć kolekcji ogólnych w przestrzeni nazw.  
  
 Kolekcje mogą się różnić, w zależności od tego, jak elementy są przechowywane, jak są sortowane, jak wyszukiwania są wykonywane i jak są dokonywane porównania. Klasa <xref:System.Collections.Queue> i <xref:System.Collections.Generic.Queue%601> klasa ogólna zapewniają listy first-in-first-out, podczas gdy <xref:System.Collections.Stack> klasa i klasa <xref:System.Collections.Generic.Stack%601> ogólna zapewniają listy ostatniego na pierwszym poziomie. Klasa <xref:System.Collections.SortedList> i <xref:System.Collections.Generic.SortedList%602> klasa ogólna zapewniają posortowane wersje <xref:System.Collections.Hashtable> klasy i klasy ogólnej. <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.Hashtable> Elementy a lub <xref:System.Collections.Generic.Dictionary%602> a są dostępne tylko przez klucz elementu, <xref:System.Collections.SortedList> ale <xref:System.Collections.ObjectModel.KeyedCollection%602> elementy a lub a są dostępne przez klucz lub przez indeks elementu. Indeksy we wszystkich kolekcjach są <xref:System.Array>oparte na zeru, z wyjątkiem , co pozwala tablice, które nie są oparte na zeru.  
  
 Funkcja LINQ to Objects umożliwia korzystanie z zapytań LINQ w celu uzyskania <xref:System.Collections.IEnumerable> dostępu <xref:System.Collections.Generic.IEnumerable%601>do obiektów w pamięci, o ile typ obiektu implementuje lub . Zapytania LINQ zapewniają wspólny wzorzec dostępu do danych; są zazwyczaj bardziej zwięzłe `foreach` i czytelne niż standardowe pętle; oraz zapewnić możliwości filtrowania, zamawiania i grupowania. Zapytania LINQ można również zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ to Objects (C#),](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)i [Parallel LINQ (PLINQ).](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Kolekcje i struktury danych](../../../docs/standard/collections/index.md)|W tym artykule omówiono różne typy kolekcji dostępne w platformie .NET Framework, w tym stosy, kolejki, listy, tablice i słowniki.|  
|[Typy kolekcji tablic wartości funkcji mieszającej i słowników](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Opisuje funkcje typów słowników opartych na skrótach ogólnych i nieogólnych.|  
|[Sortowane typów kolekcji](../../../docs/standard/collections/sorted-collection-types.md)|W tym artykule opisano klasy, które zapewniają funkcje sortowania list i zestawów.|  
|[Typy ogólne](../../../docs/standard/generics/index.md)|Opisuje funkcję rodzajowy, w tym kolekcje ogólne, delegatów i interfejsów dostarczonych przez .NET Framework. Zawiera łącza do dokumentacji funkcji dla języka C#, Visual Basic i Visual C++ oraz do obsługi technologii, takich jak odbicie.|  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
