---
title: "Często używane typy kolekcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cdc4e0660c5eae0a9550cf73d273d394ed71b823
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="commonly-used-collection-types"></a>Często używane typy kolekcji
Typy kolekcji są typowe przykłady kolekcji danych, takich jak tabele hash, kolejki, stosy, torebki, słowniki i listy.  
  
 Kolekcje są oparte na <xref:System.Collections.ICollection> interfejsu <xref:System.Collections.IList> interfejsu <xref:System.Collections.IDictionary> interfejsu lub ich odpowiedniki ogólnego. <xref:System.Collections.IList> Interfejsu i <xref:System.Collections.IDictionary> interfejsu zarówno pochodne <xref:System.Collections.ICollection> interfejsu; w związku z tym wszystkie kolekcje są oparte na <xref:System.Collections.ICollection> interfejsu bezpośrednio lub pośrednio. W kolekcji na podstawie <xref:System.Collections.IList> interfejsu (takich jak <xref:System.Array>, <xref:System.Collections.ArrayList>, lub <xref:System.Collections.Generic.List%601>) lub bezpośrednio na <xref:System.Collections.ICollection> interfejsu (takich jak <xref:System.Collections.Queue>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Stack>, <xref:System.Collections.Concurrent.ConcurrentStack%601> lub <xref:System.Collections.Generic.LinkedList%601>), co element zawiera tylko wartości. W kolekcji na podstawie <xref:System.Collections.IDictionary> interfejsu (takich jak <xref:System.Collections.Hashtable> i <xref:System.Collections.SortedList> klas, <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Generic.SortedList%602> klasy ogólne), lub <xref:System.Collections.Concurrent.ConcurrentDictionary%602> klas, każdy element zawiera zarówno klucz i wartość.  <xref:System.Collections.ObjectModel.KeyedCollection%602> Klasy jest unikatowa, ponieważ jest listę wartości z kluczami osadzone w wartości, i w związku z tym zachowuje się jak listy i jak słownika.  
  
 Kolekcje ogólne są najlepsze rozwiązania pod kątem silne wpisywanie. Jednak, jeśli język nie obsługuje elementów ogólnych, <xref:System.Collections> przestrzeń nazw zawiera podstawowe kolekcje <xref:System.Collections.CollectionBase>, <xref:System.Collections.ReadOnlyCollectionBase>, i <xref:System.Collections.DictionaryBase>, które są abstrakcyjnych klas podstawowych, które można rozszerzyć, aby utworzyć klasy kolekcji, które są silnie typizowane. Gdy wymagana jest efektywne kolekcji wielowątkowych dostęp, użyj kolekcje ogólne w <xref:System.Collections.Concurrent> przestrzeni nazw.  
  
 Kolekcje mogą się różnić w zależności od sposobu przechowywania elementy, jak są one sortowane realizację wyszukiwania i jak porównań. <xref:System.Collections.Queue> Klasy i <xref:System.Collections.Generic.Queue%601> klasy ogólnej stanowią pierwszy w pierwszym poza listę, gdy <xref:System.Collections.Stack> klasy i <xref:System.Collections.Generic.Stack%601> klasy ogólnej stanowią listę ostatnich w pierwszym poza. <xref:System.Collections.SortedList> Klasy i <xref:System.Collections.Generic.SortedList%602> klasy ogólnej zawiera posortowane wersji <xref:System.Collections.Hashtable> klasy i <xref:System.Collections.Generic.Dictionary%602> klasy ogólnej. Elementy <xref:System.Collections.Hashtable> lub <xref:System.Collections.Generic.Dictionary%602> są dostępne tylko za pomocą klucza elementu, ale elementy <xref:System.Collections.SortedList> lub <xref:System.Collections.ObjectModel.KeyedCollection%602> są dostępne przez klucz lub indeks elementu. Indeksy we wszystkich zbiorach jest liczony od zera, z wyjątkiem <xref:System.Array>, dzięki czemu tablic, które nie są liczony od zera.  
  
 LINQ do obiektów funkcji pozwala na potrzeby dostępu do obiektów w pamięci, tak długo, jak typ obiektu implementuje zapytań LINQ <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>. Zapytania LINQ Podaj wspólnego wzorca do uzyskiwania dostępu do danych; zazwyczaj są to zwięzły i bardziej czytelny niż standardowe `foreach` pętli; oraz udostępnia filtrowania, kolejność i grupowanie możliwości. Zapytania LINQ także może zwiększyć wydajność. Aby uzyskać więcej informacji, zobacz [LINQ do obiektów](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9) i [równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Kolekcje i struktury danych](../../../docs/standard/collections/index.md)|W tym artykule omówiono różne typy kolekcji dostępne w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], w tym stosy, kolejek, list, tablic i słowników.|  
|[Typy kolekcji: słownikowy i tabela skrótów](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Zawiera opis funkcji typy ogólne i nierodzajowe słownik na podstawie wyznaczania wartości skrótu.|  
|[Sortowane typy kolekcji](../../../docs/standard/collections/sorted-collection-types.md)|W tym artykule opisano klasy, które zapewniają funkcje sortowania list i zestawów.|  
|[Typy ogólne](../../../docs/standard/generics/index.md)|Zawiera opis funkcji ogólne, w tym kolekcje ogólne, delegatów i interfejsami [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Zawiera linki do dokumentacji funkcji języka C#, Visual Basic i Visual C++, a do obsługi technologii, takich jak odbicia.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
