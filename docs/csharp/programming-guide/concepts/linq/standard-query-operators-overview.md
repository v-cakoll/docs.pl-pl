---
title: Standardowe operatory zapytań — Omówienie (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 16ab04e774e6654ce67a8c1d1c5a743c999958ff
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201307"
---
# <a name="standard-query-operators-overview-c"></a>Standardowe operatory zapytań — Omówienie (C#)
*Standardowe operatory zapytań* to metody, które tworzą wzorzec LINQ. Większość z tych metod operuje na sekwencjach, gdzie sekwencja jest obiektem, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejs lub <xref:System.Linq.IQueryable%601> interfejs. Standardowe operatory zapytań zapewniają możliwości zapytań, w tym filtrowanie, projekcję, agregację, sortowanie i inne.  
  
 Istnieją dwa zestawy operatorów standardowych zapytań LINQ, które działają na obiektach typu <xref:System.Collections.Generic.IEnumerable%601> i innych, które działają na obiektach typu <xref:System.Linq.IQueryable%601> . Metody, które składają się na każdy zestaw są statycznymi elementami członkowskimi <xref:System.Linq.Enumerable> <xref:System.Linq.Queryable> klas i, odpowiednio. Są one definiowane jako *metody rozszerzające* typ, na którym działają. Oznacza to, że można je wywołać za pomocą składni metody statycznej lub składni metody wystąpienia.  
  
 Ponadto kilka metod standardowego operatora zapytań działa na typach innych niż te oparte na <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601> . <xref:System.Linq.Enumerable>Typ definiuje dwie takie metody, które działają na obiektach typu <xref:System.Collections.IEnumerable> . Te metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> i <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> umożliwiają włączenie kolekcji niesparametryzowanej lub nieogólnej, w której będą wysyłane zapytania we wzorcu LINQ. W tym celu należy utworzyć kolekcję obiektów o jednoznacznie określonym typie. <xref:System.Linq.Queryable>Klasa definiuje dwie podobne metody, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> które działają na obiektach typu <xref:System.Linq.Queryable> .  
  
 Standardowe operatory zapytań różnią się w czasie wykonywania, w zależności od tego, czy zwracają wartość singleton, czy sekwencję wartości. Metody, które zwracają pojedyncze wartości (na przykład <xref:System.Linq.Enumerable.Average%2A> i), <xref:System.Linq.Enumerable.Sum%2A> wykonują od razu. Metody, które zwracają sekwencję, opóźniają wykonanie zapytania i zwracają wyliczalny obiekt.  
  
 W przypadku metod, które działają na kolekcjach w pamięci, czyli te metody, które przechodzą <xref:System.Collections.Generic.IEnumerable%601> , zwracany wyliczalny obiekt przechwytuje argumenty, które zostały przekazane do metody. Po wyliczeniu tego obiektu jest stosowana logika operatora zapytania, a wyniki zapytania są zwracane.  
  
 W przeciwieństwie do metod, które zwiększają <xref:System.Linq.IQueryable%601> nie zaimplementować żadnego zachowania zapytania, ale kompiluje drzewo wyrażenia, które reprezentuje zapytanie, które ma zostać wykonane. Przetwarzanie zapytania jest obsługiwane przez <xref:System.Linq.IQueryable%601> obiekt źródłowy.  
  
 Wywołania metod zapytania można łączyć razem w jednym zapytaniu, co umożliwia zapełnienie zapytań.  
  
 Poniższy przykład kodu demonstruje, jak standardowe operatory zapytań mogą służyć do uzyskiwania informacji o sekwencji.  
  
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
  
## <a name="query-expression-syntax"></a>Składnia wyrażenia zapytania  
 Niektóre z często używanych standardowych operatorów zapytań mają dedykowaną składnię słowa kluczowego języka C# i Visual Basic, która umożliwia ich wywoływanie jako część *query* *wyrażenia*zapytania. Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, które mają dedykowane słowa kluczowe i ich odpowiednie składnie, zobacz [składnia wyrażeń zapytania dla standardowych operatorów zapytań (C#)](./query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Rozszerzanie standardowych operatorów zapytań  
 Zestaw standardowych operatorów zapytań można rozszerzyć przez utworzenie metod specyficznych dla domeny, które są odpowiednie dla domeny docelowej lub technologii. Możesz również zastąpić standardowe operatory zapytań własnymi implementacjami, które zapewniają dodatkowe usługi, takie jak Ocena zdalna, tłumaczenie zapytań i optymalizacja. Zobacz <xref:System.Linq.Enumerable.AsEnumerable%2A> , aby zapoznać się z przykładem.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Poniższe linki prowadzą do tematów, które dostarczają dodatkowych informacji na temat różnych standardowych operatorów zapytań opartych na funkcjonalności.  
  
 [Sortowanie danych (C#)](./sorting-data.md)  
  
 [Operacje Set (C#)](./set-operations.md)  
  
 [Filtrowanie danych (C#)](./filtering-data.md)  
  
 [Operacje kwantyfikatora (C#)](./quantifier-operations.md)  
  
 [Operacje projekcji (C#)](./projection-operations.md)  
  
 [Partycjonowanie danych (C#)](./partitioning-data.md)  
  
 [Operacje join (C#)](./join-operations.md)  
  
 [Grupowanie danych (C#)](./grouping-data.md)  
  
 [Operacje generacji (C#)](./generation-operations.md)  
  
 [Operacje równości (C#)](./equality-operations.md)  
  
 [Operacje na elementach (C#)](./element-operations.md)  
  
 [Konwertowanie typów danych (C#)](./converting-data-types.md)  
  
 [Operacje łączenia (C#)](./concatenation-operations.md)  
  
 [Operacje agregacji (C#)](./aggregation-operations.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Wprowadzenie do kwerend LINQ (C#)](./introduction-to-linq-queries.md)
- [Składnia wyrażenia zapytania dla standardowych operatorów zapytań (C#)](./query-expression-syntax-for-standard-query-operators.md)
- [Klasyfikacja standardowych operatorów zapytań według sposobu wykonywania (C#)](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [Metody rozszerzania](../../classes-and-structs/extension-methods.md)
