---
title: Aggregate — Klauzula (Visual Basic)
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: e3ce8ff7da647120e5fd9e3b4cd44cc603eb797d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519489"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate — Klauzula (Visual Basic)
Stosuje jedną lub więcej funkcji agregujących do kolekcji.  
  
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
|`element`|Wymagane. Zmienna jest używana do iteracji przez elementy kolekcji.|  
|`type`|Opcjonalna. Typ `element`. Jeśli nie określono typu, typu `element` wynika z `collection`.|  
|`collection`|Wymagane. Odnosi się do kolekcji do wykonywania operacji.|  
|`clause`|Opcjonalna. Jeden lub więcej klauzul zapytania, takie jak `Where` klauzulę, aby udoskonalić wynik zapytania, aby zastosować aggregate — klauzula lub klauzule.|  
|`expressionList`|Wymagane. Co najmniej jednego rozdzielonych przecinkami wyrażenia, które identyfikują funkcję agregacji, aby zastosować do kolekcji. Alias można zastosować do funkcji agregującej, aby określić nazwę elementu członkowskiego dla wyniku kwerendy. Jeśli nie dostarczono Brak aliasu, nazwa funkcji agregującej jest używana. Aby uzyskać przykłady zobacz sekcję dotyczącą funkcji agregujących w dalszej części tego tematu.|  
  
