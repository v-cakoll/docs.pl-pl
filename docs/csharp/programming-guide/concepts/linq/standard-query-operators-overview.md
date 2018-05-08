---
title: Operatory standardowe zapytań — omówienie (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 36bd5927e64ffacb97beac28b8e7790204e08c5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="standard-query-operators-overview-c"></a>Operatory standardowe zapytań — omówienie (C#)
*Standardowych operatorów zapytań* metod, które tworzą wzorzec LINQ. Większość tych metod działają w sekwencji, w którym sekwencja jest obiekt, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub <xref:System.Linq.IQueryable%601> interfejsu. Standardowe operatory zapytań zapewniają możliwość wykonywania kwerend włącznie z filtrowaniem projekcji, agregacji, sortowania i inne.  
  
 Istnieją dwa zestawy LINQ standardowych operatorów zapytań, który działa na obiektach typu <xref:System.Collections.Generic.IEnumerable%601> i inne, który działa na obiektach typu <xref:System.Linq.IQueryable%601>. Statyczne elementy członkowskie są metody, wchodzące w skład każdego zestawu <xref:System.Linq.Enumerable> i <xref:System.Linq.Queryable> klasy odpowiednio. Są one zdefiniowane jako *metody rozszerzenia* typu, które działają na. Oznacza to, że może być wywoływana za pomocą składni metody statycznej lub składnia metody wystąpienia.  
  
 Ponadto kilka metod operator zapytania standardowe działania dla typów innych niż te, na podstawie <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>. <xref:System.Linq.Enumerable> Typ definiuje dwie metody takie że działają zarówno na obiektach typu <xref:System.Collections.IEnumerable>. Te metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> i <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, pozwalają włączyć bez parametrów lub inny niż ogólny kolekcji w wzorcu LINQ. Do tworzenia kolekcji silnie typizowanych obiektów. <xref:System.Linq.Queryable> Klasy definiuje dwie metody podobne, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> i <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, które działają na obiektach typu <xref:System.Linq.Queryable>.  
  
 Standardowe operatory zapytań różnią się czas ich działania, w zależności od tego, czy zwracać wartość pojedynczą lub sekwencję wartości. Te metody, które zwracają wartości pojedynczego wystąpienia (na przykład <xref:System.Linq.Enumerable.Average%2A> i <xref:System.Linq.Enumerable.Sum%2A>) wykonaj natychmiast. Metody zwracające sekwencję wstrzymuje wykonywanie zapytania i zwracać obiekt wyliczalny.  
  
 W przypadku metod, które pracują na kolekcje w pamięci, czyli tych metod, które rozszerzają <xref:System.Collections.Generic.IEnumerable%601>, zwrócony obiekt wyliczalny przechwytuje argumenty, które zostały przekazane do metody. Po wyliczeniu tego obiektu jest zastosować logiki — operator zapytań i są zwracane wyniki zapytania.  
  
 Z kolei metody który rozszerzyć <xref:System.Linq.IQueryable%601> nie implementuje wszystkie zachowania podczas badania, ale kompilacji drzewo wyrażenia, które reprezentuje zapytanie do wykonania. Przetwarzanie zapytania jest obsługiwane przez źródło <xref:System.Linq.IQueryable%601> obiektu.  
  
 Wywołania metod zapytania można połączyć ze sobą w jednym zapytaniu, dzięki czemu staną się arbitralnie złożonych zapytań.  
  
 W poniższym przykładzie kodu pokazano, jak standardowe operatory kwerend może służyć do uzyskiwania informacji o sekwencji.  
  
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
 Niektóre z często używanych standardowych operatorów zapytań są wyposażone w dedykowane C# i Visual Basic składni słowa kluczowego języka, umożliwiający ich można wywołać w ramach *zapytania* *wyrażenia*. Aby uzyskać więcej informacji o standardowych operatorów zapytań, które są wyposażone w dedykowane słów kluczowych i ich odpowiedniej składni, zobacz [składnia wyrażeń dla standardowych operatorów zapytań (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Rozszerzenie standardowych operatorów zapytań  
 Zbiór standardowych operatorów zapytań można rozszerzyć, aby tworzenie metod specyficznego dla domeny, które są odpowiednie dla Twojej domeny docelowej lub technologii. Standardowe operatory zapytań można także zastąpić własne implementacje, które udostępniają dodatkowe usługi, takie jak zdalne oceny, translacja zapytania i optymalizacji. Zobacz <xref:System.Linq.Enumerable.AsEnumerable%2A> przykład.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Poniższe łącza prowadzą do tematów zawierających dodatkowe informacje na temat różnych standardowych operatorów zapytań w oparciu o funkcje.  
  
 [Sortowanie danych (C#)](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [Operacje na zestawie (C#)](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [Filtrowanie danych (C#)](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [Operacje kwantyfikatora (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [Operacje rzutowania (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [Partycjonowanie danych (C#)](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [Dołącz do operacji (C#)](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [Grupowanie danych (C#)](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [Operacje generowania (C#)](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [Operacje równości (C#)](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [Operacje na elementach (C#)](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [Konwertowanie typów danych (C#)](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [Operacje łączenia (C#)](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [Operacje agregacji (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [Wprowadzenie do kwerend LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [Składnia wyrażeń dla standardowych operatorów zapytań (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [Klasyfikacja standardowych operatorów zapytań w oparciu o sposób działania (C#)](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [Metody rozszerzeń](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
