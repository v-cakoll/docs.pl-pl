---
title: Sortowane typów kolekcji
ms.date: 04/30/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
ms.openlocfilehash: 2d9d3744859eea1a09923980b3b4c57eca6bba97
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287942"
---
# <a name="sorted-collection-types"></a>Sortowane typów kolekcji

Klasa <xref:System.Collections.SortedList?displayProperty=nameWithType> , <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> Klasa ogólna i <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> Klasa generyczna są podobne do <xref:System.Collections.Hashtable> klasy i <xref:System.Collections.Generic.Dictionary%602> klasy generycznej w tym, że implementują <xref:System.Collections.IDictionary> interfejs, ale zachowują swoje elementy w kolejności sortowania według klucza i nie mają cech o (1) wstawiania i pobierania tabel skrótów. Trzy klasy mają kilka cech wspólnych:

- Wszystkie trzy klasy implementują <xref:System.Collections.IDictionary?displayProperty=nameWithType> interfejs. Te dwie klasy ogólne implementują również <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> interfejs ogólny.

- Każdy element jest parą klucz/wartość na potrzeby wyliczenia.

   > [!NOTE]
   > Klasa niegeneryczna <xref:System.Collections.SortedList> zwraca <xref:System.Collections.DictionaryEntry> obiekty po wyliczeniu, chociaż dwa typy ogólne zwracają <xref:System.Collections.Generic.KeyValuePair%602> obiekty.

- Elementy są sortowane zgodnie z <xref:System.Collections.IComparer?displayProperty=nameWithType> implementacją (niegeneryczną <xref:System.Collections.SortedList> ) lub <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementacją (dla dwóch klas ogólnych).

- Każda Klasa zawiera właściwości, które zwracają Kolekcje zawierające tylko te klucze, lub tylko wartości.

W poniższej tabeli wymieniono niektóre różnice między dwiema posortowanymi klasami listy a <xref:System.Collections.Generic.SortedDictionary%602> klasą.

| <xref:System.Collections.SortedList>Klasa niegeneryczna i <xref:System.Collections.Generic.SortedList%602> Klasa ogólna | <xref:System.Collections.Generic.SortedDictionary%602>Klasa ogólna |
|--|--|
| Właściwości, które zwracają klucze i wartości są indeksowane, umożliwiając wydajne pobieranie indeksowane. | Brak indeksowanego pobierania. |
| Pobieranie: O (log `n` ). | Pobieranie: O (log `n` ). |
| Wstawianie i usuwanie są ogólnie O ( `n` ); jednak wstawianie ma wartość o (log `n` ) dla danych, które są już w porządku sortowania, dzięki czemu każdy element jest dodawany na końcu listy. (Przyjęto założenie, że zmiana rozmiaru nie jest wymagana). | Wstawianie i usuwanie to O (log `n` ). |
| Używa mniejszej ilości pamięci niż <xref:System.Collections.Generic.SortedDictionary%602> . | Używa większej ilości pamięci niż <xref:System.Collections.SortedList> Klasa nieogólna i <xref:System.Collections.Generic.SortedList%602> Klasa ogólna. |

W przypadku posortowanych list lub słowników, które muszą być dostępne jednocześnie z wielu wątków, można dodać logikę sortowania do klasy, która pochodzi od <xref:System.Collections.Concurrent.ConcurrentDictionary%602> . Podczas rozważania niezmienności, następujące zmienne typy są zgodne z podobną semantyką sortowania: <xref:System.Collections.Immutable.ImmutableSortedSet%601> i <xref:System.Collections.Immutable.ImmutableSortedDictionary%602> .

> [!NOTE]
> W przypadku wartości, które zawierają własne klucze (na przykład rekordy pracowników, które zawierają numer IDENTYFIKACYJNy pracownika), można utworzyć utworzoną kolekcję, która ma pewne cechy listy i pewne cechy słownika, pobierając z <xref:System.Collections.ObjectModel.KeyedCollection%602> klasy generycznej.

Począwszy od .NET Framework 4, <xref:System.Collections.Generic.SortedSet%601> Klasa udostępnia drzewo z własnym bilansem, które przechowuje dane w kolejności posortowanej po wstawieniu, usunięciu i wyszukiwaniach. Ta klasa i <xref:System.Collections.Generic.HashSet%601> Klasa implementują <xref:System.Collections.Generic.ISet%601> interfejs.

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Często używane typy kolekcji](commonly-used-collection-types.md)
