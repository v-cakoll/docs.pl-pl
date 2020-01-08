---
title: Typy o wartości zerowalnej
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
ms.openlocfilehash: 0d259e11a969f4eb7e64626a4adf498db06ece06
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347839"
---
# <a name="nullable-value-types-visual-basic"></a>Typy o wartości zerowalnej (Visual Basic)

Czasami pracujesz z typem wartości, który nie ma zdefiniowanej wartości w pewnych okolicznościach. Na przykład w przypadku pola w bazie danych może być konieczne odróżnienie od posiadania przypisanej wartości, która jest istotna i nie ma przypisanej wartości. Typy wartości można rozszerzyć, aby przyjmować ich normalne wartości lub wartość null. Takie rozszerzenie jest nazywane *typem dopuszczającym wartość null*.

Każdy typ dopuszczający wartość null jest konstruowany z ogólnej struktury <xref:System.Nullable%601>. Rozważmy bazę danych, która śledzi działania związane z pracą. Poniższy przykład tworzy typ `Boolean` nullable i deklaruje zmienną tego typu. Deklarację można napisać na trzy sposoby:

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

Zmienna `ridesBusToWork` może przechowywać w ogóle wartość `True`, wartość `False`lub brak wartości. Jego początkowa wartość domyślna nie jest wcale, co w tym przypadku może oznaczać, że informacje nie zostały jeszcze uzyskane dla tej osoby. W przeciwieństwie do `False` może oznaczać, że informacje zostały uzyskane i osoba nie przełączy magistrali do pracy.

Można zadeklarować zmienne i właściwości z typami dopuszczających wartość null i można zadeklarować tablicę z elementami typu dopuszczającego wartość null. Można zadeklarować procedury z typami dopuszczającymi wartość null jako parametry i można zwrócić typ dopuszczający wartość null z procedury `Function`ej.

Nie można skonstruować typu dopuszczającego wartość null w typie referencyjnym, takim jak tablica, `String`lub Klasa. Typ podstawowy musi być typem wartości. Aby uzyskać więcej informacji, zobacz [typy wartości i typy odwołań](value-types-and-reference-types.md).

## <a name="using-a-nullable-type-variable"></a>Użycie zmiennej typu dopuszczającego wartość null

Najważniejszymi elementami członkowskimi typu dopuszczającego wartość null są <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A> właściwości. W przypadku zmiennej typu dopuszczającego wartość null <xref:System.Nullable%601.HasValue%2A> informuje, czy zmienna zawiera zdefiniowaną wartość. Jeśli <xref:System.Nullable%601.HasValue%2A> jest `True`, można odczytać wartość z <xref:System.Nullable%601.Value%2A>. Należy zauważyć, że zarówno <xref:System.Nullable%601.HasValue%2A>, jak i <xref:System.Nullable%601.Value%2A> są `ReadOnly` właściwości.

### <a name="default-values"></a>Wartości domyślne

Gdy deklarujesz zmienną z typem dopuszczającym wartość null, jej Właściwość <xref:System.Nullable%601.HasValue%2A> ma wartość domyślną `False`. Oznacza to, że domyślnie zmienna nie ma zdefiniowanej wartości, a nie wartości domyślnej jej bazowego typu wartości. W poniższym przykładzie zmienna `numberOfChildren` początkowo nie ma zdefiniowanej wartości, mimo że wartość domyślna typu `Integer` to 0.

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Wartość null jest przydatna do wskazania niezdefiniowanej lub nieznanej wartości. Jeśli `numberOfChildren` został zadeklarowany jako `Integer`, nie będzie żadnej wartości, która może wskazywać, że informacje nie są obecnie dostępne.

### <a name="storing-values"></a>Przechowywanie wartości

