---
title: Znaki specjalne w Code (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: 95bef937912e35cd828bf0090b4cf48ccb3290cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962467"
---
# <a name="special-characters-in-code-visual-basic"></a>Znaki specjalne w Code (Visual Basic)
Czasami musisz używać znaków specjalnych w kodzie, czyli znaków, które nie są alfabetyczne ani liczbowe. Znaki interpunkcyjne i specjalne w zestawie znaków Visual Basic mają różne zastosowania, od porządkowania tekstu programu do definiowania zadań wykonywanych przez kompilator lub skompilowany program. Nie określają operacji do wykonania.  
  
## <a name="parentheses"></a>Nawiasów  
 Użyj nawiasów podczas definiowania procedury, takiej jak `Sub` lub. `Function` Wszystkie listy argumentów procedury należy ująć w nawiasy. Należy również użyć nawiasów do umieszczania zmiennych lub argumentów w grupach logicznych, szczególnie w celu zastąpienia domyślnej kolejności operatorów w wyrażeniu złożonym. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 Po wykonaniu poprzedniego kodu wartość `d` jest 8,225, a `e` wartość to 3. Obliczenie dla `d` używa domyślnego `/` pierwszeństwa względem `+` i jest równoważne z `d = b + (c / a)`. Nawiasy w obliczeniach dla `e` zastąpienia domyślnego pierwszeństwa.  
  
## <a name="separators"></a>Separatorach  
 Separatory służą do jej sugerowania: oddzielą sekcje kodu. W Visual Basic znak separatora jest dwukropek (`:`). Użyj separatorów, gdy chcesz uwzględnić wiele instrukcji w pojedynczym wierszu, a nie w osobnych wierszach. Pozwala to zaoszczędzić miejsce i zwiększa czytelność kodu. Poniższy przykład przedstawia trzy instrukcje oddzielone średnikami.  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Przerywanie i łączenie instrukcji w](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)kodzie.  
  
 Znak dwukropka (`:`) jest również używany do identyfikowania etykiety instrukcji. Aby uzyskać więcej informacji, zobacz [jak: Instrukcje](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)etykiet.  
  
## <a name="concatenation"></a>Połączenie (konkatenacja)  
 Użyj operatora do łączenia lub łączenia ciągów razem. `&` Nie należy mylić tego `+` operatora z operatorem, który dodaje razem wartości liczbowe. Jeśli używasz `+` operatora do łączenia podczas wykonywania operacji na wartościach liczbowych, możesz uzyskać nieprawidłowe wyniki. Poniższy przykład ilustruje to.  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 Po wykonaniu poprzedniego kodu wartością `resultA` jest 21,01, a `resultB` wartością jest "10,0111".  
  
## <a name="member-access-operators"></a>Operatory dostępu do elementów członkowskich  
 Aby uzyskać dostęp do elementu członkowskiego typu, należy użyć operatora kropki (`.`) lub wykrzyknika (`!`) między nazwą typu a nazwą elementu członkowskiego.  
  
### <a name="dot--operator"></a>Kropka (.) Operator  
 `.` Użyj operatora dla klasy, struktury, interfejsu lub wyliczenia jako operatora dostępu do elementu członkowskiego. Składową może być pole, właściwość, zdarzenie lub metoda. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>Wykrzyknik (!) Operator  
 `!` Operatora należy używać tylko w klasie lub interfejsie jako operator dostępu do słownika. Klasa lub interfejs musi mieć właściwość domyślną, która akceptuje pojedynczy `String` argument. Identyfikator bezpośrednio po `!` operatorze będzie wartością argumentu przekazaną do domyślnej właściwości jako ciąg. Poniższy przykład ilustruje to.  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 Trzy wiersze `MsgBox` wyjściowe wszystkich wyświetlają wartość `32856`. Pierwszy wiersz używa tradycyjnego dostępu do właściwości `index`, drugi korzysta z faktu, że `index` jest domyślną właściwością klasy `hasDefault`, a trzeci używa dostępu do słownika do klasy.  
  
 Należy zauważyć, że drugi operand `!` operatora musi być prawidłowym identyfikatorem Visual Basic, który nie jest ujęty w znaki podwójnego cudzysłowu (`" "`). Innymi słowy, nie można użyć literału ciągu ani zmiennej ciągu. Następująca zmiana w ostatnim wierszu `MsgBox` wywołania powoduje wygenerowanie błędu, ponieważ `"X"` jest to ujęty w nawias literał ciągu.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> Odwołania do kolekcji domyślnych muszą być jawne. W szczególności nie można używać `!` operatora na zmiennej z późnym wiązaniem.  
  
 Znak jest również używany `Single` jako znak typu. `!`  
  
## <a name="see-also"></a>Zobacz także

- [Konwencje dotyczące struktury programów i kodu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Znaki typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
