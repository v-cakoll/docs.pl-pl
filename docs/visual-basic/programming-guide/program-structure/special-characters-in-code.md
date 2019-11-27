---
title: Znaki specjalne w kodzie
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
ms.openlocfilehash: f4ab35b56d48ae86bdb024ffea27735b39decdc2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347266"
---
# <a name="special-characters-in-code-visual-basic"></a>Znaki specjalne w Code (Visual Basic)
Czasami musisz używać znaków specjalnych w kodzie, czyli znaków, które nie są alfabetyczne ani liczbowe. Znaki interpunkcyjne i specjalne w zestawie znaków Visual Basic mają różne zastosowania, od porządkowania tekstu programu do definiowania zadań wykonywanych przez kompilator lub skompilowany program. Nie określają operacji do wykonania.  
  
## <a name="parentheses"></a>nawiasów  
 Użyj nawiasów podczas definiowania procedury, takiej jak `Sub` lub `Function`. Wszystkie listy argumentów procedury należy ująć w nawiasy. Należy również użyć nawiasów do umieszczania zmiennych lub argumentów w grupach logicznych, szczególnie w celu zastąpienia domyślnej kolejności operatorów w wyrażeniu złożonym. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 Po wykonaniu poprzedniego kodu wartość `d` to 8,225, a wartość `e` to 3. Obliczenie dla `d` używa domyślnego pierwszeństwa `/` przez `+` i jest równoważne z `d = b + (c / a)`. Nawiasy w obliczaniu `e` przesłaniają domyślne pierwszeństwo.  
  
## <a name="separators"></a>Separatorach  
 Separatory służą do jej sugerowania: oddzielą sekcje kodu. W Visual Basic znak separatora jest dwukropek (`:`). Użyj separatorów, gdy chcesz uwzględnić wiele instrukcji w pojedynczym wierszu, a nie w osobnych wierszach. Pozwala to zaoszczędzić miejsce i zwiększa czytelność kodu. Poniższy przykład przedstawia trzy instrukcje oddzielone średnikami.  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 Znak dwukropka (`:`) jest również używany do identyfikowania etykiety instrukcji. Aby uzyskać więcej informacji, zobacz [instrukcje: etykietowanie instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Połączenie (konkatenacja)  
 Użyj operatora `&` do *łączenia*lub łączenia ciągów razem. Nie należy mylić z operatorem `+`, który dodaje razem wartości liczbowe. Jeśli używasz operatora `+`, aby łączyć się podczas wykonywania operacji na wartościach liczbowych, możesz uzyskać nieprawidłowe wyniki. Poniższy przykład ilustruje to.  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 Po wykonaniu poprzedniego kodu wartością `resultA` jest 21,01, a wartością `resultB` jest "10,0111".  
  
## <a name="member-access-operators"></a>Operatory dostępu do elementów członkowskich  
 Aby uzyskać dostęp do elementu członkowskiego typu, należy użyć operatora kropki (`.`) lub wykrzyknika (`!`) między nazwą typu a nazwą elementu członkowskiego.  
  
### <a name="dot--operator"></a>Kropka (.) Zakład  
 Użyj operatora `.` w klasie, strukturze, interfejsie lub wyliczenia jako operator dostępu do składowych. Składową może być pole, właściwość, zdarzenie lub metoda. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>Wykrzyknik (!) Zakład  
 Operatora `!` należy używać tylko w klasie lub interfejsie jako operator dostępu do słownika. Klasa lub interfejs musi mieć właściwość domyślną, która akceptuje pojedynczy argument `String`. Identyfikator bezpośrednio po operatorze `!` będzie wartością argumentu przekazaną do domyślnej właściwości jako ciąg. Poniższy przykład ilustruje to.  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 Trzy wiersze wyjściowe `MsgBox` wszystkie wyświetlają `32856`wartości. Pierwszy wiersz używa tradycyjnego dostępu do właściwości `index`, drugi korzysta z faktu, że `index` jest właściwością domyślną klasy `hasDefault`, a trzeci używa dostępu do słownika do klasy.  
  
 Należy zauważyć, że drugi operand operatora `!` musi być prawidłowym identyfikatorem Visual Basic, który nie jest ujęty w znaki podwójnego cudzysłowu (`" "`). Innymi słowy, nie można użyć literału ciągu ani zmiennej ciągu. Następująca zmiana w ostatnim wierszu wywołania `MsgBox` generuje błąd, ponieważ `"X"` jest ujętą w nawias literał ciągu.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> Odwołania do kolekcji domyślnych muszą być jawne. W szczególności nie można użyć operatora `!` na zmiennej z późnym wiązaniem.  
  
 Znak `!` jest również używany jako znak typu `Single`.  
  
## <a name="see-also"></a>Zobacz także

- [Struktura programu i konwencje związane z kodami](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Znaki typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