W typowy sposób przechowujesz wartość w zmiennej lub właściwości typu dopuszczającego wartość null. Poniższy przykład przypisuje wartość do zmiennej `numberOfChildren` zadeklarowanej w poprzednim przykładzie.

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Jeśli zmienna lub właściwość typu Nullable zawiera zdefiniowaną wartość, można spowodować przywrócenie stanu początkowego nieprzypisanej wartości. W tym celu należy ustawić zmienną lub właściwość na `Nothing`, jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> Chociaż można przypisywać `Nothing` do zmiennej typu dopuszczającego wartość null, nie można go testować dla `Nothing` przy użyciu znaku równości. Porównanie, które używa znaku równości, `someVar = Nothing`, zawsze jest obliczane do `Nothing`. Można przetestować Właściwość <xref:System.Nullable%601.HasValue%2A> zmiennej dla `False`lub test przy użyciu operatora `Is` lub `IsNot`.

### <a name="retrieving-values"></a>Pobieranie wartości

Aby pobrać wartość zmiennej typu Nullable, należy najpierw przetestować jej Właściwość <xref:System.Nullable%601.HasValue%2A>, aby potwierdzić, że ma wartość. Jeśli spróbujesz odczytać wartość, gdy <xref:System.Nullable%601.HasValue%2A> jest `False`, Visual Basic zgłasza wyjątek <xref:System.InvalidOperationException>. W poniższym przykładzie przedstawiono zalecany sposób odczytywania zmiennej `numberOfChildren` z poprzednich przykładów.

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Porównywanie typów dopuszczających wartości null

Gdy wartości null `Boolean` zmienne są używane w wyrażeniach logicznych, wynik może być `True`, `False`lub `Nothing`. Poniżej przedstawiono tabelę prawdziwą dla `And` i `Or`. Ponieważ `b1` i `b2` teraz mają trzy możliwe wartości, istnieje dziewięć kombinacji do obliczenia.

|b1|b2|B1 i B2|B1 lub B2|
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

Gdy wartość zmiennej lub wyrażenia logicznego jest `Nothing`, nie `true` ani `false`. Rozpatrzmy następujący przykład.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

W tym przykładzie `b1 And b2` oblicza `Nothing`. W efekcie klauzula `Else` jest wykonywana w każdej instrukcji `If`, a dane wyjściowe są następujące:

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso` i `OrElse`, które korzystają z oceny krótkiego obwodu, muszą ocenić dwa operandy, gdy pierwsze szacuje się w `Nothing`.

## <a name="propagation"></a>Propagacja

Jeśli jeden lub oba operandy operacji arytmetycznych, porównywania, przesunięcia lub typu mają wartość null, wynik operacji również dopuszcza wartość null. Jeśli oba operandy mają wartości, które nie są `Nothing`, operacja jest wykonywana na podstawowych wartościach operandów, tak jakby nie były typem dopuszczającym wartość null. W poniższym przykładzie zmienne `compare1` i `sum1` są wpisane niejawnie. Jeśli umieścisz wskaźnik myszy nad nimi, zobaczysz, że kompilator wnioskuje Typy dopuszczające wartość null dla obu tych elementów.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Jeśli jeden lub oba operandy mają wartość `Nothing`, wynik zostanie `Nothing`.

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Używanie typów dopuszczających wartości null z danymi

Baza danych jest jednym z najważniejszych miejsc, w których można używać typów dopuszczających wartość null. Nie wszystkie obiekty bazy danych obsługują obecnie Typy dopuszczające wartość null, ale adaptery tabeli generowane przez projektanta. Zobacz [TableAdapter support for nullable Types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).

## <a name="see-also"></a>Zobacz także

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [Typy danych](index.md)
- [Typy wartości i odwołań](value-types-and-reference-types.md)
- [Rozwiązywanie problemów związanych z typami danych](troubleshooting-data-types.md)
- [Wypełnianie zestawów danych za pomocą adapterów TableAdapter](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [If, operator](../../../language-reference/operators/if-operator.md)
- [Wnioskowanie o typie lokalnym](../variables/local-type-inference.md)
- [Is, operator](../../../language-reference/operators/is-operator.md)
- [IsNot, operator](../../../language-reference/operators/isnot-operator.md)
- [Typy wartości null (C#)](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
