---
title: Struktury decyzji
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: d0d4039ff2edc61ee8b4b732c6adcb6e420d73ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353975"
---
# <a name="decision-structures-visual-basic"></a>Struktury decyzji (Visual Basic)
Visual Basic umożliwia testowanie warunków i wykonywanie różnych operacji w zależności od wyników tego testu. Możesz sprawdzić, czy dla warunku określono wartość PRAWDA lub FAŁSZ, dla różnych wartości wyrażenia lub dla różnych wyjątków generowanych podczas wykonywania serii instrukcji.  
  
 Na poniższej ilustracji przedstawiono strukturę decyzyjną, która sprawdza, czy jest spełniony warunek, i wykonuje różne akcje w zależności od tego, czy jest to prawda czy fałsz.  
  
 ![Wykres przepływu dla elementu If...Then...Else.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>If...Then...Else — konstrukcja  
 `If...Then...Else` konstrukcje umożliwiają przetestowanie pod kątem jednego lub kilku warunków i uruchomienie jednej lub kilku instrukcji w zależności od poszczególnych warunków. Można testować warunki i podejmować działania w następujący sposób:  
  
- Uruchom jedną lub więcej instrukcji, jeśli warunek jest `True`  
  
- Uruchom jedną lub więcej instrukcji, jeśli warunek jest `False`  
  
- Uruchom niektóre instrukcje, jeśli warunek jest `True` i innych, jeśli jest `False`  
  
- Przetestuj dodatkowy warunek, jeśli poprzedni warunek jest `False`  
  
 Struktura formantów, która oferuje wszystkie te możliwości, to [Jeśli... Następnie... Else — instrukcja](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Możesz użyć pojedynczej wersji, jeśli masz tylko jeden test i jedną instrukcję do uruchomienia. Jeśli masz bardziej skomplikowany zestaw warunków i akcji, możesz użyć wersji wielowierszowej.  
  
## <a name="selectcase-construction"></a>Select...Case konstrukcja  
 Konstrukcja `Select...Case` pozwala oszacować wyrażenie jeden raz i uruchamiać różne zestawy instrukcji na podstawie różnych możliwych wartości. Aby uzyskać więcej informacji, zobacz [SELECT... Case — instrukcja](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try...Catch...Finally konstrukcja  
 `Try...Catch...Finally` konstrukcje umożliwiają uruchomienie zestawu instrukcji w środowisku, które zachowuje kontrolę, jeśli którykolwiek z instrukcji powoduje wyjątek. Dla różnych wyjątków można wykonać różne działania. Opcjonalnie można określić blok kodu, który jest uruchamiany przed wyjściem z całej konstrukcji `Try...Catch...Finally`, niezależnie od tego, co się dzieje. Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
> W przypadku wielu struktur kontroli po kliknięciu słowa kluczowego, zostaną wyróżnione wszystkie słowa kluczowe w strukturze. Na przykład po kliknięciu `If` w konstrukcji `If...Then...Else` wszystkie wystąpienia `If`, `Then`, `ElseIf`, `Else`i `End If` w konstrukcji są wyróżnione. Aby przejść do następnego lub poprzedniego wyróżnionego słowa kluczowego, naciśnij klawisze CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę.  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Inne struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [Zagnieżdżone struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [If, operator](../../../../visual-basic/language-reference/operators/if-operator.md)
