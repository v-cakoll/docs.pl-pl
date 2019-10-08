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
ms.openlocfilehash: 50a53cd45cc428541c90fbf82089518be2212fae
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004806"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate — Klauzula (Visual Basic)
Stosuje co najmniej jedną funkcję agregującą do kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`element`|Wymagany. Zmienna używana do iteracji elementów kolekcji.|  
|`type`|Opcjonalny. Typ `element`. Jeśli typ nie zostanie określony, typ `element` jest wywnioskowany z `collection`.|  
|`collection`|Wymagany. Odwołuje się do kolekcji, w której ma działać.|  
|`clause`|Opcjonalny. Co najmniej jedna klauzula zapytania, taka jak klauzula `Where`, do uściślenia wyniku zapytania, aby zastosować klauzulę agregującą lub klauzulę do.|  
|`expressionList`|Wymagany. Jedno lub więcej wyrażeń rozdzielanych przecinkami, które identyfikują funkcję agregującą, która ma zostać zastosowana do kolekcji. Można zastosować alias do funkcji agregującej, aby określić nazwę elementu członkowskiego dla wyniku zapytania. Jeśli nie podano aliasu, używana jest nazwa funkcji agregującej. Przykłady zawiera sekcja dotycząca funkcji agregujących w dalszej części tego tematu.|  
  
## <a name="remarks"></a>Uwagi  
 Klauzula `Aggregate` umożliwia uwzględnienie funkcji agregujących w zapytaniach. Funkcje agregujące wykonują operacje sprawdzania i obliczeń na zestawie wartości i zwracają pojedynczą wartość. Możesz uzyskać dostęp do obliczonej wartości przy użyciu elementu członkowskiego typu wyników zapytania. Standardowe funkcje agregujące, których można użyć, to `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min` i `Sum` funkcji. Te funkcje są znane dla deweloperów, którzy znają agregacje w programie SQL Server. Opisano je w poniższej sekcji tego tematu.  
  
 Wynik funkcji agregującej jest uwzględniany w wyniku zapytania jako pole typu wyniku zapytania. Można podać alias dla wyniku funkcji agregującej, aby określić nazwę elementu członkowskiego typu wyników zapytania, który będzie przechowywać wartość zagregowaną. Jeśli nie podano aliasu, używana jest nazwa funkcji agregującej.  
  
 Klauzula `Aggregate` może rozpoczynać zapytanie lub może być dołączana jako dodatkowa klauzula w zapytaniu. Jeśli klauzula `Aggregate` rozpoczyna zapytanie, wynikiem jest pojedyncza wartość, która jest wynikiem funkcji agregującej określonej w klauzuli `Into`. Jeśli w klauzuli `Into` określono więcej niż jedną funkcję agregującą, zapytanie zwróci pojedynczy typ z oddzielną właściwością, aby odwołać się do wyniku każdej funkcji agregującej w klauzuli `Into`. Jeśli klauzula `Aggregate` jest dołączana jako klauzula dodatkowa w zapytaniu, typ zwracany w kolekcji zapytań będzie miał osobną właściwość, aby odwołać się do wyniku każdej funkcji agregującej w klauzuli `Into`.  
  
## <a name="aggregate-functions"></a>Funkcje agregujące

Poniżej znajdują się standardowe funkcje agregujące, które mogą być używane z klauzulą `Aggregate`.  
  
### <a name="all"></a>Wszystkie

Zwraca `true`, jeśli wszystkie elementy w kolekcji spełniają określony warunek; w przeciwnym razie zwraca `false`. Oto przykład:

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>Ile

Zwraca `true`, jeśli dowolny element w kolekcji spełnia określony warunek; w przeciwnym razie zwraca `false`. Oto przykład:

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>Obliczon

Oblicza średnią wszystkich elementów w kolekcji lub oblicza dostarczone wyrażenie dla wszystkich elementów w kolekcji. Oto przykład:

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>Liczbą

Zlicza elementy w kolekcji. Możesz podać opcjonalne wyrażenie `Boolean`, aby obliczyć tylko liczbę elementów w kolekcji, które spełniają warunek. Oto przykład:

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>Grupa

Odwołuje się do wyników zapytania, które są pogrupowane w wyniku klauzuli `Group By` lub `Group Join`. Funkcja `Group` jest prawidłowa tylko w klauzuli `Into` w klauzuli `Group By` lub `Group Join`. Aby uzyskać więcej informacji i przykładów, zobacz klauzule Group [by](../../../visual-basic/language-reference/queries/group-by-clause.md) i Group [Join](../../../visual-basic/language-reference/queries/group-join-clause.md).

### <a name="longcount"></a>LongCount

Zlicza elementy w kolekcji. Możesz podać opcjonalne wyrażenie `Boolean`, aby obliczyć tylko liczbę elementów w kolekcji, które spełniają warunek. Zwraca wynik jako `Long`. Aby zapoznać się z przykładem, zobacz funkcję agregującą `Count`.

### <a name="max"></a>Maksymalny

Oblicza wartość maksymalną z kolekcji lub oblicza dostarczone wyrażenie dla wszystkich elementów w kolekcji. Oto przykład:

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>Długości

Oblicza wartość minimalną kolekcji lub oblicza dostarczone wyrażenie dla wszystkich elementów w kolekcji. Oto przykład:

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>Należności

Oblicza sumę wszystkich elementów w kolekcji lub oblicza dostarczone wyrażenie dla wszystkich elementów w kolekcji. Oto przykład:

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>Przykład  

Poniższy przykład pokazuje, jak używać klauzuli `Aggregate` do zastosowania funkcji agregujących do wyniku zapytania.  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Tworzenie funkcji agregujących zdefiniowanych przez użytkownika

 W wyrażeniu zapytania można uwzględnić własne niestandardowe funkcje agregujące, dodając metody rozszerzające do typu <xref:System.Collections.Generic.IEnumerable%601>. Metoda niestandardowa może następnie wykonać obliczenia lub operacje na wyliczalnej kolekcji, która przywołuje funkcję agregującą. Aby uzyskać więcej informacji na temat metod rozszerzających, zobacz [metody rozszerzenia](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Na przykład poniższy przykład pokazuje niestandardową funkcję agregującą, która oblicza wartość mediany kolekcji liczb. Istnieją dwa przeciążenia metody rozszerzenia `Median`. Pierwsze Przeciążenie akceptuje jako dane wejściowe, Kolekcja typu `IEnumerable(Of Double)`. Jeśli funkcja agregująca `Median` jest wywoływana dla pola zapytania typu `Double`, ta metoda zostanie wywołana. Drugie Przeciążenie metody `Median` może być przekazanie dowolnego typu ogólnego. Ogólne Przeciążenie metody `Median` przyjmuje drugi parametr, który odwołuje się do wyrażenia lambda `Func(Of T, Double)` do zaprojektowania wartości dla typu (z kolekcji) jako odpowiadającej wartości typu `Double`. Następnie przydeleguje obliczenie wartości mediany do innego przeciążenia metody `Median`. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 W poniższym przykładzie pokazano przykładowe zapytania, które wywołują funkcję agregującą `Median` w kolekcji typu `Integer` i kolekcji typu `Double`. Zapytanie, które wywołuje funkcję agregującą `Median` w kolekcji typu `Double` wywołuje Przeciążenie metody `Median`, która akceptuje jako dane wejściowe, Kolekcja typu `Double`. Zapytanie, które wywołuje funkcję agregującą `Median` w kolekcji typu `Integer` wywołuje ogólne Przeciążenie metody `Median`.  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By, klauzula](../../../visual-basic/language-reference/queries/group-by-clause.md)
