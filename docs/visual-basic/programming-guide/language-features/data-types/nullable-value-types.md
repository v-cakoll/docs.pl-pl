---
title: Typy o wartości zerowalnej - Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: d17d2ad3fd99c6d563c21ddd646396ccb1c1ca48
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921315"
---
# <a name="nullable-value-types-visual-basic"></a>Typy o wartości zerowalnej (Visual Basic)

Czasami pracuje się z typem wartości, która nie ma zdefiniowanej wartości w pewnych okolicznościach. Na przykład pola w bazie danych może być do rozróżniania masz przypisaną wartość, która ma znaczenie i nie ma przypisaną wartość. Typy wartości można rozszerzyć do wykonania w ich normalnym wartości lub wartość null. Takie rozszerzenia jest wywoływana *typu dopuszczającego wartość null*.

Każdy typ dopuszczający wartość null jest zbudowany z ogólnego <xref:System.Nullable%601> struktury. Należy wziąć pod uwagę bazy danych, który śledzi działania związane z pracą. Poniższy przykład tworzy dopuszczający wartości null `Boolean` wpisz i deklaruje zmienną typu. Deklaracji można napisać na trzy sposoby:

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

Zmienna `ridesBusToWork` może zawierać wartości `True`, wartość `False`, lub nie ma wartości wszystkie. Wartość początkową domyślną jest żadnej wartości, który w tym przypadku może oznaczać, że że informacje nie ma jeszcze uzyskać danej osoby. Z kolei `False` może oznaczać, że uzyskano informacje, a osoby nie zastąpienie magistrali do pracy.

Możesz deklarować zmienne i właściwości z typami zerowalnymi. Ponadto można zadeklarować tablicy o liczbie elementów typu dopuszczającego wartość null. Można zadeklarować procedur z typami zerowalnymi jako parametry i może zwracać typ dopuszczający wartość null z `Function` procedury.

Nie można skonstruować typu dopuszczającego wartość null na typ referencyjny, takich jak tablica, `String`, lub klasy. Typ podstawowy musi być typem wartości. Aby uzyskać więcej informacji, zobacz [typy wartości i odwołań](value-types-and-reference-types.md).

## <a name="using-a-nullable-type-variable"></a>Przy użyciu zmiennej typu dopuszczającego wartość null

Najważniejsze elementy członkowskie typu dopuszczającego wartość null są jego <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A> właściwości. Dla zmiennej typu dopuszczającego wartość null <xref:System.Nullable%601.HasValue%2A> informujący o tym, czy zmienna zawiera wartość zdefiniowana. Jeśli <xref:System.Nullable%601.HasValue%2A> jest `True`, można odczytać wartości z <xref:System.Nullable%601.Value%2A>. Należy pamiętać, że oba <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A> są `ReadOnly` właściwości.

### <a name="default-values"></a>Wartości domyślne

Kiedy Deklarujesz zmienną typu dopuszczającego wartość null, jego <xref:System.Nullable%601.HasValue%2A> właściwość ma wartość domyślną `False`. Oznacza to, że domyślnie zmiennej nie ma zdefiniowanej wartości, zamiast wartości domyślne, jego bazowego typu wartości. W poniższym przykładzie zmienna `numberOfChildren` początkowo nie ma zdefiniowanej wartości, nawet jeśli wartość domyślną `Integer` typu wynosi 0.

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Wartość null jest przydatne do wskazania wartość niezdefiniowana lub nieznany. Jeśli `numberOfChildren` zadeklarowano jako `Integer`, nie będzie żadnej wartości, które mogą wskazywać, że informacje nie są obecnie dostępne.

### <a name="storing-values"></a>Przechowywanie wartości

Wartość jest przechowywana w zmiennej lub właściwości typu dopuszczającego wartość null w typowy sposób. Poniższy przykład przypisuje wartość do zmiennej `numberOfChildren` zadeklarowanej w poprzednim przykładzie.

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Zmiennej lub właściwości typu dopuszczającego wartość null, zawiera wartość zdefiniowana, może spowodować, aby powrócić do stanu początkowego nie ma przypisaną wartość. Możesz to zrobić przez ustawienie zmiennej lub właściwości `Nothing`, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> Chociaż można przypisać `Nothing` do zmiennej typu dopuszczającego wartość null, nie możesz przetestować ją dla `Nothing` przy użyciu znaku równości. Porównanie, które używa znaku równości `someVar = Nothing`, zawsze daje w wyniku `Nothing`. Możesz przetestować zmiennej <xref:System.Nullable%601.HasValue%2A> właściwość `False`, lub testowania przy użyciu `Is` lub `IsNot` operatora.

