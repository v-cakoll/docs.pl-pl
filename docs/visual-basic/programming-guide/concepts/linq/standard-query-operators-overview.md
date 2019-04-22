---
title: Omówienie operatorów standardowej kwerendy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 9bfdf2163be52d9016a800d65006bbc4fbf560a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841475"
---
# <a name="standard-query-operators-overview-visual-basic"></a>Omówienie operatorów standardowej kwerendy (Visual Basic)
*Standardowych operatorów zapytań* metod, które tworzą wzorzec LINQ. Większość z tych metod działają na sekwencje, gdzie sekwencji jest obiektem, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub <xref:System.Linq.IQueryable%601> interfejsu. Standardowe operatory zapytań zapewniają możliwości zapytania, takie jak filtrowanie, projekcji, agregacji, sortowania i innych.  
  
 Istnieją dwa zestawy LINQ standardowych operatorów zapytań, który działa na obiekty typu <xref:System.Collections.Generic.IEnumerable%601> i inne, która operuje na obiekty typu <xref:System.Linq.IQueryable%601>. Metody, które tworzą każdego zestawu są statyczne elementy członkowskie <xref:System.Linq.Enumerable> i <xref:System.Linq.Queryable> klasy, odpowiednio. Są one definiowane jako *metody rozszerzenia* typu, które działają na. Oznacza to, że może być wywoływana przy użyciu składni metody statyczne lub składni metody wystąpienia.  
  
 Ponadto kilka metod standardowych operatorów zapytań działać dla typów innych niż te, na podstawie <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601>. <xref:System.Linq.Enumerable> Typ definiuje dwa takie metody że działają zarówno w obiektach typu <xref:System.Collections.IEnumerable>. Te metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> i <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>systemowi włączysz bez parametrów lub inną niż ogólna kolekcję we wzorcu LINQ. Mogą to zrobić, tworząc silnie typizowaną kolekcją obiektów. <xref:System.Linq.Queryable> Klasa definiuje dwie podobne metody, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> i <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, które działają na obiektach typu <xref:System.Linq.Queryable>.  
  
 Standardowe operatory zapytań różnią się w odniesieniu do momentu ich wykonania, w zależności od tego, czy zwracać wartości pojedynczego wystąpienia lub je sekvence hodnot. Te metody, które zwracają wartości pojedynczego wystąpienia (na przykład <xref:System.Linq.Enumerable.Average%2A> i <xref:System.Linq.Enumerable.Sum%2A>) od razu. Metody, które zwracają sekwencji odroczone do wykonywania zapytania i zwraca obiekt wyliczalny.  
  
 W przypadku metod, które pracują na kolekcji w pamięci, oznacza to, że te metody, które rozszerzają <xref:System.Collections.Generic.IEnumerable%601>, zwracany obiekt wyliczalny przechwytuje argumenty, które zostały przekazane do metody. Gdy ten obiekt jest zostanie wyliczonly, logika — operator zapytań są stosowane, a wyniki zapytania są zwracane.  
  
 Z kolei metody które rozszerzają <xref:System.Linq.IQueryable%601> nie implementuje żadnych zapytań zachowania, ale tworzenie drzewo wyrażenia, które reprezentuje zapytanie, które mają zostać wykonane. Przetwarzanie zapytań odbywa się przez źródło <xref:System.Linq.IQueryable%601> obiektu.  
  
 Wywołania do metody zapytania można łączyć w łańcuch w jednym zapytaniu, co umożliwia zapytania, aby stać się dowolnie złożone.  
  
 Poniższy przykład kodu pokazuje, jak standardowe operatory zapytań może służyć do uzyskiwania informacji na temat sekwencji.  
  
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
 Niektóre z często używanych standardowych operatorów zapytań są wyposażone w dedykowane języka C# i Visual Basic składni — słowo kluczowe języka, który pozwoli na można wywołać w ramach *zapytania* *wyrażenie*. Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, które są wyposażone w dedykowane słów kluczowych i ich odpowiedniej składni zobacz [składnia wyrażeń dla standardowych operatorów zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Rozszerzenie standardowych operatorów zapytań  
 Zbiór standardowych operatorów zapytań można rozszerzyć, aby utworzyć metody specyficznego dla domeny, które są odpowiednie dla Twojej domeny docelowej lub technologii. Możesz również zastąpić standardowych operatorów zapytań Twojej własnej implementacji, które zapewnia dodatkowe usługi, takie jak zdalne oceny, translacji zapytania i optymalizacji. Zobacz <xref:System.Linq.Enumerable.AsEnumerable%2A> przykład.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Poniższe łącza prowadzą do tematów, które zapewniają dodatkowe informacje na temat różnych standardowych operatorów zapytań w oparciu o funkcjonalność.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Wprowadzenie do LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [Składnia wyrażeń dla standardowych operatorów zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [Klasyfikacja standardowych operatorów zapytań w oparciu o sposób działania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
- [Metody rozszerzeń](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
