---
title: Select...Case, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: 3dedd43f920b493a0aca9ce48460b00815e1af5c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404242"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case — Instrukcja (Visual Basic)
Uruchamia jedną z kilku grup instrukcji w zależności od wartości wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`testexpression`|Wymagany. Wyrażenia. Należy oszacować do jednego z podstawowych typów danych (,,,,,,,,,, `Boolean` `Byte` `Char` `Date` `Double` `Decimal` `Integer` `Long` `Object` `SByte` `Short` , `Single` ,, `String` `UInteger` , `ULong` , i `UShort` ).|  
|`expressionlist`|Wymagane w `Case` instrukcji. Lista klauzul wyrażeń reprezentujących wartości dopasowania dla elementu `testexpression` . Wielokrotne klauzule wyrażenia są rozdzielone przecinkami. Każda klauzula może przyjmować jedną z następujących form:<br /><br /> -   *wyrażenie1* `To` *wyrażenie2*<br />-[ `Is` ] *comparisonoperator* *wyrażenie* operatorporównania<br />-   *wyrażenia*<br /><br /> Użyj `To` słowa kluczowego, aby określić granice zakresu pasujących wartości dla `testexpression` . Wartość `expression1` musi być mniejsza lub równa wartości `expression2` .<br /><br /> Użyj `Is` słowa kluczowego z operatorem porównania ( `=` ,,,, `<>` `<` `<=` `>` lub `>=` ), aby określić ograniczenie dla wartości dopasowania dla `testexpression` . Jeśli `Is` słowo kluczowe nie jest dostarczone, jest automatycznie wstawiane przed *operatorporównania*.<br /><br /> Formularz określający tylko `expression` jest traktowany jako specjalny przypadek formularza, `Is` gdzie *operatorporównania* jest znakiem równości ( `=` ). Ten formularz jest oceniany jako `testexpression`  =  `expression` .<br /><br /> Wyrażenia w `expressionlist` może być dowolnego typu danych, pod warunkiem, że są one niejawnie konwertowane na typ `testexpression` i są odpowiednie dla dwóch typów, które są `comparisonoperator` używane w.|  
|`statements`|Opcjonalny. Co najmniej jedna instrukcja `Case` , która jest uruchamiana, jeśli `testexpression` pasuje do dowolnej klauzuli w `expressionlist` .|  
|`elsestatements`|Opcjonalny. Co najmniej jedna instrukcja `Case Else` uruchamiana, jeśli `testexpression` nie jest zgodna z żadną klauzulą w `expressionlist` żadnej z `Case` instrukcji.|  
|`End Select`|Kończy definicję konstruowania.. `Select` .. `Case`|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `testexpression` dopasowuje dowolną `Case` `expressionlist` klauzulę, instrukcje po tej `Case` instrukcji są uruchamiane do następnej `Case` `Case Else` instrukcji,, lub `End Select` . Następnie kontrolka przechodzi do następującej instrukcji `End Select` . Jeśli `testexpression` jest zgodny z `expressionlist` klauzulą w więcej niż jednej `Case` klauzuli, tylko instrukcje po pierwszym uruchomieniu są wykonywane.  
  
 `Case Else`Instrukcja jest używana do wprowadzenia `elsestatements` do uruchomienia, jeśli nie zostanie znalezione dopasowanie między `testexpression` `expressionlist` klauzulą a klauzuli w żadnej z innych `Case` instrukcji. Chociaż nie jest to wymagane, dobrym pomysłem jest posiadanie `Case Else` instrukcji w `Select Case` konstrukcji do obsługi nieprzewidzianych `testexpression` wartości. Jeśli żadna `Case` `expressionlist` klauzula nie `testexpression` jest zgodna i nie ma żadnej `Case Else` instrukcji, kontrola przechodzi do następującej instrukcji `End Select` .  
  
 W każdej klauzuli można używać wielu wyrażeń lub zakresów `Case` . Na przykład następujący wiersz jest prawidłowy.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> `Is`Słowo kluczowe używane w `Case` `Case Else` instrukcjach i nie jest takie samo jak [operator is](../operators/is-operator.md), który jest używany do porównywania odwołań do obiektów.  
  
 Można określić zakresy i wiele wyrażeń dla ciągów znaków. W poniższym przykładzie `Case` dopasowuje dowolny ciąg, który jest dokładnie równy "jabłek", ma wartość między "NUTS" i "zup" w kolejności alfabetycznej lub zawiera dokładną wartość taką samą jak bieżąca wartość `testItem` .  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Ustawienie `Option Compare` może mieć wpływ na porównania ciągów. W obszarze `Option Compare Text` ciągi "jabłka" i "jabłka" są porównywane jako równe, ale w obszarze `Option Compare Binary` nie są.  
  
> [!NOTE]
> `Case`Instrukcja z wieloma klauzulami może wykazywać zachowanie znane jako *krótkie obwody*. Visual Basic oblicza klauzule od lewej do prawej, a jeśli jeden generuje dopasowanie z `testexpression` , pozostałe klauzule nie są oceniane. Krótkie obwody mogą zwiększyć wydajność, ale może generować nieoczekiwane wyniki, jeśli oczekuje się, że każde wyrażenie w `expressionlist` jest oceniane. Aby uzyskać więcej informacji na temat skracania obwodów, zobacz [wyrażenia logiczne](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Jeśli kod w `Case` `Case Else` bloku instrukcji lub nie musi uruchamiać żadnych więcej instrukcji w bloku, może wyjść z bloku przy użyciu `Exit Select` instrukcji. Powoduje to natychmiastowe przeniesienie kontroli do poniższej instrukcji `End Select` .  
  
 `Select Case`konstrukcje mogą być zagnieżdżane. Każda konstrukcja zagnieżdżona `Select Case` musi mieć zgodną `End Select` instrukcję i musi być całkowicie zawarta w obrębie pojedynczego `Case` lub `Case Else` bloku instrukcji `Select Case` konstrukcji zewnętrznej, w ramach której jest zagnieżdżony.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa konstrukcji, `Select Case` Aby napisać linię odpowiadającą wartości zmiennej `number` . Druga `Case` instrukcja zawiera wartość, która pasuje do bieżącej wartości `number` , więc instrukcji, która zapisuje "od 6 do 8 włącznie".  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End — instrukcja](end-statement.md)
- [If...Then...Else, instrukcja](if-then-else-statement.md)
- [Option Compare — Instrukcja](option-compare-statement.md)
- [Exit, instrukcja](exit-statement.md)