## <a name="remarks"></a>Uwagi  
 `Aggregate` Klauzuli może służyć do uwzględnienia funkcji agregujących w zapytaniach. Funkcje agregujące wykonują zbiór wartości kontroli i obliczeń i zwracać pojedynczą wartość. Obliczona wartość dostęp przy użyciu członka typu wyniku zapytania. Standardowe funkcje agregujące, których można użyć są `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, i `Sum` funkcji. Te funkcje są znane deweloperom, którzy są zaznajomieni z wartości zagregowanych w języku SQL. Zostały one opisane w poniższej sekcji tego tematu.  
  
 Wynik funkcji agregującej znajduje się w wyniku kwerendy jako pole typu wyniku zapytania. Możesz podać alias wyniku funkcji agregującej do określenia nazwy elementu członkowskiego typu wyniku zapytania, który będzie przechowywać wartości zagregowanej. Jeśli nie dostarczono Brak aliasu, nazwa funkcji agregującej jest używana.  
  
 `Aggregate` Klauzuli można rozpocząć zapytania lub może być uwzględniany jako dodatkową klauzulę w zapytaniu. Jeśli `Aggregate` klauzuli rozpoczyna się zapytanie, wynik jest pojedynczą wartość, która jest wynikiem funkcji agregującej, określone w `Into` klauzuli. Jeśli określono więcej niż jedną funkcję agregacji w `Into` klauzuli zapytanie zwraca jeden typ z właściwością oddzielne k odkazu wynik każdego w funkcji agregującej `Into` klauzuli. Jeśli `Aggregate` klauzula jest dołączony jako dodatkową klauzulę w zapytaniu, typ zwracany w kolekcji zapytanie będzie miał oddzielny właściwości, aby odwoływać się do wyniku każdej funkcji agregującej w `Into` klauzuli.  
  
## <a name="aggregate-functions"></a>Funkcje agregujące

Poniżej przedstawiono standardowe funkcje agregujące, które mogą być używane z `Aggregate` klauzuli.  
  
### <a name="all"></a>Wszystkie

Zwraca `true` , gdy wszystkie elementy w kolekcji spełniają określony warunek; w przeciwnym razie zwraca `false`. Oto przykład:

[!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]

### <a name="any"></a>Wszystkie

Zwraca `true` , jeżeli dowolny element w kolekcji spełnia określony warunek; w przeciwnym razie zwraca `false`. Oto przykład:

[!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]

### <a name="average"></a>Średnia

Oblicza średnią wszystkich elementów w kolekcji, lub oblicza wyrażenie podane dla wszystkich elementów w kolekcji. Oto przykład:

[!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]

### <a name="count"></a>Liczba

Zlicza liczbę elementów w kolekcji. Można podać opcjonalny `Boolean` wyrażenia do obliczania tylko liczby elementów w kolekcji, które spełniają warunek. Oto przykład:

[!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]

### <a name="group"></a>Grupa

Odwołuje się do wyników zapytania, które są grupowane w `Group By` lub `Group Join` klauzuli. `Group` Funkcja jest prawidłowa tylko w `Into` klauzuli `Group By` lub `Group Join` klauzuli. Aby uzyskać więcej informacji i przykładów, zobacz [grupy przez klauzulę](../../../visual-basic/language-reference/queries/group-by-clause.md) i [Group Join — klauzula](../../../visual-basic/language-reference/queries/group-join-clause.md).

### <a name="longcount"></a>LongCount

Zlicza liczbę elementów w kolekcji. Można podać opcjonalny `Boolean` wyrażenia do obliczania tylko liczby elementów w kolekcji, które spełniają warunek. Zwraca wynik w postaci `Long`. Aby uzyskać przykład, zobacz `Count` funkcję agregacji.

### <a name="max"></a>Maksymalna

Oblicza maksymalną wartość z kolekcji, lub oblicza wyrażenie podane dla wszystkich elementów w kolekcji. Oto przykład:

[!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]

### <a name="min"></a>min

Oblicza minimalną wartość z kolekcji, lub oblicza wyrażenie podane dla wszystkich elementów w kolekcji. Oto przykład:

[!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]

### <a name="sum"></a>Suma

Oblicza sumę wszystkich elementów w kolekcji, lub oblicza wyrażenie podane dla wszystkich elementów w kolekcji. Oto przykład:

[!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]

## <a name="example"></a>Przykład  

Poniższy przykład pokazuje, jak używać `Aggregate` klauzuli w celu zastosowanie funkcji agregujących do wyniku zapytania.  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Tworzenie funkcji agregujących zdefiniowanych przez użytkownika

 W wyrażeniu zapytania może zawierać własne niestandardowe funkcje agregujące, dodając metody rozszerzenia umożliwiające <xref:System.Collections.Generic.IEnumerable%601> typu. Metoda niestandardowych można wykonywać obliczenia lub operacja wyliczalny kolekcję, do której istnieje odwołanie do funkcji agregującej. Aby uzyskać więcej informacji dotyczących metod rozszerzających, zobacz [metody rozszerzenia](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Na przykład poniższy kod przedstawia niestandardowych funkcji agregującej, który oblicza wartość mediany zbioru liczb. Istnieją dwa przeciążenia `Median` — metoda rozszerzenia. Pierwsze przeciążenie przyjmuje jako dane wejściowe, Kolekcja typu `IEnumerable(Of Double)`. Jeśli `Median` funkcji agregującej jest wywoływana dla pola zapytania typu `Double`, ta metoda zostanie wywołana. Drugie przeciążenie `Median` metody mogą być przekazywane do dowolnego typu ogólnego. Przeciążenie ogólne `Median` metoda przyjmuje drugi parametr, który odwołuje się do `Func(Of T, Double)` wyrażenia lambda do projektu wartość dla typu (z kolekcji) jako wartość odpowiedniego typu `Double`. Następnie deleguje ona obliczenia wartość mediany, aby inne przeciążenia `Median` metody. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeń Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 W poniższym przykładzie przedstawiono przykładowe zapytania, które wywołują `Median` funkcję zbierania typu agregacji `Integer`, a kolekcja typu `Double`. Zapytanie, które wywołuje `Median` funkcję na kolekcję typu agregacji `Double` wywołuje przeciążenia `Median` metodę, która przyjmuje jako dane wejściowe, Kolekcja typu `Double`. Zapytanie, które wywołuje `Median` funkcję na kolekcję typu agregacji `Integer` wywołuje przeciążenia ogólne `Median` metody.  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)  
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)  
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)  
- [Klauzula Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
