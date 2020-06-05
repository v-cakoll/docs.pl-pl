---
title: Aggregate, klauzula
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
ms.openlocfilehash: 326c3306368ceca2122e912556efd84e4bfef1f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413004"
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
|`type`|Opcjonalny. Typ `element` . Jeśli typ nie zostanie określony, typ `element` jest wnioskowany z `collection` .|  
|`collection`|Wymagany. Odwołuje się do kolekcji, w której ma działać.|  
|`clause`|Opcjonalny. Co najmniej jedna klauzula zapytania, taka jak `Where` klauzula, do uściślenia wyniku zapytania, aby zastosować klauzulę agregującą lub klauzulę do.|  
|`expressionList`|Wymagany. Jedno lub więcej wyrażeń rozdzielanych przecinkami, które identyfikują funkcję agregującą, która ma zostać zastosowana do kolekcji. Można zastosować alias do funkcji agregującej, aby określić nazwę elementu członkowskiego dla wyniku zapytania. Jeśli nie podano aliasu, używana jest nazwa funkcji agregującej. Przykłady zawiera sekcja dotycząca funkcji agregujących w dalszej części tego tematu.|  
  
## <a name="remarks"></a>Uwagi  
 `Aggregate`Klauzula może służyć do uwzględnienia funkcji agregujących w zapytaniach. Funkcje agregujące wykonują operacje sprawdzania i obliczeń na zestawie wartości i zwracają pojedynczą wartość. Możesz uzyskać dostęp do obliczonej wartości przy użyciu elementu członkowskiego typu wyników zapytania. Standardowe funkcje agregujące, których można użyć, to funkcje,,,,,, `All` `Any` `Average` `Count` `LongCount` `Max` `Min` i `Sum` . Te funkcje są znane dla deweloperów, którzy znają agregacje w programie SQL Server. Opisano je w poniższej sekcji tego tematu.  
  
 Wynik funkcji agregującej jest uwzględniany w wyniku zapytania jako pole typu wyniku zapytania. Można podać alias dla wyniku funkcji agregującej, aby określić nazwę elementu członkowskiego typu wyników zapytania, który będzie przechowywać wartość zagregowaną. Jeśli nie podano aliasu, używana jest nazwa funkcji agregującej.  
  
 `Aggregate`Klauzula może rozpoczynać zapytanie lub może być dołączana jako dodatkowa klauzula w zapytaniu. Jeśli `Aggregate` klauzula rozpoczyna kwerendę, wynikiem jest pojedyncza wartość, która jest wynikiem funkcji agregującej określonej w `Into` klauzuli. Jeśli w klauzuli określono więcej niż jedną funkcję agregującą `Into` , zapytanie zwraca pojedynczy typ z oddzielną właściwością, aby odwołać wynik każdej funkcji agregującej w `Into` klauzuli. Jeśli `Aggregate` klauzula jest uwzględniona jako dodatkowa klauzula w zapytaniu, typ zwracany w kolekcji zapytań będzie miał osobną właściwość, aby odwołać się do wyniku każdej funkcji agregującej w `Into` klauzuli.  
  
## <a name="aggregate-functions"></a>Funkcje agregujące

Poniżej znajdują się standardowe funkcje agregujące, które mogą być używane z `Aggregate` klauzulą.  
  
### <a name="all"></a>Wszyscy

Zwraca `true` czy wszystkie elementy w kolekcji spełniają określony warunek; w przeciwnym razie zwraca `false` . Poniżej przedstawiono przykład:

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>Dowolne

Zwraca `true` czy dowolny element w kolekcji spełnia określony warunek; w przeciwnym razie zwraca `false` . Poniżej przedstawiono przykład:

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>Średnia

Oblicza średnią wszystkich elementów w kolekcji lub oblicza dostarczone wyrażenie dla wszystkich elementów w kolekcji. Poniżej przedstawiono przykład:

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>Liczba

