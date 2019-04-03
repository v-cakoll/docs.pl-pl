---
title: Struktury decyzji (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: 20b60fb425278dacb56ee5f888967554a1f76aeb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825381"
---
# <a name="decision-structures-visual-basic"></a>Struktury decyzji (Visual Basic)
Visual Basic umożliwia warunki badania i wykonywać różne operacje, w zależności od wyników tego testu. Możesz sprawdzić warunku jest wartość true lub false dla różnych wartości wyrażenia lub różne wyjątki generowane, gdy wykonać serię instrukcji.  
  
 Poniższa ilustracja przedstawia strukturę decyzji, które sprawdza, czy warunek jest spełniony i wykonują różne akcje zależnie od tego, czy jest wartość PRAWDA lub FAŁSZ.  
  
 ![Schemat blokowy If... Następnie... Konstrukcja ELSE](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "ifthenelse —")  
Wykonywanie różnych akcji, gdy warunek ma wartość PRAWDA, a jeśli ma wartość false  
  
## <a name="ifthenelse-construction"></a>If...Then...Else Construction  
 `If...Then...Else` konstrukcje umożliwiają testowanie dla co najmniej jeden warunek i uruchomić jedną lub więcej instrukcji w zależności od każdego warunku. Można przetestować warunki i akcje w następujący sposób:  
  
-   Uruchomić jedną lub więcej instrukcji, jeśli warunek jest `True`  
  
-   Uruchomić jedną lub więcej instrukcji, jeśli warunek jest `False`  
  
-   Uruchamianie niektórych instrukcji, jeśli warunek jest `True` i innym osobom, gdy jest `False`  
  
-   Dodatkowe warunki badania, w przypadku warunku wstępnego `False`  
  
 Struktura kontrolki, która oferuje wszystkie powyższe możliwości jest [Jeśli... Następnie... Else — instrukcja](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Można użyć wersji jednowierszowego, jeśli masz tylko jeden test i jednej instrukcji do uruchomienia. W przypadku bardziej złożonego zestawu warunków i akcji można użyć wersji wielu linii.  
  
## <a name="selectcase-construction"></a>Wybierz... Konstrukcja wielkości liter  
 `Select...Case` Konstrukcja umożliwia ocena wyrażenia jeden raz i uruchomić różne zestawy instrukcji, w oparciu o różne możliwe wartości. Aby uzyskać więcej informacji, zobacz [wybierz... Case — instrukcja](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try... CATCH... Na koniec konstrukcji  
 `Try...Catch...Finally` konstrukcje umożliwiają uruchamianie zbiór instrukcji w środowisku, w którym zachowuje kontrolki, jeśli dowolny z zestawienia powoduje wyjątek. Możesz wykonywać różne akcje dla różnych wyjątków. Opcjonalnie można określić bloku kodu, który jest uruchamiany przed zakończeniem pracy całego `Try...Catch...Finally` konstrukcji, niezależnie od tego, co występuje. Aby uzyskać więcej informacji, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Dla wielu struktur sterowania po kliknięciu słowem kluczowym wszystkich słów kluczowych w strukturze, zostały wyróżnione. Na przykład po kliknięciu `If` w `If...Then...Else` budowy, wszystkie wystąpienia elementu `If`, `Then`, `ElseIf`, `Else`, i `End If` w konstrukcji są wyróżnione. Aby przejść do następnego lub poprzedniego wyróżnionego słów kluczowych, naciśnij klawisz Strzałka CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę Strzałka.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Inne struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [Zagnieżdżone struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [If, operator](../../../../visual-basic/language-reference/operators/if-operator.md)
