---
title: 'Porady: dodawanie i usuwanie elementów ConcurrentDictionary'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
ms.openlocfilehash: dc4d13e09a91633fac1fcf5bd8ab5b043473bd7d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711314"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Porady: dodawanie i usuwanie elementów ConcurrentDictionary
Ten przykład pokazuje, jak dodawać, pobierać, aktualizować i usuwać elementy z <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>. Ta klasa kolekcji jest bezpieczną implementacją wątku. Zalecamy używanie go zawsze, gdy wiele wątków może próbować uzyskać dostęp do elementów współbieżnie.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> udostępnia kilka wygodnych metod, które nie są potrzebne, aby kod mógł najpierw sprawdzić, czy klucz istnieje przed próbą dodania lub usunięcia danych. Poniższa tabela zawiera listę tych wygodnych metod i opisuje, kiedy ich używać.  
  
|Metoda|Użyj, gdy...|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Chcesz dodać nową wartość dla określonego klucza i, jeśli klucz już istnieje, chcesz zastąpić jego wartość.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Chcesz pobrać istniejącą wartość dla określonego klucza i, jeśli klucz nie istnieje, chcesz określić parę klucz/wartość.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Chcesz dodać, pobrać, zaktualizować lub usunąć parę klucz/wartość i, jeśli klucz już istnieje, lub próba nie powiedzie się z innego powodu, chcesz wykonać jakąś alternatywną akcję.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa dwóch wystąpień <xref:System.Threading.Tasks.Task>, aby dodać elementy do <xref:System.Collections.Concurrent.ConcurrentDictionary%602> współbieżnie, a następnie wyprowadza całą zawartość, aby pokazać, że elementy zostały dodane pomyślnie. W przykładzie pokazano również, jak za pomocą metod <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>i <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> dodawać, aktualizować i pobierać elementy z kolekcji.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jest zaprojektowana dla scenariuszy wielowątkowych. Nie trzeba używać blokad w kodzie, aby dodawać lub usuwać elementy z kolekcji. Jest jednak zawsze możliwe, aby jeden wątek pobierał wartość, a drugi wątek natychmiast zaktualizować kolekcję, dając ten sam klucz nowej wartości.  
  
 Ponadto mimo że wszystkie metody <xref:System.Collections.Concurrent.ConcurrentDictionary%602> są bezpieczne dla wątków, nie wszystkie metody są niepodzielne, w odróżnieniu od <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>. Delegat użytkownika, który jest przesyłany do tych metod, jest wywoływany poza wewnętrzną blokadą słownika (dzieje się tak, aby zapobiec blokowaniu wszystkich wątków w nieznanym kodzie). W związku z tym, istnieje możliwość, że ta sekwencja zdarzeń ma być wykonywana:  
  
 1\) wywołań wątku <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, nie znajduje żadnych elementów i tworzy nowy element do dodania przez wywołanie delegata obiekt valueFactory.  
  
 2\) wywołania threadB <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> współbieżnie, jego delegat obiekt valueFactory jest wywoływany i dociera do blokady wewnętrznej przed wątkiem, a więc nowa para klucz-wartość zostanie dodana do słownika.  
  
 3\) delegata użytkownika wątku, a wątek dociera do blokady, ale teraz widzi, że element już istnieje.  
  
 4\) Thread a wykonuje "Get" i zwraca dane, które zostały wcześniej dodane przez threadB.  
  
 W związku z tym nie ma gwarancji, że dane zwracane przez <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> są tymi samymi danymi, które zostały utworzone przez obiekt valueFactory wątku. Podobna sekwencja zdarzeń może wystąpić w przypadku wywołania <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
