---
title: 'Porady: dodawanie i usuwanie elementów ConcurrentDictionary'
ms.date: 05/04/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
ms.openlocfilehash: 6e5204c5a71232ef9d1a050891e7fe6d92c375f2
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796122"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Porady: dodawanie i usuwanie elementów ConcurrentDictionary

Ten przykład pokazuje, jak dodawać, pobierać, aktualizować i usuwać elementy z <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>. Ta klasa kolekcji jest bezpieczną implementacją wątku. Zalecamy używanie go zawsze, gdy wiele wątków może próbować uzyskać dostęp do elementów współbieżnie.

<xref:System.Collections.Concurrent.ConcurrentDictionary%602>Program udostępnia kilka wygodnych metod, które nie są potrzebne, aby kod mógł najpierw sprawdzić, czy klucz istnieje przed próbą dodania lub usunięcia danych. Poniższa tabela zawiera listę tych wygodnych metod i opisuje, kiedy ich używać.

| Metoda | Użyj, gdy... |
|--|--|
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> | Chcesz dodać nową wartość dla określonego klucza i, jeśli klucz już istnieje, chcesz zastąpić jego wartość. |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> | Chcesz pobrać istniejącą wartość dla określonego klucza i, jeśli klucz nie istnieje, chcesz określić parę klucz/wartość. |
| <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A> | Chcesz dodać, pobrać, zaktualizować lub usunąć parę klucz/wartość i, jeśli klucz już istnieje, lub próba nie powiedzie się z innego powodu, chcesz wykonać jakąś alternatywną akcję. |

## <a name="example"></a>Przykład

W poniższym przykładzie użyto dwóch <xref:System.Threading.Tasks.Task> wystąpień, aby dodać do <xref:System.Collections.Concurrent.ConcurrentDictionary%602> współbieżności elementy, a następnie cała zawartość, aby pokazać, że elementy zostały dodane pomyślnie. W przykładzie pokazano również <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, jak używać metod, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>i <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> do dodawania, aktualizowania i pobierania elementów z kolekcji.

[!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
[!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]

<xref:System.Collections.Concurrent.ConcurrentDictionary%602>jest przeznaczony do scenariuszy wielowątkowych. Nie trzeba używać blokad w kodzie, aby dodawać lub usuwać elementy z kolekcji. Jest jednak zawsze możliwe, aby jeden wątek pobierał wartość, a drugi wątek natychmiast zaktualizować kolekcję, dając ten sam klucz nowej wartości.

Ponadto mimo że wszystkie metody <xref:System.Collections.Concurrent.ConcurrentDictionary%602> są bezpieczne wątkowo, nie wszystkie metody są niepodzielne, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> w <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>odróżnieniu od siebie i. Delegat użytkownika, który jest przesyłany do tych metod, jest wywoływany poza wewnętrzną blokadą słownika (dzieje się tak, aby zapobiec blokowaniu wszystkich wątków w nieznanym kodzie). W związku z tym, istnieje możliwość, że ta sekwencja zdarzeń ma być wykonywana:

1. _threadA_ wywołania <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>Thread a, nie wyszukują żadnych elementów i nie tworzy nowego elementu do dodania przez wywołanie `valueFactory` delegata.

1. _threadB_ wywołania <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> threadB współbieżnie, jego `valueFactory` delegat jest wywoływany i dociera do blokady wewnętrznej przed _wątkiem_, a więc nowa para klucz-wartość jest dodawana do słownika.

1. obiekt delegowany użytkownika _wątku jest_ zakończony, a wątek dociera do blokady, ale teraz widzi, że element już istnieje.

1. _wątek_ a wykonuje "Get" i zwraca dane, które zostały wcześniej dodane przez _threadB_.

W związku z tym nie ma gwarancji, że dane zwracane przez <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> są tymi samymi danymi, które zostały utworzone przez wątek. `valueFactory` Podobna sekwencja zdarzeń może wystąpić, gdy <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> jest wywoływana.

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekcje bezpieczne dla wątków](../../../../docs/standard/collections/thread-safe/index.md)
