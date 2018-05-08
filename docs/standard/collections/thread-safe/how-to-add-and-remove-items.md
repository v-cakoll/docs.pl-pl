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
ms.openlocfilehash: 6aa309f2c6c44934f491229ac43003a05301bacb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a>Porady: dodawanie i usuwanie elementów ConcurrentDictionary
W tym przykładzie pokazano, jak dodać, pobierania, aktualizowanie i usuwanie elementów z <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>. Ta klasa kolekcji jest implementacją wątkowo. Zaleca się używania jej w każdym przypadku, gdy wiele wątków może próby uzyskania dostępu do elementów jednocześnie.  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> zapewnia kilka metod wygody wchodzące niepotrzebnych kodu najpierw sprawdź, czy istnieje klucz przed próbuje dodać lub usunąć dane. Poniższej tabeli wymieniono te metody wygody oraz opis ich użycie.  
  
|Metoda|Używany, gdy...|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|Aby dodać nową wartość dla określonego klucza i, jeśli klucz już istnieje, chcesz zastąpić jej wartość.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|Chcesz pobrać istniejące wartości dla określonego klucza i, jeśli klucz nie istnieje, ma zostać określone pary klucza/wartości.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A>|Chcesz dodać, get, zaktualizować lub usunąć pary klucz wartość, a jeśli klucz już istnieje lub próba nie powiedzie się z jakiegokolwiek powodu, chcesz wykonać niektóre akcje, alternatywnych.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto dwóch <xref:System.Threading.Tasks.Task> wystąpień, aby dodać niektóre elementy do <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jednocześnie, a następnie wyświetla całą zawartość, aby pokazać, że elementy nie zostały dodane pomyślnie. W przykładzie przedstawiono również sposób użycia <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, i <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> metody dodawania, aktualizacji i pobierania elementów z kolekcji.  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jest przeznaczony do scenariuszy wielowątkowych. Nie trzeba stosować blokady w kodzie, aby dodać lub usunąć elementy z kolekcji. Jednak zawsze jest jeden wątek, aby pobrać wartości i inny wątek natychmiast zaktualizować kolekcji, zapewniając nową wartość w taki sam klucz.  
  
 Ponadto mimo że wszystkie metody <xref:System.Collections.Concurrent.ConcurrentDictionary%602> są wątkowo, nie wszystkie metody są atomic, w szczególności <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>. Delegowanie użytkownika, który jest przekazywany do tych metod jest wywoływany poza słownik wewnętrzny blokady. (Jest to na celu zapobieganie blokuje wszystkie wątki nieznany kod.) Dlatego możliwe jest dla tej sekwencji zdarzenia:  
  
 1\) wywołania threadA <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, znajdzie żadnego elementu i tworzy nowy element do dodania, wywołując delegata obiekt valueFactory.  
  
 2\) wywołania threadB <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> jednocześnie, swojego delegata obiekt valueFactory jest wywoływana dociera wewnętrzny blokady przed threadA i dlatego jego nowej pary klucz wartość zostanie dodany do słownika.  
  
 3\) ukończeniu delegowanie użytkownika w threadA i Wątek dociera blokady, ale teraz widzi element już istnieje  
  
 4\) threadA wykonuje procedurę "Get" i zwraca dane, które zostało dodane wcześniej threadB.  
  
 W związku z tym nie jest gwarancję, że dane, który jest zwracany przez <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> jest tych samych danych, który został utworzony przez obiekt valueFactory wątku. Podobne sekwencję zdarzeń, może wystąpić podczas <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Kolekcje bezpieczne wątkowo](../../../../docs/standard/collections/thread-safe/index.md)