### <a name="retrieving-values"></a>Pobieranie wartości

Aby pobrać wartość zmiennej typu dopuszczającego wartość null, najpierw należy przetestować jego <xref:System.Nullable%601.HasValue%2A> właściwości, aby upewnić się, że ma ona wartość. Jeśli użytkownik próbuje odczytać wartości podczas <xref:System.Nullable%601.HasValue%2A> jest `False`, Visual Basic zgłasza <xref:System.InvalidOperationException> wyjątku. W poniższym przykładzie przedstawiono zalecaną metodą odczyt zmiennej `numberOfChildren` z poprzednich przykładów.

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Porównywanie typów dopuszczających wartości zerowe

Gdy nullable `Boolean` zmienne są używane w wyrażeniach logicznych, może to spowodować `True`, `False`, lub `Nothing`. Poniżej znajduje się w tabeli prawdziwych danych `And` i `Or`. Ponieważ `b1` i `b2` powstał trzema możliwymi wartościami, istnieją dziewięć kombinacji do oceny.

|b1|b2|B1 i b2|B1 i b2|
|--------|--------|---------------|--------------|
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|
|`Nothing`|`True`|`Nothing`|`True`|
|`Nothing`|`False`|`False`|`Nothing`|
|`True`|`Nothing`|`Nothing`|`True`|
|`True`|`True`|`True`|`True`|
|`True`|`False`|`False`|`True`|
|`False`|`Nothing`|`False`|`Nothing`|
|`False`|`True`|`False`|`True`|
|`False`|`False`|`False`|`False`|

Gdy wartość zmiennej typu Boolean lub wyrażenia jest `Nothing`, nie jest `true` ani `false`. Rozważmy następujący przykład.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

W tym przykładzie `b1 And b2` daje w wyniku `Nothing`. W rezultacie `Else` klauzula jest wykonywana w każdym `If` instrukcji i dane wyjściowe są następujące:

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso` i `OrElse`, wykorzystującymi zwarcia musi wzięcia pod uwagę drugiej operandy przy pierwszym daje w wyniku `Nothing`.

## <a name="propagation"></a>Propagacja

Jeśli jeden lub oba operandy operacje arytmetyczne, porównanie, przesunięcia lub operację typu ma wartość null, wynik operacji jest również dopuszczającego wartość null. Jeśli oba operandy mają wartości, które nie są `Nothing`, operacja jest wykonywana na podstawowej wartości argumentów, tak, jakby nie były typu dopuszczającego wartość null. W poniższym przykładzie zmienne `compare1` i `sum1` są wpisywane niejawnie. Jeśli przytrzymasz wskaźnik myszy nad nimi, zobaczysz, że kompilator wnioskuje typy dopuszczające wartości null dla obu z nich.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Jeśli jeden lub oba argumenty mają wartość `Nothing`, wynik będzie `Nothing`.

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Używanie typów dopuszczających wartości zerowe z danymi

Baza danych jest jednym z najważniejszych miejsc do użycia typy dopuszczające wartości null. Nie wszystkie obiekty bazy danych obecnie obsługuje typy dopuszczające wartości null, ale działają adaptery wygenerowany przez projektanta tabel. Zobacz [TableAdapter obsługę typów dopuszczających wartości zerowe](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).

## <a name="see-also"></a>Zobacz także

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [Używanie typów dopuszczających wartości zerowe](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [Typy danych](index.md)
- [Typy wartości i odwołań](value-types-and-reference-types.md)
- [Rozwiązywanie problemów związanych z typami](troubleshooting-data-types.md)
- [Wypełnij zestawów danych za pomocą adapterów TableAdapter](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [If — operator](../../../language-reference/operators/if-operator.md)
- [Wnioskowanie o typie lokalnym](../variables/local-type-inference.md)
- [Is — Operator](../../../language-reference/operators/is-operator.md)
- [Operator IsNot](../../../language-reference/operators/isnot-operator.md)