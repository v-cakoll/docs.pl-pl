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
ms.openlocfilehash: d035118febc5ea9d1ea8e5cc0145cb030626b030
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583249"
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
|`testexpression`|Wymagany. Wyrażenia. Należy oszacować do jednego z podstawowych typów danych (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, 0, 1, 2 , 3, 4 i 5).|  
|`expressionlist`|Wymagane w instrukcji `Case`. Lista klauzul wyrażeń reprezentujących wartości dopasowania dla `testexpression`. Wielokrotne klauzule wyrażenia są rozdzielone przecinkami. Każda klauzula może przyjmować jedną z następujących form:<br /><br /> -   *wyrażenie1* `To` *wyrażenie2*<br />-[`Is`] *wyrażenie* operatorporównania<br />*wyrażenie* -   <br /><br /> Użyj słowa kluczowego `To`, aby określić granice zakresu pasujących wartości dla `testexpression`. Wartość `expression1` musi być mniejsza lub równa wartości `expression2`.<br /><br /> Użyj słowa kluczowego `Is` z operatorem porównania (`=`, `<>`, `<`, `<=`, `>` lub `>=`), aby określić ograniczenie wartości dopasowywania dla `testexpression`. Jeśli nie podano słowa kluczowego `Is`, zostanie ono automatycznie wstawione przed *operatorporównania*.<br /><br /> Formularz określający tylko `expression` jest traktowany jako specjalny przypadek formularza `Is`, gdzie *operatorporównania* jest znakiem równości (`=`). Ten formularz jest oceniany jako `testexpression`  =  `expression`.<br /><br /> Wyrażenia w `expressionlist` mogą być dowolnego typu danych, pod warunkiem, że są niejawnie konwertowane na typ `testexpression` i odpowiednie `comparisonoperator` są prawidłowe dla dwóch typów, z których jest używana.|  
|`statements`|Opcjonalny. Co najmniej jednej instrukcji, która jest wykonywana `Case`, jeśli `testexpression` dopasowuje dowolną klauzulę w `expressionlist`.|  
|`elsestatements`|Opcjonalny. Co najmniej jednej instrukcji, która jest wykonywana `Case Else`, jeśli `testexpression` nie pasuje do żadnej klauzuli w `expressionlist` żadnej instrukcji `Case`.|  
|`End Select`|Kończy definicję `Select`... `Case` konstrukcja.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `testexpression` dopasowuje dowolną klauzulę `expressionlist` `Case`, instrukcje następujące po instrukcji `Case` są uruchamiane do następnej instrukcji `Case`, `Case Else` lub `End Select`. Następnie formant przekazuje do instrukcji następującej po `End Select`. Jeśli `testexpression` jest zgodna z klauzulą `expressionlist` w więcej niż jednej klauzuli `Case`, tylko instrukcje po pierwszym uruchomieniu.  
  
 Instrukcja `Case Else` służy do wprowadzenia `elsestatements` do uruchomienia, jeśli nie zostanie znalezione dopasowanie między `testexpression` i klauzulą `expressionlist` w żadnej z innych instrukcji `Case`. Chociaż nie jest to wymagane, dobrym pomysłem jest posiadanie instrukcji `Case Else` w konstrukcji `Select Case` do obsługi nieprzewidzianych wartości `testexpression`. Jeśli klauzula `expressionlist` `Case` nie pasuje do `testexpression` i nie ma żadnej instrukcji `Case Else`, kontrola przechodzi do instrukcji następującej po `End Select`.  
  
 W każdej klauzuli `Case` można używać wielu wyrażeń lub zakresów. Na przykład następujący wiersz jest prawidłowy.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> Słowo kluczowe `Is` używane w instrukcjach `Case` i `Case Else` nie jest takie samo jak [operator is](../../../visual-basic/language-reference/operators/is-operator.md), który jest używany do porównywania odwołań do obiektów.  
  
 Można określić zakresy i wiele wyrażeń dla ciągów znaków. W poniższym przykładzie `Case` dopasowuje dowolny ciąg, który jest dokładnie równy "jabłek", ma wartość między "NUTS" i "zup" w kolejności alfabetycznej lub zawiera dokładną wartość taką samą jak bieżąca wartość `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Ustawienie `Option Compare` może wpływać na porównania ciągów. W obszarze `Option Compare Text` ciągi "jabłka" i "jabłka" są porównywane jako równe, ale w obszarze `Option Compare Binary`, nie.  
  
> [!NOTE]
> Instrukcja `Case` z wieloma klauzulami może wykazywać zachowanie znane jako *krótkie obwody*. Visual Basic oblicza klauzule od lewej do prawej, a jeśli jeden generuje dopasowanie z `testexpression`, pozostałe klauzule nie są oceniane. Krótkie obwody mogą zwiększyć wydajność, ale może generować nieoczekiwane wyniki, jeśli oczekuje się, że każde wyrażenie w `expressionlist` ma zostać ocenione. Aby uzyskać więcej informacji na temat skracania obwodów, zobacz [wyrażenia logiczne](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Jeśli kod w bloku instrukcji `Case` lub `Case Else` nie musi uruchamiać żadnych więcej instrukcji w bloku, może wyjść z bloku przy użyciu instrukcji `Exit Select`. Spowoduje to natychmiastowe przeniesienie kontroli do instrukcji następującej `End Select`.  
  
 Konstrukcje `Select Case` mogą być zagnieżdżane. Każda konstrukcja zagnieżdżonych `Select Case` musi mieć zgodną instrukcję `End Select` i musi być całkowicie zawarta w pojedynczym `Case` lub `Case Else` bloku instrukcji elementu zewnętrznego `Select Case`, w ramach którego jest zagnieżdżony.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa konstrukcji `Select Case`, aby napisać linię odpowiadającą wartości zmiennej `number`. Druga instrukcja `Case` zawiera wartość, która jest zgodna z bieżącą wartością `number`, więc instrukcji, która zapisuje "od 6 do 8 włącznie".  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End, instrukcja](../../../visual-basic/language-reference/statements/end-statement.md)
- [If...Then...Else, instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare, instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
