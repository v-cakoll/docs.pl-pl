---
title: Omówienie standardowych operatorów zapytań (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 76c2c4684f33c3fb30748b5f08efd215548661ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167858"
---
# <a name="standard-query-operators-overview-c"></a>Omówienie standardowych operatorów zapytań (C#)
*Standardowe operatory zapytań* są metody, które tworzą wzorzec LINQ. Większość z tych metod działa na sekwencje, gdzie sekwencja <xref:System.Collections.Generic.IEnumerable%601> jest obiektem, którego typ implementuje interfejs lub <xref:System.Linq.IQueryable%601> interfejs. Standardowe operatory zapytań zapewniają możliwości zapytania, w tym filtrowanie, projekcję, agregację, sortowanie i inne.  
  
 Istnieją dwa zestawy operatorów standardowych zapytań LINQ, jeden, który działa na obiektach typu, <xref:System.Collections.Generic.IEnumerable%601> a drugi działa na obiektach typu <xref:System.Linq.IQueryable%601>. Metody, które tworzą każdy zestaw są <xref:System.Linq.Enumerable> statyczne <xref:System.Linq.Queryable> elementy członkowskie i klas, odpowiednio. Są one zdefiniowane jako *metody rozszerzenia* typu, na których działają. Oznacza to, że można je wywołać przy użyciu składni metody statycznej lub składni metody wystąpienia.  
  
 Ponadto kilka standardowych metod operatorkwerendy działają na typach innych niż te oparte na <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>. Typ <xref:System.Linq.Enumerable> definiuje dwie takie metody, które działają <xref:System.Collections.IEnumerable>na obiektach typu . Te metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> i <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, pozwalają włączyć nieparametryzowane lub nieogólne, kolekcja, które mają być badane w wzorzec LINQ. Robią to, tworząc silnie typizyszoną kolekcję obiektów. Klasa <xref:System.Linq.Queryable> definiuje dwie podobne metody <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>i , które działają <xref:System.Linq.Queryable>na obiektach typu .  
  
 Operatory standardowych zapytań różnią się w czasie ich wykonywania, w zależności od tego, czy zwracają one wartość singleton lub sekwencji wartości. Te metody, które zwracają wartość singleton <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Sum%2A>(na przykład i ) wykonać natychmiast. Metody, które zwracają sekwencję odroczyć wykonanie kwerendy i zwrócić wyliczany obiekt.  
  
 W przypadku metod, które działają na kolekcje w pamięci, to <xref:System.Collections.Generic.IEnumerable%601>znaczy te metody, które rozszerzają , zwracany obiekt wyliczany przechwytuje argumenty, które zostały przekazane do metody. Po wyliczeniu tego obiektu jest stosowana logika operatora kwerendy i zwracane są wyniki kwerendy.  
  
 Natomiast metody, które <xref:System.Linq.IQueryable%601> rozszerzają nie implementują żadnego zachowania zapytań, ale tworzą drzewo wyrażeń, które reprezentuje kwerendę do wykonania. Przetwarzanie zapytań jest obsługiwane <xref:System.Linq.IQueryable%601> przez obiekt źródłowy.  
  
 Wywołania metod kwerendy można połączyć ze sobą w jedną kwerendę, co umożliwia kwerendy stają się arbitralnie złożone.  
  
 Poniższy przykład kodu pokazuje, jak standardowe operatory zapytań mogą służyć do uzyskiwania informacji o sekwencji.  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS
```  
  
## <a name="query-expression-syntax"></a>Składnia wyrażenia kwerendy  
 Niektóre z najczęściej używanych standardowych operatorów zapytań mają dedykowaną składnię słów kluczowych języka Języka C# i Języka Visual Basic, która umożliwia wywoływanie ich jako część *wyrażenia* *zapytania.* Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, które mają dedykowane słowa kluczowe i odpowiadające im składnie, zobacz [Składnia wyrażeń zapytań dla standardowych operatorów zapytań (C#).](./query-expression-syntax-for-standard-query-operators.md)  
  
## <a name="extending-the-standard-query-operators"></a>Rozszerzanie standardowych operatorów zapytań  
 Zestaw standardowych operatorów zapytań można rozszerzyć, tworząc metody specyficzne dla domeny, które są odpowiednie dla domeny docelowej lub technologii. Można również zastąpić standardowych operatorów zapytań z własnych implementacji, które zapewniają dodatkowe usługi, takie jak zdalnej oceny, tłumaczenia zapytań i optymalizacji. Zobacz <xref:System.Linq.Enumerable.AsEnumerable%2A> przykład.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Poniższe łącza prowadzą do tematów, które zawierają dodatkowe informacje na temat różnych standardowych operatorów zapytań na podstawie funkcji.  
  
 [Sortowanie danych (C#)](./sorting-data.md)  
  
 [Ustawianie operacji (C#)](./set-operations.md)  
  
 [Filtrowanie danych (C#)](./filtering-data.md)  
  
 [Operacje kwantyfikatora (C#)](./quantifier-operations.md)  
  
 [Operacje projekcji (C#)](./projection-operations.md)  
  
 [Partycjonowanie danych (C#)](./partitioning-data.md)  
  
 [Dołącz do operacji (C#)](./join-operations.md)  
  
 [Grupowanie danych (C#)](./grouping-data.md)  
  
 [Operacje wytwarzania (C#)](./generation-operations.md)  
  
 [Operacje równości (C#)](./equality-operations.md)  
  
 [Operacje elementów (C#)](./element-operations.md)  
  
 [Konwertowanie typów danych (C#)](./converting-data-types.md)  
  
 [Operacje łączenia (C#)](./concatenation-operations.md)  
  
 [Operacje agregacji (C#)](./aggregation-operations.md)  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Wprowadzenie do kwerend LINQ (C#)](./introduction-to-linq-queries.md)
- [Składnia wyrażenia kwerendy dla standardowych operatorów kwerend (C#)](./query-expression-syntax-for-standard-query-operators.md)
- [Klasyfikacja standardowych operatorów zapytań według sposobu wykonania (C#)](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [Metody rozszerzeń](../../classes-and-structs/extension-methods.md)
