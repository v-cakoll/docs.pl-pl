---
title: Typy o wartości zerowalnej (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16df20be89a88aa68e06692594c208cee1ab2dea
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="nullable-value-types-visual-basic"></a>Typy o wartości zerowalnej (Visual Basic)
Czasami użytkownik pracuje z typem wartości, która nie ma zdefiniowanej wartości w pewnych okolicznościach. Na przykład pola w bazie danych może być konieczne rozróżnienia o przypisane wartości, który jest łatwy do rozpoznania i nie ma przypisanej wartości. Typy wartości można rozszerzyć ich normalne wartości lub wartość null. Przedłużenie jest nazywany *typ dopuszczający wartość null*.  
  
 Każdy typ dopuszczający wartość null jest utworzone na podstawie ogólnego <xref:System.Nullable%601> struktury. Należy wziąć pod uwagę służący do śledzenia działań związanych z pracą bazy danych. Poniższy przykład tworzy nullable `Boolean` wpisz i deklaruje zmienną tego typu. Deklaracja może zapisać trzy sposoby:  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]  
  
 Zmienna `ridesBusToWork` może zawierać wartości `True`, wartość `False`, lub nie wartości we wszystkich. Wartość domyślną początkowej mają żadnej wartości, które w tym przypadku może oznaczać, że informacje nie ma jeszcze uzyskać tej osoby. Z kolei `False` może oznaczać, że uzyskano informacje, a osoby nie które wywołują magistrali do pracy.  
  
 Można zadeklarować zmienne i właściwości z typów dopuszczających wartości zerowe i można zadeklarować tablicy z elementami typu dopuszczającego wartość null. Można zadeklarować procedur z typy dopuszczające wartości null jako parametry, a można zwrócić wartości null typu z `Function` procedury.  
  
 Nie można skonstruować typu dopuszczającego wartość null na typ referencyjny, takich jak tablicy, `String`, lub klasy. Typ podstawowy musi być typem wartości. Aby uzyskać więcej informacji, zobacz [typów wartości i typy referencyjne](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
## <a name="using-a-nullable-type-variable"></a>Użycie zmiennej typu dopuszczającego wartość null  
 Najważniejsze elementy członkowskie typu dopuszczającego wartości null są jego <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A> właściwości. Dla zmiennej typu dopuszczającego wartość null <xref:System.Nullable%601.HasValue%2A> informuje, czy zmienna zawiera zdefiniowanej wartości. Jeśli <xref:System.Nullable%601.HasValue%2A> jest `True`, można odczytać wartości z <xref:System.Nullable%601.Value%2A>. Należy pamiętać, że oba <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A> są `ReadOnly` właściwości.  
  
### <a name="default-values"></a>Wartości domyślne  
 Deklaracja zmiennej typu dopuszczającego wartość null, jego <xref:System.Nullable%601.HasValue%2A> właściwość ma wartość domyślną równą `False`. Oznacza to, że domyślnie zmienna nie ma zdefiniowanej wartości, zamiast wartości domyślnej z jego typem podstawowym wartość. W poniższym przykładzie zmienna `numberOfChildren` początkowo nie ma zdefiniowanej wartości, nawet jeśli wartość domyślną `Integer` typ jest 0.  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]  
  
 Wartość null jest wskazuje niezdefiniowaną lub nieznaną wartość. Jeśli `numberOfChildren` zadeklarowano jako `Integer`, nie byłoby żadna wartość, która może wskazywać, że informacje nie są obecnie dostępne.  
  
### <a name="storing-values"></a>Przechowywanie wartości  
 Wartości są przechowywane w zmiennej lub właściwości typu dopuszczającego wartość null w typowy sposób. Poniższy przykład przypisuje wartość do zmiennej `numberOfChildren` zadeklarowany w poprzednim przykładzie.  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]  
  
 Zmienna lub właściwość typu dopuszczającego wartość null, zawiera wartość zdefiniowane, może spowodować jej powraca do stanu początkowego wyeliminowanie konieczności przypisaną wartość. Możesz to zrobić przez ustawienie zmiennej lub właściwości do `Nothing`, jak pokazano na poniższym przykładzie.  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]  
  
