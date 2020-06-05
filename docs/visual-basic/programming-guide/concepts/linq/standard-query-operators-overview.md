---
title: Standardowe operatory zapytań — Omówienie
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 7c229a576f6695282473352d6253d2c699c76604
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406784"
---
# <a name="standard-query-operators-overview-visual-basic"></a>Standardowe operatory zapytań — Omówienie (Visual Basic)

*Standardowe operatory zapytań* to metody, które tworzą wzorzec LINQ. Większość z tych metod operuje na sekwencjach, gdzie sekwencja jest obiektem, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejs lub <xref:System.Linq.IQueryable%601> interfejs. Standardowe operatory zapytań zapewniają możliwości zapytań, w tym filtrowanie, projekcję, agregację, sortowanie i inne.

Istnieją dwa zestawy operatorów standardowych zapytań LINQ, które działają na obiektach typu <xref:System.Collections.Generic.IEnumerable%601> i innych, które działają na obiektach typu <xref:System.Linq.IQueryable%601> . Metody, które składają się na każdy zestaw są statycznymi elementami członkowskimi <xref:System.Linq.Enumerable> <xref:System.Linq.Queryable> klas i, odpowiednio. Są one definiowane jako *metody rozszerzające* typ, na którym działają. Oznacza to, że można je wywołać za pomocą składni metody statycznej lub składni metody wystąpienia.

Ponadto kilka metod standardowego operatora zapytań działa na typach innych niż te oparte na <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Linq.IQueryable%601> . <xref:System.Linq.Enumerable>Typ definiuje dwie takie metody, które działają na obiektach typu <xref:System.Collections.IEnumerable> . Te metody <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> i <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> umożliwiają włączenie kolekcji niesparametryzowanej lub nieogólnej, w której będą wysyłane zapytania we wzorcu LINQ. W tym celu należy utworzyć kolekcję obiektów o jednoznacznie określonym typie. <xref:System.Linq.Queryable>Klasa definiuje dwie podobne metody, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> które działają na obiektach typu <xref:System.Linq.Queryable> .

Standardowe operatory zapytań różnią się w czasie wykonywania, w zależności od tego, czy zwracają wartość singleton, czy sekwencję wartości. Metody, które zwracają pojedyncze wartości (na przykład <xref:System.Linq.Enumerable.Average%2A> i), <xref:System.Linq.Enumerable.Sum%2A> wykonują od razu. Metody, które zwracają sekwencję, opóźniają wykonanie zapytania i zwracają wyliczalny obiekt.

W przypadku metod, które działają na kolekcjach w pamięci, czyli te metody, które przechodzą <xref:System.Collections.Generic.IEnumerable%601> , zwracany wyliczalny obiekt przechwytuje argumenty, które zostały przekazane do metody. Po wyliczeniu tego obiektu jest stosowana logika operatora zapytania, a wyniki zapytania są zwracane.

W przeciwieństwie do metod, które zwiększają <xref:System.Linq.IQueryable%601> nie zaimplementować żadnego zachowania zapytania, ale kompiluje drzewo wyrażenia, które reprezentuje zapytanie, które ma zostać wykonane. Przetwarzanie zapytania jest obsługiwane przez <xref:System.Linq.IQueryable%601> obiekt źródłowy.

Wywołania metod zapytania można łączyć razem w jednym zapytaniu, co umożliwia zapełnienie zapytań.

Poniższy przykład kodu demonstruje, jak standardowe operatory zapytań mogą służyć do uzyskiwania informacji o sekwencji.

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

Niektóre z często używanych standardowych operatorów zapytań mają dedykowaną składnię słowa kluczowego języka C# i Visual Basic, która umożliwia ich wywoływanie jako część *query* *wyrażenia*zapytania. Aby uzyskać więcej informacji na temat standardowych operatorów zapytań, które mają dedykowane słowa kluczowe i ich odpowiednie składnie, zobacz [składnia wyrażeń zapytania dla standardowych operatorów zapytań (Visual Basic)](query-expression-syntax-for-standard-query-operators.md).

## <a name="extending-the-standard-query-operators"></a>Rozszerzanie standardowych operatorów zapytań

Zestaw standardowych operatorów zapytań można rozszerzyć przez utworzenie metod specyficznych dla domeny, które są odpowiednie dla domeny docelowej lub technologii. Możesz również zastąpić standardowe operatory zapytań własnymi implementacjami, które zapewniają dodatkowe usługi, takie jak Ocena zdalna, tłumaczenie zapytań i optymalizacja. Zobacz <xref:System.Linq.Enumerable.AsEnumerable%2A> , aby zapoznać się z przykładem.

## <a name="related-sections"></a>Sekcje pokrewne

Poniższe linki prowadzą do tematów, które dostarczają dodatkowych informacji na temat różnych standardowych operatorów zapytań opartych na funkcjonalności.

- [Sortowanie danych](sorting-data.md)

- [Operacje Set (Visual Basic)](set-operations.md)

- [Filtrowanie danych (Visual Basic)](filtering-data.md)

- [Operacje kwantyfikatora (Visual Basic)](quantifier-operations.md)

- [Operacje projekcji (Visual Basic)](projection-operations.md)

- [Partycjonowanie danych (Visual Basic)](partitioning-data.md)

- [Operacje join (Visual Basic)](join-operations.md)

- [Grupowanie danych (Visual Basic)](grouping-data.md)

- [Operacje generacji (Visual Basic)](generation-operations.md)

- [Operacje równości (Visual Basic)](equality-operations.md)

- [Operacje elementu (Visual Basic)](element-operations.md)

- [Konwertowanie typów danych (Visual Basic)](converting-data-types.md)

- [Operacje łączenia (Visual Basic)](concatenation-operations.md)

- [Operacje agregacji (Visual Basic)](aggregation-operations.md)

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [Wprowadzenie do LINQ (Visual Basic)](introduction-to-linq.md)
- [Składnia wyrażenia zapytania dla standardowych operatorów zapytań (Visual Basic)](query-expression-syntax-for-standard-query-operators.md)
- [Klasyfikacja standardowych operatorów zapytań według sposobu wykonywania (Visual Basic)](classification-of-standard-query-operators-by-manner-of-execution.md)
- [Metody rozszerzające](../../language-features/procedures/extension-methods.md)
