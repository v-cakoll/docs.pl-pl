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
ms.openlocfilehash: 932b38d97b36292e66bfad91a9a3799459d3b73c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654359"
---
# <a name="special-characters-in-code-visual-basic"></a>Znaki specjalne w Code (Visual Basic)
Czasami trzeba użyć znaków specjalnych w kodzie, oznacza to, znaki, które nie są alfabetycznej lub liczbowe. Interpunkcja i znaki specjalne w zestawie znaków języka Visual Basic mają różnych zastosowań z organizowanie tekst programu do określenia zadań, które wykonuje kompilatora lub skompilowany program. Nie należy określać operacji do wykonania.  
  
## <a name="parentheses"></a>Nawiasów  
 Użyj nawiasów w przypadku zdefiniowania procedury, takich jak `Sub` lub `Function`. Wszystkie listy argumentów procedury należy ująć w nawias. Również Użyj nawiasów wprowadzenia zmienne lub argumenty w grupy logiczne, szczególnie w celu zastąpienia domyślna kolejność pierwszeństwa operatora w wyrażenie złożone. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 Po realizacji poprzedniego kodu, wartość `d` 8.225 i wartość `e` to 3. Obliczanie `d` korzysta z domyślnego pierwszeństwo `/` za pośrednictwem `+` i stanowi odpowiednik `d = b + (c / a)`. Nawiasy w obliczaniu `e` zastąpić domyślny priorytet.  
  
## <a name="separators"></a>Separatorach  
 Separatory czy ich nazwy sugeruje: oddzielają fragmentów kodu. W języku Visual Basic znak separatora jest dwukropkiem (`:`). Użyj separatorów, jeśli chcesz dołączyć wiele instrukcji w jednym wierszu, a nie oddzielnych wierszach. To pozwala zaoszczędzić miejsce i poprawia czytelność kodu. W poniższym przykładzie przedstawiono trzy instrukcje oddzielone dwukropkiem.  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 Aby uzyskać więcej informacji, zobacz [porady: podział i łączenie instrukcji w Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 Dwukropkiem (`:`) znaków również służy do identyfikowania etykiety instrukcji. Aby uzyskać więcej informacji, zobacz [porady: Etykieta instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Połączenie (konkatenacja)  
 Użyj `&` operator *łączenia*, lub łączący ciągów. Nie należy mylić jej z `+` operatora, który dodaje wartości liczbowych. Jeśli używasz `+` operator do połączenia, gdy działają na wartości liczbowe można uzyskać niepoprawnych wyników. W poniższym przykładzie pokazano to.  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 Po realizacji poprzedniego kodu, wartość `resultA` jest 21.01 i wartość `resultB` jest "10.0111".  
  
## <a name="member-access-operators"></a>Operatory dostępu do elementu członkowskiego  
 Aby uzyskać dostęp do elementu członkowskiego typu, należy użyć kropki (.) (`.`) lub wykrzyknika (`!`) operatora pomiędzy nazwą typu i nazwę elementu członkowskiego.  
  
### <a name="dot--operator"></a>Kropkę (.) Operator  
 Użyj `.` operator klasy, struktury, interfejsu lub wyliczenia jako operatora dostępu do elementu członkowskiego. Element członkowski może być pola, właściwości, zdarzenia lub metody. Ilustruje to poniższy przykład.  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a>Wykrzyknika (!) Operator  
 Użyj `!` operator tylko dla klasy ani interfejsu jako operator dostępu do słownika. Klasy lub interfejsu musi mieć właściwość domyślny, który akceptuje pojedynczy `String` argumentu. Identyfikator bezpośrednio po `!` operator staje się wartość argumentu przekazanego do domyślnej właściwości w postaci ciągu. W poniższym przykładzie pokazano to.  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 Output trzy wiersze `MsgBox` wszystkich wyświetlania wartość `32856`. Pierwszy wiersz używa tradycyjny dostęp do właściwości `index`, drugi wykorzystuje fakt, że `index` jest domyślną właściwość klasy `hasDefault`, i trzeci używa słownika dostępu do klasy.  
  
 Należy pamiętać, że drugi operand `!` operatora musi być prawidłowym identyfikatorem języka Visual Basic nie jest ujęta w znaki podwójnego cudzysłowu (`" "`). Innymi słowy nie można użyć literału ciągu lub zmiennej ciągu. Następujące zmiany do ostatniego wiersza `MsgBox` wywołania generuje błąd, ponieważ `"X"` jest literałem ciągu zamknięte.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  Musi być jawnego odwołania do kolekcji domyślnej. W szczególności, nie można użyć `!` operatora zmiennej późnym wiązaniem.  
  
 `!` Znak jest również używany jako `Single` znaku typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura programu i konwencje związane z kodami](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Znaki typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
