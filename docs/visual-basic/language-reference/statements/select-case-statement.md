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
ms.openlocfilehash: 9d24b455d92cbd00b268df26283aab082b7703a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case — Instrukcja (Visual Basic)
Uruchamia jedną lub kilka grup instrukcji w zależności od wartości wyrażenia.  
  
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
|`testexpression`|Wymagana. Wyrażenie. Musi być jednego z typów podstawowych danych (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, i `UShort`).|  
|`expressionlist`|Wymagane w `Case` instrukcji. Lista klauzule wyrażenia reprezentujący dopasowania wartości `testexpression`. Wiele klauzule wyrażenia są oddzielone przecinkami. Każdej klauzuli można wykonać jedną z następujących formatów:<br /><br /> -   *wyrażenie1* `To` *wyrażenie2*<br />— [ `Is` ] *OperatorPorównania* *wyrażenia*<br />-   *wyrażenie*<br /><br /> Użyj `To` — słowo kluczowe, aby określić granice zakresu dopasowania wartości `testexpression`. Wartość `expression1` musi być mniejsza niż wartość `expression2`.<br /><br /> Użyj `Is` — słowo kluczowe z operatora porównania (`=`, `<>`, `<`, `<=`, `>`, lub `>=`) do określenia ograniczenie dla wartości dopasowania `testexpression`. Jeśli `Is` — słowo kluczowe nie jest podany, automatycznie dodaje się go przed *OperatorPorównania*.<br /><br /> Formularz, określając tylko `expression` jest traktowany jako specjalny przypadek `Is` tworzą where *OperatorPorównania* jest znak równości (`=`). Ten formularz jest szacowana jako `testexpression`  =  `expression`.<br /><br /> Wyrażenia w `expressionlist` może być dowolnego typu danych, zakładając, że są one umożliwiają niejawnej konwersji na typ `testexpression` i odpowiednie `comparisonoperator` jest prawidłowy dla dwóch typów jest używany z.|  
|`statements`|Opcjonalna. Jeden lub więcej następujących instrukcji `Case` wykonywania Jeśli `testexpression` odpowiada klauzuli w `expressionlist`.|  
|`elsestatements`|Opcjonalna. Jeden lub więcej następujących instrukcji `Case Else` wykonywania Jeśli `testexpression` jest niezgodny z klauzuli w `expressionlist` któregokolwiek z `Case` instrukcje.|  
|`End Select`|Kończy definicję `Select`... `Case` konstrukcji.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `testexpression` zgodny z dowolnym `Case` `expressionlist` klauzuli, instrukcje po `Case` instrukcji uruchamiany do następnego `Case`, `Case Else`, lub `End Select` instrukcji. Kontrola następnie przechodzi do instrukcji następującej `End Select`. Jeśli `testexpression` odpowiada `expressionlist` klauzuli w więcej niż jednym `Case` Uruchom tylko instrukcje po pierwsze dopasowanie klauzuli.  
  
 `Case Else` Wprowadzenie używana jest instrukcja `elsestatements` do uruchomienia, jeśli nie znaleziono między `testexpression` i `expressionlist` klauzuli w żadnym innym `Case` instrukcje. Mimo że nie jest to wymagane, to warto mieć `Case Else` instrukcji w Twojej `Select Case` konstrukcji, aby obsłużyć nieprzewidzianego `testexpression` wartości. Jeśli nie `Case` `expressionlist` odpowiada klauzuli `testexpression` i ma nie `Case Else` instrukcji sterowania przekazywany do instrukcji następującej `End Select`.  
  
 Można użyć wielu wyrażeń lub zakresów w każdym `Case` klauzuli. Na przykład następujący wiersz jest nieprawidłowy.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  `Is` Słowo kluczowe użyte w `Case` i `Case Else` instrukcji nie jest taka sama jak [operatora Is](../../../visual-basic/language-reference/operators/is-operator.md), które jest używane dla obiekt porównanie odwołań.  
  
 Można określić zakresy i wiele wyrażeń dla ciągów znaków. W poniższym przykładzie `Case` dopasowuje dowolny ciąg, są dokładnie takie same "jabłek", ma wartość z zakresu od "nuts" i "zup" w kolejności alfabetycznej lub zawiera dokładnie samą wartość, jak bieżąca wartość `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Ustawienie `Option Compare` mogą mieć wpływ na porównywanie ciągów. W obszarze `Option Compare Text`, ciągi "Jabłek" i "jabłek" porównania jako równe, ale w obszarze `Option Compare Binary`, nie ma.  
  
> [!NOTE]
>  A `Case` instrukcji z wielu klauzul można zachowują znany jako *zwarcie*. Visual Basic ocenia klauzule od lewej do prawej, a jeśli tworzy dopasowania `testexpression`, pozostałe klauzule nie są sprawdzane. Zwarcie może zwiększyć wydajność, ale może spowodować nieoczekiwane wyniki, jeśli są oczekiwane co wyrażenie w `expressionlist` ma zostać obliczone. Aby uzyskać więcej informacji dotyczących zwarcie, zobacz [wyrażeń logicznych](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Jeśli kod w `Case` lub `Case Else` blok instrukcji nie trzeba uruchamiać więcej oświadczeń w bloku, go zamknąć bloku przy użyciu `Exit Select` instrukcji. Ten formant natychmiast przenosi do instrukcji następującej `End Select`.  
  
 `Select Case` konstrukcje mogą być zagnieżdżone. Każdy zagnieżdżone `Select Case` konstrukcji musi mieć zgodną `End Select` instrukcji i musi być całkowicie zawarty w jednym `Case` lub `Case Else` blok instrukcji zewnętrznego `Select Case` konstrukcji, w którym jest zagnieżdżony.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select Case` konstrukcji do zapisywania wiersza odpowiadającą wartości zmiennej `number`. Drugi `Case` instrukcja zawiera wartość odpowiadającą bieżącej wartości `number`, więc instrukcji, która zapisuje "od 6 do 8 włącznie" jest uruchamiana.  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)  
 [If...Then...Else, instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Option Compare, instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