Zlicza elementy w kolekcji. Można podać opcjonalne `Boolean` wyrażenie, aby obliczyć tylko liczbę elementów w kolekcji, które spełniają warunek. Poniżej przedstawiono przykład:

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>Grupa

Odwołuje się do wyników zapytania, które są pogrupowane w `Group By` wyniku `Group Join` klauzuli OR. `Group`Funkcja jest prawidłowa tylko w `Into` klauzuli `Group By` `Group Join` klauzuli OR. Aby uzyskać więcej informacji i przykładów, zobacz klauzule Group [by](group-by-clause.md) i Group [Join](group-join-clause.md).

### <a name="longcount"></a>LongCount

Zlicza elementy w kolekcji. Można podać opcjonalne `Boolean` wyrażenie, aby obliczyć tylko liczbę elementów w kolekcji, które spełniają warunek. Zwraca wynik w postaci `Long` . Aby zapoznać się z przykładem, zobacz `Count` Funkcja agregująca.

### <a name="max"></a>Maks.

Oblicza wartość maksymalną z kolekcji lub oblicza dostarczone wyrażenie dla wszystkich elementów w kolekcji. Poniżej przedstawiono przykład:

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>Min.

Oblicza wartość minimalną kolekcji lub oblicza dostarczone wyrażenie dla wszystkich elementów w kolekcji. Poniżej przedstawiono przykład:

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>Suma

Oblicza sumę wszystkich elementów w kolekcji lub oblicza dostarczone wyrażenie dla wszystkich elementów w kolekcji. Poniżej przedstawiono przykład:

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>Przykład  

Poniższy przykład pokazuje, jak używać `Aggregate` klauzuli do stosowania funkcji agregujących do wyniku zapytania.  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Tworzenie funkcji agregujących zdefiniowanych przez użytkownika

 W wyrażeniu zapytania można uwzględnić własne niestandardowe funkcje agregujące, dodając metody rozszerzające do <xref:System.Collections.Generic.IEnumerable%601> typu. Metoda niestandardowa może następnie wykonać obliczenia lub operacje na wyliczalnej kolekcji, która przywołuje funkcję agregującą. Aby uzyskać więcej informacji na temat metod rozszerzających, zobacz [metody rozszerzenia](../../programming-guide/language-features/procedures/extension-methods.md).  
  
 Na przykład poniższy przykład pokazuje niestandardową funkcję agregującą, która oblicza wartość mediany kolekcji liczb. Istnieją dwa przeciążenia `Median` metody rozszerzenia. Pierwsze przeciążenie przyjmuje jako dane wejściowe, Kolekcja typu `IEnumerable(Of Double)` . Jeśli `Median` Funkcja agregująca jest wywoływana dla pola zapytania typu `Double` , ta metoda zostanie wywołana. Drugie Przeciążenie `Median` metody może być przekazanie dowolnego typu ogólnego. Ogólne Przeciążenie `Median` metody przyjmuje drugi parametr, który odwołuje się do `Func(Of T, Double)` wyrażenia lambda, aby zaprojektować wartość dla typu (z kolekcji) jako odpowiadającą wartość typu `Double` . Następnie przydeleguje obliczenie wartości mediany do innego przeciążenia `Median` metody. Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 Poniższy przykład pokazuje przykładowe zapytania, które wywołują `Median` funkcję agregującą w kolekcji typu `Integer` , i kolekcję typu `Double` . Zapytanie, które wywołuje `Median` funkcję agregującą w kolekcji typu `Double` wywołuje Przeciążenie `Median` metody, która akceptuje, jako dane wejściowe, Kolekcja typu `Double` . Zapytanie, które wywołuje `Median` funkcję agregującą w kolekcji typu `Integer` wywołuje ogólne Przeciążenie `Median` metody.  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](index.md)
- [SELECT — klauzula](select-clause.md)
- [Klauzula from](from-clause.md)
- [Klauzula WHERE](where-clause.md)
- [Group By, klauzula](group-by-clause.md)
