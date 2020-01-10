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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711340"
---
# <a name="sorted-collection-types"></a>Sortowane typów kolekcji
Klasa <xref:System.Collections.SortedList?displayProperty=nameWithType>, Klasa ogólna <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> i Klasa ogólna <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> są podobne do klasy <xref:System.Collections.Hashtable> i <xref:System.Collections.Generic.Dictionary%602> klasy ogólnej w tym, że implementują interfejs <xref:System.Collections.IDictionary>, ale utrzymują ich elementy w kolejności sortowania według klucza i nie mają cech O (1) wstawiania i pobierania w tabelach skrótów. Trzy klasy mają kilka cech wspólnych:  
  
- Wszystkie trzy klasy implementują interfejs <xref:System.Collections.IDictionary?displayProperty=nameWithType>. Te dwie klasy generyczne implementują również interfejs ogólny <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>.  
  
- Każdy element jest parą klucz/wartość na potrzeby wyliczenia.  
  
    > [!NOTE]
    > Klasa niegeneryczna <xref:System.Collections.SortedList> zwraca obiekty <xref:System.Collections.DictionaryEntry> po wyliczeniu, chociaż dwa typy ogólne zwracają <xref:System.Collections.Generic.KeyValuePair%602> obiektów.  
  
- Elementy są sortowane zgodnie z implementacją <xref:System.Collections.IComparer?displayProperty=nameWithType> (dla nieogólnego <xref:System.Collections.SortedList>) lub implementacji <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> (dla dwóch klas ogólnych).  
  
- Każda Klasa zawiera właściwości, które zwracają Kolekcje zawierające tylko te klucze, lub tylko wartości.  
  
 W poniższej tabeli wymieniono niektóre różnice między dwiema posortowanymi klasami list i klasą <xref:System.Collections.Generic.SortedDictionary%602>.  
  
|<xref:System.Collections.SortedList> klasy niegenerycznej i klasy generycznej <xref:System.Collections.Generic.SortedList%602>|Klasa ogólna <xref:System.Collections.Generic.SortedDictionary%602>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Właściwości, które zwracają klucze i wartości są indeksowane, umożliwiając wydajne pobieranie indeksowane.|Brak indeksowanego pobierania.|  
|Pobieranie: O (Dziennik `n`).|Pobieranie: O (Dziennik `n`).|  
|Wstawianie i usuwanie jest ogólnie O (`n`); jednak wstawianie ma wartość O (log `n`) dla danych, które są już w porządku sortowania, dzięki czemu każdy element zostanie dodany na końcu listy. (Przyjęto założenie, że zmiana rozmiaru nie jest wymagana).|Wstawianie i usuwanie to O (Dziennik `n`).|  
|Używa mniejszej ilości pamięci niż <xref:System.Collections.Generic.SortedDictionary%602>.|Używa więcej pamięci niż Klasa niegeneryczna <xref:System.Collections.SortedList> i <xref:System.Collections.Generic.SortedList%602> klasy ogólnej.|  
  
 W przypadku posortowanych list lub słowników, które muszą być dostępne jednocześnie z wielu wątków, można dodać logikę sortowania do klasy, która pochodzi od <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.  
  
> [!NOTE]
> W przypadku wartości, które zawierają własne klucze (na przykład rekordy pracowników, które zawierają numer IDENTYFIKACYJNy pracownika), można utworzyć utworzoną kolekcję, która ma pewne cechy listy i pewne cechy słownika, pobierając z klasy generycznej <xref:System.Collections.ObjectModel.KeyedCollection%602>.  
  
 Począwszy od .NET Framework 4, Klasa <xref:System.Collections.Generic.SortedSet%601> udostępnia drzewo z własnym zrównoważeniem, które przechowuje dane w kolejności posortowanej po wstawieniu, usunięciu i wyszukiwaniach. Ta klasa i Klasa <xref:System.Collections.Generic.HashSet%601> implementują interfejs <xref:System.Collections.Generic.ISet%601>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
