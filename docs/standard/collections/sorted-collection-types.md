---
title: Sortowane typów kolekcji
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e932b3af0b952fa88d33df453917cb11c3ceed33
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517763"
---
# <a name="sorted-collection-types"></a>Sortowane typów kolekcji
<xref:System.Collections.SortedList?displayProperty=nameWithType> Klasy <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> klasy generycznej i <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> ogólnej klasy są podobne do <xref:System.Collections.Hashtable> klasy i <xref:System.Collections.Generic.Dictionary%602> ogólnej klasy, implementują <xref:System.Collections.IDictionary> interfejs, ale obsługa ich elementy w sortowaniu kolejność według klucza, a nie mają O(1) wstawiania i pobieranie charakterystycznych dla tabel skrótów. Trzy klasy wspólnym kilka funkcji:  
  
-   Implementowanie wszystkich trzech klasach <xref:System.Collections.IDictionary?displayProperty=nameWithType> interfejsu. Dwie klasy ogólne także implementować <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> interfejs generyczny.  
  
-   Każdy element jest pary klucz/wartość do celów wyliczenia.  
  
    > [!NOTE]
    >  Nongeneric <xref:System.Collections.SortedList> klasy zwraca <xref:System.Collections.DictionaryEntry> obiekty podczas wyliczone, mimo że zwraca dwa typy rodzajowe <xref:System.Collections.Generic.KeyValuePair%602> obiektów.  
  
-   Elementy są sortowane według <xref:System.Collections.IComparer?displayProperty=nameWithType> implementacji (dla nongeneric <xref:System.Collections.SortedList>) lub <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementacji (w przypadku dwóch klas ogólnych).  
  
-   Każda klasa zawiera właściwości, które zwracają kolekcje zawierające tylko kluczy lub tylko wartości.  
  
 W poniższej tabeli wymieniono niektóre różnice między dwoma klasami posortowanej listy i <xref:System.Collections.Generic.SortedDictionary%602> klasy.  
  
|<xref:System.Collections.SortedList> Klasa nierodzajowymi i <xref:System.Collections.Generic.SortedList%602> klasy ogólnej|<xref:System.Collections.Generic.SortedDictionary%602> Klasa ogólna|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Właściwości, które zwracają kluczy i wartości są indeksowane, umożliwiając wydajne indeksowane pobierania.|Nie pobieranie indeksowanego.|  
|Pobieranie jest O (log `n`).|Pobieranie jest O (log `n`).|  
|Wstawiania i usuwania są zwykle O (`n`); jednak wstawiania znajduje się O (log `n`) dla danych, które już znajdują się w kolejności sortowania, tak aby każdy element jest dodawany na końcu listy. (Przy założeniu, że zmiany rozmiaru nie jest wymagane.)|Wstawiania i usuwania są O (log `n`).|  
|Wykorzystuje mniej pamięci niż <xref:System.Collections.Generic.SortedDictionary%602>.|Używa więcej pamięci niż <xref:System.Collections.SortedList> nierodzajowymi klasy i <xref:System.Collections.Generic.SortedList%602> klasy ogólnej.|  
  
 Posortowanej listy lub słowników, które muszą być dostępne jednocześnie z wielu wątków, możesz dodać logikę sortowania do klasy, która pochodzi od klasy <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.  
  
> [!NOTE]
>  Dla wartości, które zawierają własne klucze (na przykład, rekordy pracowników, które zawierają numer identyfikacyjny pracownika), można utworzyć kolekcję kluczem, która ma pewne właściwości listy i niektóre właściwości słownika, wynikające z <xref:System.Collections.ObjectModel.KeyedCollection%602> ogólny Klasa.  
  
 Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Collections.Generic.SortedSet%601> klasa udostępnia własny równoważenia drzewa, która przechowuje dane w kolejności posortowanej po wstawienia, usuwania i wyszukiwania. Ta klasa i <xref:System.Collections.Generic.HashSet%601> implementacji klasy <xref:System.Collections.Generic.ISet%601> interfejsu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
