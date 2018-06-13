---
title: Aggregate — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 1db4b7fdcf9c8a38c2c49eca9d874eccea90ab1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604903"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate — Klauzula (Visual Basic)
Stosuje co najmniej jeden funkcje agregujące do kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`element`|Wymagana. Zmienna używany do iterowania po elementach kolekcji.|  
|`type`|Opcjonalna. Typ `element`. Jeśli nie określono typu, typu `element` jest wywnioskowany na podstawie `collection`.|  
|`collection`|Wymagana. Odnosi się do kolekcji do działania na.|  
|`clause`|Opcjonalna. Co najmniej jednego zapytania klauzule, takie jak `Where` klauzuli, aby doprecyzować wyniku zapytania, aby zastosować aggregate — klauzula lub klauzule.|  
|`expressionList`|Wymagana. Co najmniej jeden rozdzielana przecinkami wyrażeń określających funkcji agregującej do zastosowania do kolekcji. Alias można stosować do funkcji agregującej, aby określić nazwę elementu członkowskiego wyniku zapytania. Jeśli nie jest dostarczony żadnego aliasu, nazwy funkcji agregującej jest używany. Aby uzyskać przykłady zobacz sekcję funkcje agregujące w dalszej części tego tematu.|  
  
## <a name="remarks"></a>Uwagi  
 `Aggregate` Klauzuli może służyć do uwzględnienia funkcji agregujących w zapytaniach. Funkcje agregujące wykonać kontroli i obliczenia przez zestaw wartości i zwraca pojedynczą wartość. Obliczona wartość mogą korzystać za pomocą elementu członkowskiego typu wyników zapytania. Standardowe funkcje agregujące, których można użyć są `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, i `Sum` funkcji. Te funkcje są znane deweloperom, którzy zapoznali się z wartości zagregowanych SQL. Są one opisane w poniższej sekcji tego tematu.  
  
 Wynik funkcji agregującej znajduje się w wyniku zapytania jako pola typu wyników zapytania. Możesz podać alias dla wyniku funkcji agregującej do określenia nazwy elementu członkowskiego typu wyników zapytania, który będzie przechowywać wartość zagregowaną. Jeśli nie jest dostarczony żadnego aliasu, nazwy funkcji agregującej jest używany.  
  
 `Aggregate` Klauzuli rozpocząć zapytania lub może zostać dołączony jako dodatkową klauzulą w zapytaniu. Jeśli `Aggregate` klauzuli rozpoczyna się zapytanie, wynik jest pojedynczą wartość będącą wynikiem określona w funkcji agregującej `Into` klauzuli. Jeśli określono więcej niż jedną funkcję agregacji w `Into` klauzuli, gdy kwerenda zwraca jednego typu z właściwością oddzielne do odwołują się do wyniku w każdej funkcji agregującej `Into` klauzuli. Jeśli `Aggregate` klauzuli jest uwzględniona jako dodatkową klauzulą w zapytaniu, typ zwracany w kolekcji zapytania ma oddzielne właściwość do odwołują się do wyniku w każdej funkcji agregującej `Into` klauzuli.  
  
## <a name="aggregate-functions"></a>Funkcje agregujące  
 Poniższa lista zawiera standardowe funkcje agregujące, które mogą być używane z `Aggregate` klauzuli.  
  
|Funkcja|Opis|  
|---|---|  
|`All`|Zwraca `true` , gdy wszystkie elementy w kolekcji spełniają określony warunek; w przeciwnym razie zwraca `false`. Poniżej przedstawiono przykładowy:<br /><br /> [!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]|  
|`Any`|Zwraca `true` Jeśli dowolny element w kolekcji spełnia określony warunek; w przeciwnym razie zwraca `false`. Poniżej przedstawiono przykładowy:<br /><br /> [!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]|  
|`Average`|Oblicza średnią wszystkich elementów w kolekcji lub wyrażenia oblicza podane dla wszystkich elementów w kolekcji. Poniżej przedstawiono przykładowy:<br /><br /> [!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]|  
|`Count`|Oblicza liczbę elementów w kolekcji. Możesz podać opcjonalny `Boolean` wyrażenie do obliczenia tylko liczbę elementów w kolekcji, które spełniają warunek. Poniżej przedstawiono przykładowy:<br /><br /> [!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]|  
|`Group`|Odwołuje się do wyników zapytania, które są zgrupowane w `Group By` lub `Group Join` klauzuli. `Group` Funkcja jest prawidłowa tylko w `Into` klauzuli `Group By` lub `Group Join` klauzuli. Aby uzyskać dodatkowe informacje i przykłady, zobacz [grupy przez klauzuli](../../../visual-basic/language-reference/queries/group-by-clause.md) i [klauzuli Join grupy](../../../visual-basic/language-reference/queries/group-join-clause.md).|  
|`LongCount`|Oblicza liczbę elementów w kolekcji. Możesz podać opcjonalny `Boolean` wyrażenie do obliczenia tylko liczbę elementów w kolekcji, które spełniają warunek. Zwraca wynik w postaci `Long`. Na przykład zobacz `Count` funkcję agregacji.|  
|`Max`|Oblicza maksymalną wartość z kolekcji lub oblicza wyrażenie podane dla wszystkich elementów w kolekcji. Poniżej przedstawiono przykładowy:<br /><br /> [!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]|  
|`Min`|Oblicza minimalną wartość z kolekcji lub oblicza wyrażenie podane dla wszystkich elementów w kolekcji. Poniżej przedstawiono przykładowy:<br /><br /> [!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]|  
|`Sum`|Oblicza sumę wszystkich elementów w kolekcji lub oblicza wyrażenie podane dla wszystkich elementów w kolekcji. Poniżej przedstawiono przykładowy:<br /><br /> [!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]|  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób użycia `Aggregate` klauzuli dotyczyć funkcji agregujących w wyniku zapytania.  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Tworzenie funkcji agregujących zdefiniowane przez użytkownika  
 W wyrażeniu zapytania można dołączać własne niestandardowe funkcji agregujących, dodając metody rozszerzenia umożliwiające <xref:System.Collections.Generic.IEnumerable%601> typu. Niestandardowe metodę można wykonywać obliczenia lub operacji w kolekcji wyliczalny, który odwołuje się do funkcji agregujących. Aby uzyskać więcej informacji na temat metody rozszerzenia, zobacz [metody rozszerzenia](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Na przykład następujący przykładowy kod przedstawia niestandardowej funkcji agregującej, która daje w wyniku wartość mediany zbioru liczb. Istnieją dwa przeciążenia metody `Median` — metoda rozszerzenia. Pierwszy przeciążenie akceptuje jako dane wejściowe, kolekcję typu `IEnumerable(Of Double)`. Jeśli `Median` funkcji agregującej jest wywoływana dla pola zapytania typu `Double`, ta metoda zostanie wywołana. Drugi przeciążenia `Median` metody mogą być przekazywane do dowolnego typu ogólnego. Ogólny przeciążenia `Median` metoda przyjmuje drugi parametr, który odwołuje się do `Func(Of T, Double)` wyrażenia lambda do projektu wartość dla typu (z kolekcji) jako wartość odpowiedniego typu `Double`. Następnie deleguje obliczania średniej wartości inne przeciążenia `Median` metody. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 Poniższy kod przykładowy przedstawiono przykładowe zapytania, które wywołują `Median` funkcję na kolekcję typu agregacji `Integer`i kolekcji typu `Double`. Zapytanie, które wywołuje `Median` funkcję na kolekcję typu agregacji `Double` wywołania przeciążenia `Median` metodę, która przyjmuje jako dane wejściowe, kolekcję typu `Double`. Zapytania, który wywołuje `Median` funkcję na kolekcję typu agregacji `Integer` wywołuje ogólnego przeciążenia `Median` metody.  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Group By, klauzula](../../../visual-basic/language-reference/queries/group-by-clause.md)
