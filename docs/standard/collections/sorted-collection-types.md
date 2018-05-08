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
ms.openlocfilehash: 31b40167be4f2760eb7c88155e1733266e34d11d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="sorted-collection-types"></a>Sortowane typów kolekcji
<xref:System.Collections.SortedList?displayProperty=nameWithType> Klasy <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> klasy ogólnej i <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> klasy ogólnej są podobne do <xref:System.Collections.Hashtable> klasy i <xref:System.Collections.Generic.Dictionary%602> ogólnej klasy w tym wdrażają <xref:System.Collections.IDictionary> interfejsu, ale obsługa ich kolejność elementów w sortowania według klucza, a nie mają O(1) wstawiania i pobierania charakterystycznych dla tablic skrótów. Trzy klasy mają kilka funkcji cechy wspólne:  
  
-   Wszystkie trzy klasy implementować <xref:System.Collections.IDictionary?displayProperty=nameWithType> interfejsu. Dwie klasy rodzajowe także implementować <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> interfejs generyczny.  
  
-   Każdy element jest parę klucza i wartości dla celów wyliczenia.  
  
    > [!NOTE]
    >  Nongeneric <xref:System.Collections.SortedList> klasy zwraca <xref:System.Collections.DictionaryEntry> obiektów po wyliczone, mimo że zwracać dwa typy ogólne <xref:System.Collections.Generic.KeyValuePair%602> obiektów.  
  
-   Elementy są sortowane według <xref:System.Collections.IComparer?displayProperty=nameWithType> implementacji (dla nongeneric <xref:System.Collections.SortedList>) lub <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementacji (dwie klasy ogólnego).  
  
-   Każda klasa udostępnia właściwości, które zwracają kolekcje zawierające tylko klucze lub tylko wartości.  
  
 W poniższej tabeli przedstawiono niektóre różnice między dwoma klasami posortowaną listę i <xref:System.Collections.Generic.SortedDictionary%602> klasy.  
  
|<xref:System.Collections.SortedList> Klasa nierodzajowe i <xref:System.Collections.Generic.SortedList%602> klasy ogólnej|<xref:System.Collections.Generic.SortedDictionary%602> Klasa ogólna|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Właściwości, które zwracają kluczy i wartości są indeksowane, umożliwiając wydajne indeksowana pobierania.|Nie indeksowanego pobierania.|  
|Pobieranie jest O (dziennika `n`).|Pobieranie jest O (dziennika `n`).|  
|Wstawianie i usuwanie są zwykle O (`n`), jednak wstawiania jest O (dziennika `n`) dla danych, które już znajdują się w kolejności sortowania, dzięki czemu każdy element zostanie dodany na końcu listy. (Przy założeniu, że zmiany rozmiaru nie jest wymagane.)|Wstawianie i usuwanie są O (dziennika `n`).|  
|Wykorzystuje mniej pamięci niż <xref:System.Collections.Generic.SortedDictionary%602>.|Używa więcej pamięci niż <xref:System.Collections.SortedList> nierodzajowe klasy i <xref:System.Collections.Generic.SortedList%602> klasy ogólnej.|  
  
 Posortowane list lub słowników, które muszą być dostępne jednocześnie z wielu wątków, można dodać logikę sortowania do klasy, która jest pochodną <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.  
  
> [!NOTE]
>  Wartości, które zawierają własne klucze (na przykład pracownik rekordy, które zawierają numer identyfikacyjny), można utworzyć kolekcji kluczem, w której niektóre właściwości listy i niektóre właściwości słownika przez wynikających z <xref:System.Collections.ObjectModel.KeyedCollection%602> ogólne Klasa.  
  
 Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Collections.Generic.SortedSet%601> klasa udostępnia własnym równoważenia drzewa, która przechowuje dane posortowane po operacji wstawienia, usuwanie i wyszukiwania. Ta klasa i <xref:System.Collections.Generic.HashSet%601> implementacji klasy <xref:System.Collections.Generic.ISet%601> interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>  
 [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
