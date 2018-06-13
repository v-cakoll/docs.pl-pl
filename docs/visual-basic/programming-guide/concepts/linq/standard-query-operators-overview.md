---
title: Operatory standardowe zapytań — omówienie (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 27b144ae75054dbdc535b6ad894e4a5a0b8529e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653575"
---
# <a name="standard-query-operators-overview-visual-basic"></a>Operatory standardowe zapytań — omówienie (Visual Basic)
*Standardowych operatorów zapytań* metod, które tworzą wzorzec LINQ. Większość tych metod działają w sekwencji, w którym sekwencja jest obiekt, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub <xref:System.Linq.IQueryable%601> interfejsu. Standardowe operatory zapytań zapewniają możliwość wykonywania kwerend włącznie z filtrowaniem projekcji, agregacji, sortowania i inne.  
  
 Istnieją dwa zestawy LINQ standardowych operatorów zapytań, który działa na obiektach typu <xref:System.Collections.Generic.IEnumerable%601> i inne, który działa na obiektach typu <xref:System.Linq.IQueryable%601>. Statyczne elementy członkowskie są metody, wchodzące w skład każdego zestawu <xref:System.Linq.Enumerable> i <xref:System.Linq.Queryable> klasy odpowiednio. Są one zdefiniowane jako *metody rozszerzenia* typu, które działają na. Oznacza to, że może być wywoływana za pomocą składni metody statycznej lub składnia metody wystąpienia.  
  
 Ponadto kilka metod operator zapytania standardowe działania dla typów innych niż te, na podstawie <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>. <xref:System.Linq.Enumerable> Typ definiuje dwie metody takie że działają zarówno na obiektach typu <xref:System.Collections.IEnumerable>. Te metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> i <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, pozwalają włączyć bez parametrów lub inny niż ogólny kolekcji w wzorcu LINQ. Do tworzenia kolekcji silnie typizowanych obiektów. <xref:System.Linq.Queryable> Klasy definiuje dwie metody podobne, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> i <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, które działają na obiektach typu <xref:System.Linq.Queryable>.  
  
 Standardowe operatory zapytań różnią się czas ich działania, w zależności od tego, czy zwracać wartość pojedynczą lub sekwencję wartości. Te metody, które zwracają wartości pojedynczego wystąpienia (na przykład <xref:System.Linq.Enumerable.Average%2A> i <xref:System.Linq.Enumerable.Sum%2A>) wykonaj natychmiast. Metody zwracające sekwencję wstrzymuje wykonywanie zapytania i zwracać obiekt wyliczalny.  
  
 W przypadku metod, które pracują na kolekcje w pamięci, czyli tych metod, które rozszerzają <xref:System.Collections.Generic.IEnumerable%601>, zwrócony obiekt wyliczalny przechwytuje argumenty, które zostały przekazane do metody. Po wyliczeniu tego obiektu jest zastosować logiki — operator zapytań i są zwracane wyniki zapytania.  
  
 Z kolei metody który rozszerzyć <xref:System.Linq.IQueryable%601> nie implementuje wszystkie zachowania podczas badania, ale kompilacji drzewo wyrażenia, które reprezentuje zapytanie do wykonania. Przetwarzanie zapytania jest obsługiwane przez źródło <xref:System.Linq.IQueryable%601> obiektu.  
  
 Wywołania metod zapytania można połączyć ze sobą w jednym zapytaniu, dzięki czemu staną się arbitralnie złożonych zapytań.  
  
 W poniższym przykładzie kodu pokazano, jak standardowe operatory kwerend może służyć do uzyskiwania informacji o sekwencji.  
  
```vb  
Dim sentence = "the quick brown fox jumps over the lazy dog"  
' Split the string into individual words to create a collection.  
Dim words = sentence.Split(" "c)  
  
Dim query = From word In words   
            Group word.ToUpper() By word.Length Into gr = Group   
            Order By Length _  
            Select Length, GroupedWords = gr  
  
Dim output As New System.Text.StringBuilder  
For Each obj In query  
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))  
    For Each word As String In obj.GroupedWords  
        output.AppendLine(word)  
    Next  
Next  
  
'Display the output  
MsgBox(output.ToString())  
  
' This code example produces the following output:  
'  
' Words of length 3:  
' THE  
' FOX  
' THE  
' DOG  
' Words of length 4:  
' OVER  
' LAZY  
' Words of length 5:  
' QUICK  
' BROWN  
' JUMPS   
```  
  
## <a name="query-expression-syntax"></a>Składnia wyrażenia zapytania  
 Niektóre z często używanych standardowych operatorów zapytań są wyposażone w dedykowane C# i Visual Basic składni słowa kluczowego języka, umożliwiający ich można wywołać w ramach *zapytania* *wyrażenia*. Aby uzyskać więcej informacji o standardowych operatorów zapytań, które są wyposażone w dedykowane słów kluczowych i ich odpowiedniej składni, zobacz [składnia wyrażeń dla standardowych operatorów zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Rozszerzenie standardowych operatorów zapytań  
 Zbiór standardowych operatorów zapytań można rozszerzyć, aby tworzenie metod specyficznego dla domeny, które są odpowiednie dla Twojej domeny docelowej lub technologii. Standardowe operatory zapytań można także zastąpić własne implementacje, które udostępniają dodatkowe usługi, takie jak zdalne oceny, translacja zapytania i optymalizacji. Zobacz <xref:System.Linq.Enumerable.AsEnumerable%2A> przykład.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Poniższe łącza prowadzą do tematów zawierających dodatkowe informacje na temat różnych standardowych operatorów zapytań w oparciu o funkcje.  
  
 [Sortowanie danych](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [Operacje na zestawie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [Filtrowanie danych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [Operacje kwantyfikatora (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [Operacje rzutowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [Partycjonowanie danych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [Dołącz do operacji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [Grupowanie danych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [Operacje generowania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [Operacje równości (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [Operacje na elementach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [Konwertowanie typów danych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [Operacje łączenia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [Operacje agregacji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [Wprowadzenie do LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 [Składnia wyrażeń dla standardowych operatorów zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [Klasyfikacja standardowych operatorów zapytań w oparciu o sposób działania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [Metody rozszerzeń](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
