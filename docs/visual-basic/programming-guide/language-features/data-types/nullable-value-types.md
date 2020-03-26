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
ms.openlocfilehash: beed8262c50dc68330b8f03aa3d864ed2f8df0d5
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249685"
---
# <a name="nullable-value-types-visual-basic"></a>Typy o wartości zerowalnej (Visual Basic)

Czasami pracujesz z typem wartości, który nie ma zdefiniowanej wartości w pewnych okolicznościach. Na przykład pole w bazie danych może być konieczności rozróżnienia między o przypisanej wartości, która ma znaczenie i nie ma przypisanej wartości. Typy wartości można rozszerzyć, aby wziąć ich wartości normalne lub wartość null. Takie rozszerzenie jest nazywane *typem nullable*.

Każdy typ wartości nullable jest <xref:System.Nullable%601> konstruowany ze struktury ogólnej. Należy wziąć pod uwagę bazę danych, która śledzi działania związane z pracą. Poniższy przykład konstruuje `Boolean` typ nullable i deklaruje zmienną tego typu. Deklarację można napisać na trzy sposoby:

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

Zmienna `ridesBusToWork` może zawierać `True`wartość , `False`wartość , lub w ogóle nie. Jego początkowa wartość domyślna nie jest wcale wartością, co w tym przypadku może oznaczać, że informacje nie zostały jeszcze uzyskane dla tej osoby. W przeciwieństwie `False` do tego, może to oznaczać, że informacje zostały uzyskane, a osoba nie jedzie autobusem do pracy.

Można zadeklarować zmienne i właściwości z typami wartości nullable i można zadeklarować tablicę z elementami typu wartości nullable. Można zadeklarować procedury z typami wartości nullable jako parametry i `Function` można zwrócić typ wartości nullable z procedury.

Nie można skonstruować typu nullable na typ odwołania, takich jak tablica, `String`, lub klasy. Typ podstawowy musi być typem wartości. Aby uzyskać więcej informacji, zobacz [Typy wartości i Typy odwołań](value-types-and-reference-types.md).

## <a name="using-a-nullable-type-variable"></a>Korzystanie ze zmiennej typu możliwego do wartości null

Najważniejszymi elementami elementów członkowskich typu <xref:System.Nullable%601.HasValue%2A> <xref:System.Nullable%601.Value%2A> wartości możliwego do wartości null są jego i właściwości. Dla zmiennej typu wartości możliwej do wartości null informuje, <xref:System.Nullable%601.HasValue%2A> czy zmienna zawiera zdefiniowaną wartość. Jeśli <xref:System.Nullable%601.HasValue%2A> `True`tak, można odczytać <xref:System.Nullable%601.Value%2A>wartość z . Należy zauważyć, <xref:System.Nullable%601.Value%2A> `ReadOnly` że oba <xref:System.Nullable%601.HasValue%2A> i są właściwości.

### <a name="default-values"></a>Wartości domyślne

Podczas deklarowania zmiennej z typem <xref:System.Nullable%601.HasValue%2A> wartości możliwej do `False`wartości null jej właściwość ma wartość domyślną . Oznacza to, że domyślnie zmienna nie ma zdefiniowanej wartości, zamiast wartości domyślnej jej typa wartości podstawowej. W poniższym przykładzie `numberOfChildren` zmienna początkowo nie ma zdefiniowanej `Integer` wartości, nawet jeśli domyślną wartością typu jest 0.

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

Wartość null jest przydatna do wskazania wartości niezdefiniowanej lub nieznanej. Gdyby `numberOfChildren` został zadeklarowany jako `Integer`, nie byłoby żadnej wartości, która mogłaby wskazywać, że informacje nie są obecnie dostępne.

### <a name="storing-values"></a>Przechowywanie wartości

Wartość jest przechowywana w zmiennej lub właściwości typu wartości nullable w typowy sposób. Poniższy przykład przypisuje wartość do `numberOfChildren` zmiennej zadeklarowanej w poprzednim przykładzie.

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

Jeśli zmienna lub właściwość typu wartości możliwej do wartości null zawiera zdefiniowaną wartość, może spowodować, że powróci do stanu początkowego, który nie ma przypisanej wartości. Można to zrobić, ustawiając `Nothing`zmienną lub właściwość na , jak pokazano w poniższym przykładzie.

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> Chociaż można `Nothing` przypisać do zmiennej typu wartości nullable, `Nothing` nie można przetestować go za pomocą znaku równości. Porównanie, które używa znaku `someVar = Nothing`równości, zawsze `Nothing`ocenia . Właściwość zmiennej można przetestować pod kątem `False` `Is` , lub przetestować za pomocą operatora lub. `IsNot` <xref:System.Nullable%601.HasValue%2A>

### <a name="retrieving-values"></a>Pobieranie wartości

Aby pobrać wartość zmiennej typu wartości możliwej do wartości <xref:System.Nullable%601.HasValue%2A> null, należy najpierw przetestować jej właściwość, aby potwierdzić, że ma wartość. Jeśli spróbujesz odczytać <xref:System.Nullable%601.HasValue%2A> wartość, gdy jest `False` <xref:System.InvalidOperationException> , Visual Basic zgłasza wyjątek. W poniższym przykładzie przedstawiono `numberOfChildren` zalecany sposób odczytywania zmiennej poprzednich przykładów.

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a>Porównywanie typów powodujących wartość null

Gdy zmienne `Boolean` nullowalne są używane w wyrażeniach `True` `False`logicznych, wynikiem może być , lub `Nothing`. Poniżej znajduje się `And` tabela prawdy dla i `Or`. Ponieważ `b1` `b2` i teraz mają trzy możliwe wartości, istnieje dziewięć kombinacji do oceny.

|b1|B2|b1 I b2|b1 Lub b2|
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

Gdy wartość zmiennej logicznej lub `Nothing`wyrażenia jest `true` , `false`nie jest ani, ani . Rozważmy następujący przykład.

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

W tym `b1 And b2` przykładzie `Nothing`ocenia . W rezultacie klauzula `Else` jest wykonywana `If` w każdej instrukcji, a dane wyjściowe są następujące:

`Expression is not true`

`Expression is not false`

> [!NOTE]
> `AndAlso`i `OrElse`, które korzystają z oceny zwarcia, muszą ocenić `Nothing`swoje drugie argumenty, gdy pierwszy ocenia.

## <a name="propagation"></a>Propagacja

Jeśli jeden lub oba argumenty operacji arytmetycznej, porównania, przesunięcia lub typu jest typem wartości możliwej do wartości null, wynikiem operacji jest również typ wartości powodującej wartość null. Jeśli oba argumenty mają wartości, `Nothing`które nie są, operacja jest wykonywana na podstawowych wartości operands, tak jakby nie były typu wartości nullable. W poniższym przykładzie `compare1` `sum1` zmienne i są niejawnie wpisane. Jeśli opierasz wskaźnik myszy na nich, zobaczysz, że kompilator wnioskuje nullable typów wartości dla obu z nich.

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

Jeśli jeden lub oba argumenty mają `Nothing`wartość , `Nothing`wynik będzie .

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a>Używanie typów nullable z danymi

Baza danych jest jednym z najważniejszych miejsc do użycia typów wartości nullable. Nie wszystkie obiekty bazy danych obsługują obecnie typy wartości nullable, ale karty tabel generowane przez projektanta zrobić. Zobacz [TableAdapter wsparcie dla typów nullable](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).

## <a name="see-also"></a>Zobacz też

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
- [Typy wartości z dopuszczalną wartości (C#)](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
