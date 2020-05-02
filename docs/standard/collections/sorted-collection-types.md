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
ms.openlocfilehash: c948c70a06931f5f93a6f4235585cf7ac94e8533
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728367"
---
# <a name="sorted-collection-types"></a>Sortowane typów kolekcji

<xref:System.Collections.SortedList?displayProperty=nameWithType> Klasa, Klasa <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> ogólna i Klasa <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> generyczna są podobne do <xref:System.Collections.Hashtable> klasy i klasy <xref:System.Collections.Generic.Dictionary%602> generycznej w tym, że implementują <xref:System.Collections.IDictionary> interfejs, ale zachowują swoje elementy w kolejności sortowania według klucza i nie mają cech o (1) wstawiania i pobierania tabel skrótów. Trzy klasy mają kilka cech wspólnych:

- Wszystkie trzy klasy implementują <xref:System.Collections.IDictionary?displayProperty=nameWithType> interfejs. Te dwie klasy ogólne implementują również <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> interfejs ogólny.

- Każdy element jest parą klucz/wartość na potrzeby wyliczenia.

   > [!NOTE]
   > Klasa niegeneryczna <xref:System.Collections.SortedList> zwraca <xref:System.Collections.DictionaryEntry> obiekty po wyliczeniu, chociaż dwa typy ogólne zwracają <xref:System.Collections.Generic.KeyValuePair%602> obiekty.

- Elementy są sortowane zgodnie z <xref:System.Collections.IComparer?displayProperty=nameWithType> implementacją (niegeneryczną <xref:System.Collections.SortedList>) lub <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementacją (dla dwóch klas ogólnych).

- Każda Klasa zawiera właściwości, które zwracają Kolekcje zawierające tylko te klucze, lub tylko wartości.

W poniższej tabeli wymieniono niektóre różnice między dwiema posortowanymi klasami listy a <xref:System.Collections.Generic.SortedDictionary%602> klasą.

| <xref:System.Collections.SortedList>Klasa niegeneryczna <xref:System.Collections.Generic.SortedList%602> i Klasa ogólna | <xref:System.Collections.Generic.SortedDictionary%602>Klasa ogólna |
|--|--|
| Właściwości, które zwracają klucze i wartości są indeksowane, umożliwiając wydajne pobieranie indeksowane. | Brak indeksowanego pobierania. |
| Pobieranie: O (log `n`). | Pobieranie: O (log `n`). |
| Wstawianie i usuwanie jest ogólnie O (`n`); jednak wstawianie ma wartość O (log `n`) dla danych, które są już w kolejności sortowania, dzięki czemu każdy element zostanie dodany na końcu listy. (Przyjęto założenie, że zmiana rozmiaru nie jest wymagana). | Wstawianie i usuwanie to O (log `n`). |
| Używa mniejszej ilości pamięci <xref:System.Collections.Generic.SortedDictionary%602>niż. | Używa większej ilości pamięci niż <xref:System.Collections.SortedList> Klasa nieogólna i Klasa <xref:System.Collections.Generic.SortedList%602> ogólna. |

W przypadku posortowanych list lub słowników, które muszą być dostępne jednocześnie z wielu wątków, można dodać logikę sortowania do klasy, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>która pochodzi od. Podczas rozważania niezmienności, następujące zmienne typy są zgodne z podobną semantyką <xref:System.Collections.Immutable.ImmutableSortedSet%601> sortowania <xref:System.Collections.Immutable.ImmutableSortedDictionary%602>: i.

> [!NOTE]
> W przypadku wartości, które zawierają własne klucze (na przykład rekordy pracowników, które zawierają numer IDENTYFIKACYJNy pracownika), można utworzyć utworzoną kolekcję, która ma pewne cechy listy i pewne cechy słownika, pobierając z klasy <xref:System.Collections.ObjectModel.KeyedCollection%602> generycznej.

Począwszy od .NET Framework 4, <xref:System.Collections.Generic.SortedSet%601> Klasa udostępnia drzewo z własnym bilansem, które przechowuje dane w kolejności posortowanej po wstawieniu, usunięciu i wyszukiwaniach. Ta klasa i <xref:System.Collections.Generic.HashSet%601> Klasa implementują <xref:System.Collections.Generic.ISet%601> interfejs.

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