> [!NOTE]
>  Chociaż można przypisać `Nothing` do zmiennej typu dopuszczającego wartość null, nie można przetestować go dla `Nothing` przy użyciu znaku równości. Porównanie, które używa znaku równości `someVar = Nothing`, zawsze daje w wyniku `Nothing`. Można przetestować zmiennej <xref:System.Nullable%601.HasValue%2A> właściwość `False`, lub testowania przy użyciu `Is` lub `IsNot` operatora.  
  
### <a name="retrieving-values"></a>Pobieranie wartości  
 Można pobrać wartości zmiennej typu dopuszczającego wartość null, należy najpierw przetestować jego <xref:System.Nullable%601.HasValue%2A> właściwości, aby upewnić się, że ma ona wartość. Jeśli użytkownik próbuje odczytać wartości podczas <xref:System.Nullable%601.HasValue%2A> jest `False`, Visual Basic generuje <xref:System.InvalidOperationException> wyjątku. W poniższym przykładzie przedstawiono zalecany sposób odczytać zmiennej `numberOfChildren` poprzednich przykładach.  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]  
  
## <a name="comparing-nullable-types"></a>Porównanie typów dopuszczających wartości zerowe  
 W przypadku wartości null `Boolean` zmienne są używane w wyrażeniach logicznych, może to spowodować powstanie `True`, `False`, lub `Nothing`. Poniżej znajduje się Tabela prawdy dla `And` i `Or`. Ponieważ `b1` i `b2` już trzema możliwymi wartościami są dziewięć kombinacji do oceny.  
  
|B1|B2|B1 i b2|B1 lub b2|  
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
  
 Gdy jest wartość logiczna lub wyrażenie `Nothing`, nie jest `true` ani `false`. Rozważmy następujący przykład.  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]  
  
 W tym przykładzie `b1 And b2` daje w wyniku `Nothing`. W związku z tym `Else` klauzuli jest wykonywana w każdym `If` instrukcji i dane wyjściowe wygląda następująco:  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  `AndAlso` i `OrElse`, wykorzystującymi zwarcia oceny, musi mieć drugi operandy po pierwszym daje w wyniku `Nothing`.  
  
## <a name="propagation"></a>Propagacja  
 Jeśli jeden lub oba argumenty operacji arytmetyczne, porównania, shift lub typ operacji jest wartość null, wynik operacji jest również wartości null. Jeśli oba argumenty mają wartości, które nie są `Nothing`, operacja jest wykonywana na wartości podstawowych argumentów operacji, tak, jakby nie był typ dopuszczający wartość null. W poniższym przykładzie, zmienne `compare1` i `sum1` niejawnie wpisywania. Jeśli wskaźnik myszy nad nimi, zobaczysz, że kompilator wnioskuje typy dopuszczające wartości null dla obu z nich.  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]  
  
 Jeśli jeden lub oba argumenty mają wartość `Nothing`, wynikiem będzie `Nothing`.  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]  
  
## <a name="using-nullable-types-with-data"></a>Używanie typów dopuszczających wartości zerowe z danymi  
 Baza danych jest jednym z najważniejszych miejsc, można używać typu dopuszczającego wartość null. Nie wszystkie obiekty bazy danych nie obsługiwało typy dopuszczające wartości null, ale nie adaptery wygenerowany przez projektanta tabel. Sekcja "Obsługa TableAdapter typy dopuszczające wartości zerowe" w [TableAdapter — Przegląd](/visualstudio/data-tools/tableadapter-overview).
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.InvalidOperationException>  
 <xref:System.Nullable%601.HasValue%2A>  
 [Używanie typów dopuszczających wartości null](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Typy wartości i odwołań](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [TableAdapter — Przegląd](/visualstudio/data-tools/tableadapter-overview)  
 [If, operator](../../../../visual-basic/language-reference/operators/if-operator.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Is, operator](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot, operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)
