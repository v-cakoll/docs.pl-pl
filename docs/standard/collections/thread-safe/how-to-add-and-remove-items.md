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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98d30cd89114aa4aa3d4f7f71f5174c54d3fcecb
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075764"
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Porady: dodawanie i usuwanie elementów ConcurrentDictionary
W tym przykładzie pokazano, jak dodawanie, pobieranie, Aktualizuj i usuń elementy z <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>. Ta klasa kolekcji jest implementacja metodą o bezpiecznych wątkach. Zalecamy użycie go zawsze wtedy, gdy wiele wątków może próbować uzyskać dostęp do elementów jednocześnie.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> zapewnia kilka metod jako udogodnienie, które ułatwiają niepotrzebne dla kodu najpierw sprawdzić, czy klucz istnieje przed próbuje dodać lub usunąć dane. Poniższa tabela zawiera listę tych metod jako udogodnienie i opisuje, kiedy ich używać.  
  
|Metoda|Należy użyć, gdy...|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Aby dodać nową wartość dla określonego klucza i, jeśli klucz już istnieje, chcesz zastąpić jej wartość.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Chcesz pobrać istniejącą wartość dla określonego klucza i, jeśli klucz nie istnieje, chcesz określić pary klucz/wartość.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Chcesz dodać, pobieranie, aktualizowanie lub usuwanie pary klucz/wartość, a jeśli klucz już istnieje, lub próba nie powiedzie się z jakiegokolwiek innego powodu, chcesz wykonania określonego działania alternatywnego.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto dwóch <xref:System.Threading.Tasks.Task> wystąpienia, aby dodać niektóre elementy pod kątem <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jednocześnie, a następnie generuje całą zawartość, aby pokazać, że elementy zostały pomyślnie dodane. W przykładzie pokazano również sposób użycia <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, i <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> metody dodawania, aktualizacji i pobierania elementów z kolekcji.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jest przeznaczona dla scenariuszy wielowątkowych. Nie trzeba stosować blokady w kodzie, aby dodać lub usunąć elementy z kolekcji. Jednak zawsze jest możliwe dla jednego wątku do pobierania wartości, a inny wątek można natychmiast zaktualizować kolekcji, zapewniając tym samym kluczem nową wartość.  
  
 Ponadto mimo że wszystkie metody <xref:System.Collections.Concurrent.ConcurrentDictionary%602> są wątkowo, nie wszystkie metody są niepodzielne, w szczególności <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>. Pełnomocnika użytkownika, który jest przekazywany do tych metod zostanie wywołana poza słownika blokady wewnętrzne (w ten sposób zapobiec blokuje wszystkie wątki w nieznanym kodzie). W związku z tym możliwe jest dla tej sekwencji zdarzenia:  
  
 1\) wywołania threadA <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>żadnego elementu znajduje i tworzy nowy element do dodania, wywołując delegata valueFactory.  
  
 2\) wywołania threadB <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> współbieżnie, jego valueFactory obiekt delegowany jest wywoływany dociera wewnętrznego blokady przed threadA i dlatego jego nową parę klucz wartość zostanie dodany do słownika.  
  
 3\) pełnomocnika użytkownika threadA firmy zostanie zakończone i wątku dociera blokady, ale teraz widzi, że element już istnieje.  
  
 4\) threadA wykonuje "Get" i zwraca dane, które zostało dodane wcześniej threadB.  
  
 W związku z tym, nie jest masz gwarancję, że dane, który jest zwracany przez <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> to te same dane, które zostało utworzone przez valueFactory wątku. Podobne sekwencję zdarzeń mogą wystąpić podczas <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> jest wywoływana.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
