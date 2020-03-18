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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711314"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Porady: dodawanie i usuwanie elementów ConcurrentDictionary
W tym przykładzie pokazano, jak dodawać, pobierać, aktualizować i usuwać elementy z pliku <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>. Ta klasa kolekcji jest implementacją zabezpieczaną dla wątków. Zaleca się, aby używać go zawsze, gdy wiele wątków może próbować uzyskać dostęp do elementów jednocześnie.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>Udostępnia kilka metod wygody, które sprawiają, że nie ma potrzeby dla kodu, aby najpierw sprawdzić, czy klucz istnieje przed próbą dodania lub usunięcia danych. W poniższej tabeli wymieniono te metody wygody i opisano, kiedy z nich korzystać.  
  
|Metoda|Użyj, gdy...|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Chcesz dodać nową wartość dla określonego klucza i, jeśli klucz już istnieje, chcesz zastąpić jego wartość.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Chcesz pobrać istniejącą wartość dla określonego klucza, a jeśli klucz nie istnieje, chcesz określić parę klucz/wartość.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Chcesz dodać, uzyskać, zaktualizować lub usunąć parę klucz/wartość, a jeśli klucz już istnieje lub próba nie powiedzie się z jakiegokolwiek innego powodu, chcesz podjąć jakąś alternatywną akcję.|  
  
## <a name="example"></a>Przykład  
 W poniższym <xref:System.Threading.Tasks.Task> przykładzie użyto dwóch wystąpień, aby dodać niektóre elementy do <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jednocześnie, a następnie generuje całą zawartość, aby pokazać, że elementy zostały pomyślnie dodane. W przykładzie pokazano również, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>jak <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> używać <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, i metody dodawania, aktualizowania i pobierania elementów z kolekcji.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>jest przeznaczony dla scenariuszy wielowątkowych. Nie trzeba używać blokad w kodzie, aby dodać lub usunąć elementy z kolekcji. Jednak zawsze jest możliwe dla jednego wątku, aby pobrać wartość, a inny wątek natychmiast zaktualizować kolekcję, nadając ten sam klucz nową wartość.  
  
 Ponadto, chociaż wszystkie <xref:System.Collections.Concurrent.ConcurrentDictionary%602> metody są bezpieczne dla wątków, nie <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> wszystkie <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>metody są atomowe, w szczególności i . Delegat użytkownika, który jest przekazywany do tych metod jest wywoływana poza słownika blokady wewnętrznej (odbywa się to, aby zapobiec nieznany kod z blokowania wszystkich wątków). W związku z tym jest możliwe dla tej sekwencji zdarzeń występuje:  
  
 1\) threadA <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>wywołuje , nie znajdzie elementu i tworzy nowy element do dodaj, wywołując valueFactory delegate.  
  
 2\) threadB <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> wywołuje jednocześnie, jego wartośćDelegat fabryki jest wywoływany i dociera do wewnętrznej blokady przed threadA, a więc jego nowa para klucz wartość jest dodawany do słownika.  
  
 Delegat\) użytkownika 3 threadA kończy się, a wątek dociera do blokady, ale teraz widzi, że element już istnieje.  
  
 4\) threadA wykonuje "Get" i zwraca dane, które zostały wcześniej dodane przez threadB.  
  
 W związku z tym nie jest gwarantowane, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> że dane, które są zwracane przez to te same dane, które zostały utworzone przez valueFactory wątku. Podobna sekwencja zdarzeń <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> może wystąpić, gdy jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
