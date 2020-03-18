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
ms.openlocfilehash: adabda4801abc7a11a9b22181701eb233b35a251
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711340"
---
# <a name="sorted-collection-types"></a>Sortowane typów kolekcji
Klasa, <xref:System.Collections.SortedList?displayProperty=nameWithType> klasa <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> ogólna i <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> klasa ogólna <xref:System.Collections.Hashtable> są podobne <xref:System.Collections.Generic.Dictionary%602> do klasy i <xref:System.Collections.IDictionary> klasy ogólnej w tym, że implementują interfejs, ale zachowują swoje elementy w kolejności sortowania według klucza i nie mają o(1) wstawiania i pobierania charakterystyczne tabel mieszania. Trzy klasy mają kilka cech wspólnych:  
  
- Wszystkie trzy klasy <xref:System.Collections.IDictionary?displayProperty=nameWithType> implementują interfejs. Dwie klasy ogólne również <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> zaimplementować interfejs ogólny.  
  
- Każdy element jest parą klucz/wartość do celów wyliczenia.  
  
    > [!NOTE]
    > Klasa <xref:System.Collections.SortedList> nierodzajowa <xref:System.Collections.DictionaryEntry> zwraca obiekty po wyliczeniu, <xref:System.Collections.Generic.KeyValuePair%602> chociaż dwa typy ogólne zwracają obiekty.  
  
- Elementy są sortowane <xref:System.Collections.IComparer?displayProperty=nameWithType> zgodnie z implementacją (dla nieogólnych) <xref:System.Collections.SortedList>lub implementacją <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> (dla dwóch klas ogólnych).  
  
- Każda klasa zawiera właściwości, które zwracają kolekcje zawierające tylko klucze lub tylko wartości.  
  
 W poniższej tabeli wymieniono niektóre różnice między dwiema klasami posortowanych list a klasą. <xref:System.Collections.Generic.SortedDictionary%602>  
  
|<xref:System.Collections.SortedList>klasa nieogólna i <xref:System.Collections.Generic.SortedList%602> klasa ogólna|<xref:System.Collections.Generic.SortedDictionary%602>klasa ogólna|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Właściwości, które zwracają klucze i wartości są indeksowane, umożliwiając wydajne pobieranie indeksowane.|Brak pobierania indeksowane.|  
|Pobieranie jest O(log). `n`|Pobieranie jest O(log). `n`|  
|Wstawianie i usuwanie są`n`na ogół O( ); jednak wstawianie jest O(log) `n`dla danych, które są już w kolejności sortowania, tak aby każdy element jest dodawany na końcu listy. (Zakłada się, że rozmiar nie jest wymagany).)|Wstawianie i usuwanie są `n`O(log).|  
|Zużywa mniej <xref:System.Collections.Generic.SortedDictionary%602>pamięci niż .|Używa więcej pamięci <xref:System.Collections.SortedList> niż klasy <xref:System.Collections.Generic.SortedList%602> nierodzajowej i klasy ogólnej.|  
  
 W przypadku posortowanych list lub słowników, które muszą być dostępne jednocześnie z wielu wątków, można dodać logikę sortowania do klasy, która pochodzi od <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.  
  
> [!NOTE]
> W przypadku wartości, które zawierają własne klucze (na przykład rekordy pracowników, które zawierają numer imion pracownika), można utworzyć kolekcję kluczy, która ma pewne cechy listy i niektóre cechy słownika, wywodząc się z klasy <xref:System.Collections.ObjectModel.KeyedCollection%602> ogólnej.  
  
 Począwszy od .NET Framework <xref:System.Collections.Generic.SortedSet%601> 4, klasa zapewnia drzewa samorównoważenia, który przechowuje dane w posortowane posortowaniu po wstawienia, usunięcia i wyszukiwania. Ta klasa <xref:System.Collections.Generic.HashSet%601> i klasa <xref:System.Collections.Generic.ISet%601> implementują interfejs.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
