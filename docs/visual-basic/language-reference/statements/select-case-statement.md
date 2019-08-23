---
title: Select...Case — Instrukcja (Visual Basic)
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
ms.openlocfilehash: 627318677270ba4ffa8ee430febea7ddf83bd245
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957644"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case — Instrukcja (Visual Basic)
Uruchamia jedną z kilku grup instrukcji w zależności od wartości wyrażenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`testexpression`|Wymagany. Wyrażenia. Należy oszacować do`Boolean`jednego z podstawowych typów danych (, `Decimal` `Double` `Byte` `Date` `Char` ,`SByte` ,`Short`,,,,,,,, `Integer` `Long` `Object` `Single`, ,`String` ,i`UShort`). `UInteger` `ULong`|  
|`expressionlist`|Wymagane w `Case` instrukcji. Lista klauzul wyrażeń reprezentujących wartości dopasowania dla `testexpression`elementu. Wielokrotne klauzule wyrażenia są rozdzielone przecinkami. Każda klauzula może przyjmować jedną z następujących form:<br /><br /> -   *wyrażenie1* `To` *wyrażenie2*<br />-[ `Is` ] *wyrażenie* operatorporównania<br />-   *wyrażenia*<br /><br /> Użyj słowa `To` kluczowego, aby określić granice zakresu pasujących wartości dla `testexpression`. Wartość `expression1` musi być mniejsza lub równa `expression2`wartości.<br /><br /> `<` `<=` `<>` `>` `>=`Użyj słowa kluczowego z operatorem porównania`=`(,,,, lub), aby określić ograniczenie dla wartości dopasowania dla `testexpression`. `Is` Jeśli słowo kluczowe nie jest dostarczone, jest automatycznie wstawiane przed *operatorporównania.* `Is`<br /><br /> Formularz określający tylko `expression` jest traktowany jako specjalny przypadek formularza, `Is` gdzie *operatorporównania* jest znakiem równości (`=`). Ten formularz jest oceniany `testexpression`jako  =  `expression`.<br /><br /> Wyrażenia w `expressionlist` może być dowolnego typu danych, pod warunkiem, że są one niejawnie konwertowane na `testexpression` typ i są `comparisonoperator` odpowiednie dla dwóch typów, które są używane w.|  
|`statements`|Opcjonalny. Co najmniej jedna instrukcja `Case` , która jest uruchamiana, jeśli `testexpression` pasuje `expressionlist`do dowolnej klauzuli w.|  
|`elsestatements`|Opcjonalna. `Case Else` Co najmniej jedna instrukcja uruchamiana, jeśli `testexpression` nie jest `expressionlist` zgodna z żadną klauzulą w żadnej `Case` z instrukcji.|  
|`End Select`|Kończy definicję `Select`... `Case` konstrukcja.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `testexpression` dopasowuje `Case` dowolną `Case` `Case Else` `End Select` klauzulę, instrukcje po `Case` tej instrukcji są uruchamiane do następnej instrukcji,, lub. `expressionlist` Następnie kontrolka przechodzi do następującej `End Select`instrukcji. Jeśli `testexpression` jest zgodny `expressionlist` z klauzulą w więcej `Case` niż jednej klauzuli, tylko instrukcje po pierwszym uruchomieniu są wykonywane.  
  
 `testexpression` `elsestatements` `Case` `expressionlist` Instrukcja jest używana do wprowadzenia do uruchomienia, jeśli nie zostanie znalezione dopasowanie między klauzulą a klauzuli w żadnej z innych instrukcji. `Case Else` Chociaż nie jest to wymagane, dobrym pomysłem jest posiadanie `Case Else` instrukcji `Select Case` w konstrukcji do obsługi nieprzewidzianych `testexpression` wartości. Jeśli żadna `Case` klauzula nie `expressionlist` jest zgodna `testexpression` i nie `Case Else` ma żadnej instrukcji, kontrola przechodzi do następującej `End Select`instrukcji.  
  
 W każdej `Case` klauzuli można używać wielu wyrażeń lub zakresów. Na przykład następujący wiersz jest prawidłowy.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> Słowo kluczowe używane `Case` w instrukcjach `Case Else` i nie jest takie samo jak [operator is](../../../visual-basic/language-reference/operators/is-operator.md), który jest używany do porównywania odwołań do obiektów. `Is`  
  
 Można określić zakresy i wiele wyrażeń dla ciągów znaków. W poniższym przykładzie `Case` dopasowuje dowolny ciąg, który jest dokładnie równy "jabłek", ma wartość między "NUTS" i "zup" w kolejności alfabetycznej lub zawiera dokładną wartość taką samą jak bieżąca `testItem`wartość.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Ustawienie `Option Compare` może mieć wpływ na porównania ciągów. W `Option Compare Text`obszarze ciągi "jabłka" i "jabłka" są porównywane jako równe, ale `Option Compare Binary`w obszarze nie są.  
  
> [!NOTE]
> Instrukcja z wieloma klauzulami może wykazywać zachowanie znane jako *krótkie obwody.* `Case` Visual Basic oblicza klauzule od lewej do prawej, a jeśli jeden generuje dopasowanie z `testexpression`, pozostałe klauzule nie są oceniane. Krótkie obwody mogą zwiększyć wydajność, ale może generować nieoczekiwane wyniki, jeśli oczekuje się, że każde wyrażenie `expressionlist` w jest oceniane. Aby uzyskać więcej informacji na temat skracania obwodów, zobacz [wyrażenia logiczne](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Jeśli kod w `Case` bloku instrukcji lub `Case Else` nie musi uruchamiać żadnych więcej instrukcji w bloku, może wyjść `Exit Select` z bloku przy użyciu instrukcji. Powoduje to natychmiastowe przeniesienie kontroli do poniższej `End Select`instrukcji.  
  
 `Select Case`konstrukcje mogą być zagnieżdżane. Każda konstrukcja `Select Case` zagnieżdżona musi mieć zgodną `End Select` instrukcję i musi być całkowicie zawarta `Case` w `Case Else` obrębie pojedynczego lub bloku instrukcji `Select Case` konstrukcji zewnętrznej, w ramach której jest zagnieżdżony.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Select Case` konstrukcji, aby napisać linię odpowiadającą wartości zmiennej `number`. Druga `Case` instrukcja zawiera wartość, która pasuje do bieżącej `number`wartości, więc instrukcji, która zapisuje "od 6 do 8 włącznie".  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [Instrukcja End](../../../visual-basic/language-reference/statements/end-statement.md)
- [Dyrektywa #If...Then...#Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare, instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
