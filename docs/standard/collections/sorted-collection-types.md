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
ms.openlocfilehash: c49b3fcd5b50cc5b48497dcf97862e80b066ab46
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957881"
---
# <a name="sorted-collection-types"></a>Sortowane typów kolekcji
<xref:System.Collections.SortedList?displayProperty=nameWithType> Klasa <xref:System.Collections.IDictionary> <xref:System.Collections.Hashtable> ,Klasa<xref:System.Collections.Generic.Dictionary%602> ogólna i Klasa generycznasąpodobnedoklasyiklasygenerycznejwtym,żeimplementująinterfejs,aleutrzymująswoją<xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> elementy w kolejności sortowania według klucza i nie mają cech O (1) wstawiania i pobierania w tabelach skrótów. Trzy klasy mają kilka cech wspólnych:  
  
- Wszystkie trzy klasy implementują <xref:System.Collections.IDictionary?displayProperty=nameWithType> interfejs. Te dwie klasy ogólne implementują <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> również interfejs ogólny.  
  
- Każdy element jest parą klucz/wartość na potrzeby wyliczenia.  
  
    > [!NOTE]
    > Klasa niegeneryczna <xref:System.Collections.SortedList> zwraca <xref:System.Collections.DictionaryEntry> obiekty po wyliczeniu, chociaż dwa typy ogólne zwracają <xref:System.Collections.Generic.KeyValuePair%602> obiekty.  
  
- Elementy są sortowane zgodnie <xref:System.Collections.IComparer?displayProperty=nameWithType> z implementacją (niegeneryczną <xref:System.Collections.SortedList>) lub <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementacją (dla dwóch klas ogólnych).  
  
- Każda Klasa zawiera właściwości, które zwracają Kolekcje zawierające tylko te klucze, lub tylko wartości.  
  
 W poniższej tabeli wymieniono niektóre różnice między dwiema posortowanymi klasami listy a <xref:System.Collections.Generic.SortedDictionary%602> klasą.  
  
|<xref:System.Collections.SortedList>Klasa niegeneryczna <xref:System.Collections.Generic.SortedList%602> i Klasa ogólna|<xref:System.Collections.Generic.SortedDictionary%602>Klasa ogólna|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Właściwości, które zwracają klucze i wartości są indeksowane, umożliwiając wydajne pobieranie indeksowane.|Brak indeksowanego pobierania.|  
|Pobieranie: O (log `n`).|Pobieranie: O (log `n`).|  
|Wstawianie i usuwanie są ogólnie o (`n`); jednak wstawianie ma wartość o (log `n`) dla danych, które są już w porządku sortowania, dzięki czemu każdy element jest dodawany na końcu listy. (Przyjęto założenie, że zmiana rozmiaru nie jest wymagana).|Wstawianie i usuwanie to O (log `n`).|  
|Używa mniejszej ilości pamięci <xref:System.Collections.Generic.SortedDictionary%602>niż.|Używa większej ilości pamięci niż <xref:System.Collections.SortedList> Klasa nieogólna <xref:System.Collections.Generic.SortedList%602> i Klasa ogólna.|  
  
 W przypadku posortowanych list lub słowników, które muszą być dostępne jednocześnie z wielu wątków, można dodać logikę sortowania do klasy, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>która pochodzi od.  
  
> [!NOTE]
> W przypadku wartości, które zawierają własne klucze (na przykład rekordy pracowników, które zawierają numer identyfikacyjny pracownika), można utworzyć kolekcję z podzbiorem, która ma pewne cechy listy i pewne cechy słownika, wywodząc z <xref:System.Collections.ObjectModel.KeyedCollection%602> ogólnej określonej.  
  
 Począwszy od .NET Framework 4, <xref:System.Collections.Generic.SortedSet%601> Klasa udostępnia drzewo z własnym bilansem, które przechowuje dane w kolejności posortowanej po wstawieniu, usunięciu i wyszukiwaniach. Ta klasa i <xref:System.Collections.Generic.HashSet%601> Klasa <xref:System.Collections.Generic.ISet%601> implementują interfejs.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
