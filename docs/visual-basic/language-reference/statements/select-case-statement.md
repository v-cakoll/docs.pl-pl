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
ms.openlocfilehash: f99db4f1dc224e5f75ee67ba94c3745f28438724
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814617"
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
|`testexpression`|Wymagana. wyrażenie. Musi być jednym z typów podstawowych danych (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, i `UShort`).|  
|`expressionlist`|Wymagane w `Case` instrukcji. Lista klauzule wyrażenia reprezentujących wartości dopasowanie `testexpression`. Wiele klauzul wyrażenia są oddzielone przecinkami. Każdej klauzuli może mieć jedną z następujących form:<br /><br /> -   *wyrażenie1* `To` *wyrażenie2*<br />-[ `Is` ] *OperatorPorównania* *wyrażenia*<br />-   *expression*<br /><br /> Użyj `To` — słowo kluczowe, aby określić granice zakresu dopasowania wartości `testexpression`. Wartość `expression1` musi być mniejsza niż wartość `expression2`.<br /><br /> Użyj `Is` — słowo kluczowe za pomocą operatora porównania (`=`, `<>`, `<`, `<=`, `>`, lub `>=`) można określić ograniczenie wartości dopasowanie `testexpression`. Jeśli `Is` — słowo kluczowe nie jest podany, jest automatycznie wstawiany przed *OperatorPorównania*.<br /><br /> Formularz, określając tylko `expression` jest traktowany jako w wyjątkowym przypadku okna `Is` tworzą gdzie *OperatorPorównania* jest znak równości (`=`). Ta forma jest oceniane jako `testexpression`  =  `expression`.<br /><br /> Wyrażenia w `expressionlist` mogą być dowolnego typu danych, pod warunkiem że są one niejawnie konwertowane na typ `testexpression` i odpowiednie `comparisonoperator` nadaje się do dwóch typów jest używany z.|  
|`statements`|Opcjonalna. Jeden lub więcej następujących instrukcji `Case` wykonywania Jeśli `testexpression` pasuje do żadnej klauzuli w `expressionlist`.|  
|`elsestatements`|Opcjonalna. Jeden lub więcej następujących instrukcji `Case Else` wykonywania Jeśli `testexpression` nie odpowiada żadnej klauzuli w `expressionlist` któregokolwiek z `Case` instrukcji.|  
|`End Select`|Kończy definicję `Select`... `Case` konstrukcji.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `testexpression` pasuje do żadnej `Case` `expressionlist` klauzuli, instrukcje po `Case` instrukcji uruchomić maksymalnie do następnego `Case`, `Case Else`, lub `End Select` instrukcji. Następnie sterowanie przechodzi do instrukcji następującej `End Select`. Jeśli `testexpression` odpowiada `expressionlist` klauzuli w więcej niż jednym `Case` klauzuli tylko instrukcje po pierwsze dopasowanie są wykonywane.  
  
 `Case Else` Instrukcja jest używane do wprowadzenia `elsestatements` do uruchomienia, jeśli nie zostanie znalezione dopasowanie między `testexpression` i `expressionlist` klauzuli w żadnym innym `Case` instrukcji. Chociaż nie jest to wymagane, to dobry pomysł, aby mieć `Case Else` instrukcji w swojej `Select Case` konstrukcji, aby obsłużyć nieprzewidziane `testexpression` wartości. Jeśli nie `Case` `expressionlist` pasuje do klauzuli `testexpression` i ma nie `Case Else` instrukcji, kontrola przechodzi do następujących instrukcji `End Select`.  
  
 Można użyć wielu wyrażeń lub zakresów, które znajdują się w każdym `Case` klauzuli. Na przykład poniższy wiersz jest prawidłowy.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  `Is` Słowo kluczowe użyte w `Case` i `Case Else` instrukcji nie jest taka sama jak [operatora Is](../../../visual-basic/language-reference/operators/is-operator.md), używany do porównania odwołanie do obiektu.  
  
 Można określić zakresy i wiele wyrażeń dla ciągów znaków. W poniższym przykładzie `Case` dopasowuje dowolny ciąg, który jest dokładnie taka sama jak "apples", wartość z zakresu od "nuts" i "od początku" w kolejności alfabetycznej lub zawiera dokładnie tę samą wartość jak bieżąca wartość `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Ustawienie `Option Compare` mogą mieć wpływ na porównywania ciągów. W obszarze `Option Compare Text`, porównywane ciągi są "Apples" i "apples" jako równe, ale opcja `Option Compare Binary`, nie ma.  
  
> [!NOTE]
>  A `Case` instrukcji z wieloma klauzulami może cechować się zachowanie nazywane *zwarcie*. Visual Basic ocenia klauzule od lewej do prawej, a jeśli jedną daje zgodna z `testexpression`, pozostałe klauzule nie są sprawdzane. Zwarcie może poprawić wydajność, ale mogą dawać nieoczekiwane wyniki, jeśli są oczekiwane każde wyrażenie w `expressionlist` ma zostać obliczone. Aby uzyskać więcej informacji na temat zwarcie, zobacz [wyrażeń logicznych](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Jeśli kod w `Case` lub `Case Else` blok instrukcji nie jest konieczne uruchamianie żadnych dodatkowych instrukcji w bloku, je zamknąć blok przy użyciu `Exit Select` instrukcji. Ten formant natychmiast przenosi do następujących instrukcji `End Select`.  
  
 `Select Case` konstrukcje mogą być zagnieżdżone. Każda zagnieżdżona `Select Case` konstrukcja musi mieć zgodną `End Select` instrukcji i musi być całkowicie zawarty w obrębie pojedynczego `Case` lub `Case Else` blok instrukcji zewnętrznego `Select Case` konstrukcji, w którym jest zagnieżdżony.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Select Case` konstrukcji do zapisania wiersz odpowiadający wartości zmiennej `number`. Drugi `Case` instrukcja zawiera wartość, która pasuje do bieżącej wartości `number`, więc instrukcję, która zapisuje "na od 6 do 8 (włącznie)" jest uruchamiana.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [Instrukcja End](../../../visual-basic/language-reference/statements/end-statement.md)
- [Dyrektywa #If...Then...#Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare, instrukcja](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit, instrukcja](../../../visual-basic/language-reference/statements/exit-statement.md)
