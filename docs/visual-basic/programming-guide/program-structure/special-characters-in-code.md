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
ms.openlocfilehash: 1541ac1793c9f3c082b688fecd4eb82fb5b59590
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726731"
---
# <a name="special-characters-in-code-visual-basic"></a>Znaki specjalne w Code (Visual Basic)
Czasami trzeba używać znaków specjalnych w kodzie, czyli niedozwolone znaki numeryczne lub alfabetycznego. Interpunkcja i znaki specjalne w zestawie znaków języka Visual Basic mają różne przypadki z organizowania tekstu do definiowania zadań, które kompilator lub skompilowany program wykonuje. Nie należy określać operacji do wykonania.  
  
## <a name="parentheses"></a>Nawiasy  
 Użyj nawiasów, gdy zdefiniowania procedury, takich jak `Sub` lub `Function`. Wszystkie listy argumentów procedury należy ująć w nawiasy. Możesz także użyć nawiasów za wprowadzanie argumentów lub zmienne w grupy logiczne, szczególnie, aby zastąpić domyślną kolejność pierwszeństwa operatorów w wyrażeniu złożone. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 Następujące wykonywanie poprzedniego kodu, a wartość `d` 8.225 i wartość `e` to 3. Obliczanie dla `d` używa priorytet domyślny `/` za pośrednictwem `+` i jest odpowiednikiem `d = b + (c / a)`. Nawiasy w obliczaniu `e` zastąpić domyślny priorytet.  
  
## <a name="separators"></a>Separatorach  
 Separatory czy sugeruje nazwy: oddzielają sekcje kodu. W języku Visual Basic separatorem jest dwukropek (`:`). Separatory należy użyć uwzględnić wiele instrukcji w jednym wierszu, a nie oddzielnych wierszach. To pozwala zaoszczędzić miejsce i poprawia czytelność kodu. Poniższy przykład pokazuje trzy instrukcje rozdzielone średnikami.  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [jak: Przerywanie i łączenie instrukcji w kodzie](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 Dwukropek (`:`) znak jest również używany do identyfikowania Etykieta instrukcji. Aby uzyskać więcej informacji, zobacz [jak: Etykietowanie instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Połączenie (konkatenacja)  
 Użyj `&` operator *łączenia*, lub ze sobą łączenia ciągów. Nie należy mylić z `+` operatora, który dodaje wartości liczbowych. Jeśli używasz `+` operatora do łączenia podczas działania w przypadku wartości numerycznych, można uzyskać niepoprawnych wyników. Poniższy przykład przedstawia to.  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 Następujące wykonywanie poprzedniego kodu, a wartość `resultA` 21.01 i wartość `resultB` jest "10.0111".  
  
## <a name="member-access-operators"></a>Operatory dostępu do składowych  
 Aby uzyskać dostęp do składowej typu, należy użyć kropki (`.`) lub wykrzyknika (`!`) operator między nazwę typu, a nazwa elementu członkowskiego.  
  
### <a name="dot--operator"></a>Kropka (.) Operator  
 Użyj `.` operator dla klasy, struktury, interfejs lub wyliczenie jako operator dostępu do elementu członkowskiego. Element członkowski może być pola, właściwości, zdarzenia lub metody. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a>Wykrzyknika (!) Operator  
 Użyj `!` operatora tylko na klasę lub interfejs jako operator dostępu do słownika. Klasa lub interfejs musi mieć właściwość domyślną, która akceptuje pojedynczy `String` argumentu. Identyfikator natychmiast po `!` operator staje się wartość argumentu przekazanego do właściwości domyślnej jako ciąg. Poniższy przykład przedstawia to.  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 Trzy wiersze w danych wyjściowych `MsgBox` wyświetlanie wszystkich wartości `32856`. Pierwszy wiersz używa tradycyjny dostęp do właściwości `index`, drugi wykorzystuje fakt, `index` jest domyślną właściwością klasy `hasDefault`, a trzeci używa dostęp do słownika do klasy.  
  
 Należy pamiętać, że drugi argument operacji `!` operator musi być prawidłowym identyfikatorem języka Visual Basic nie jest ujęta w znaki podwójnego cudzysłowu (`" "`). Innymi słowy nie można użyć literału ciągu lub zmiennej ciągu. Następujące zmiany do ostatniego wiersza `MsgBox` wywołanie generuje błąd, ponieważ `"X"` jest ujęty ciąg literału.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  Odwołania do kolekcji domyślne muszą być jawne. W szczególności, nie można użyć `!` operatora zmiennej z późnym wiązaniem.  
  
 `!` Znak jest również używane jako `Single` wpisz znak.  
  
## <a name="see-also"></a>Zobacz także
- [Konwencje dotyczące struktury programów i kodu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Znaki typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
