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
ms.openlocfilehash: aac9844240defc5a21a3f4e6090fa8f49e6348a1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403523"
---
# <a name="decision-structures-visual-basic"></a>Struktury decyzji (Visual Basic)
Visual Basic umożliwia testowanie warunków i wykonywanie różnych operacji w zależności od wyników tego testu. Możesz sprawdzić, czy dla warunku określono wartość PRAWDA lub FAŁSZ, dla różnych wartości wyrażenia lub dla różnych wyjątków generowanych podczas wykonywania serii instrukcji.  
  
 Na poniższej ilustracji przedstawiono strukturę decyzyjną, która sprawdza, czy jest spełniony warunek, i wykonuje różne akcje w zależności od tego, czy jest to prawda czy fałsz.  
  
 ![Wykres przepływu dla elementu IF... Następnie... Else.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>If... Następnie... Else — konstrukcja  
 `If...Then...Else`Konstrukcje umożliwiają przetestowanie pod kątem jednego lub kilku warunków i uruchomienie jednej lub kilku instrukcji w zależności od poszczególnych warunków. Można testować warunki i podejmować działania w następujący sposób:  
  
- Uruchom jedną lub więcej instrukcji, jeśli warunek jest`True`  
  
- Uruchom jedną lub więcej instrukcji, jeśli warunek jest`False`  
  
- Uruchom niektóre instrukcje, jeśli warunek jest `True` i inne, jeśli jest`False`  
  
- Przetestuj dodatkowy warunek, jeśli poprzedni warunek jest`False`  
  
 Struktura formantów, która oferuje wszystkie te możliwości, to [Jeśli... Następnie... Else — instrukcja](../../../language-reference/statements/if-then-else-statement.md). Możesz użyć pojedynczej wersji, jeśli masz tylko jeden test i jedną instrukcję do uruchomienia. Jeśli masz bardziej skomplikowany zestaw warunków i akcji, możesz użyć wersji wielowierszowej.  
  
## <a name="selectcase-construction"></a>Wybierz... Konstrukcja przypadku  
 `Select...Case`Konstrukcja pozwala oszacować wyrażenie jeden raz i uruchamiać różne zestawy instrukcji na podstawie różnych możliwych wartości. Aby uzyskać więcej informacji, zobacz [SELECT... Case — instrukcja](../../../language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Spróbuj... Catch... Na końcu konstrukcja  
 `Try...Catch...Finally`Konstrukcje umożliwiają uruchomienie zestawu instrukcji w środowisku, które zachowuje kontrolę, jeśli którykolwiek z instrukcji powoduje wyjątek. Dla różnych wyjątków można wykonać różne działania. Opcjonalnie można określić blok kodu, który jest uruchamiany przed wyjściem z całego `Try...Catch...Finally` konstruowania, niezależnie od tego, co się dzieje. Aby uzyskać więcej informacji, zobacz [try... Catch... Finally — instrukcja](../../../language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
> W przypadku wielu struktur kontroli po kliknięciu słowa kluczowego, zostaną wyróżnione wszystkie słowa kluczowe w strukturze. Na przykład po kliknięciu `If` w `If...Then...Else` konstrukcji wszystkie wystąpienia elementów,,, `If` `Then` `ElseIf` `Else` i `End If` w konstrukcji są wyróżnione. Aby przejść do następnego lub poprzedniego wyróżnionego słowa kluczowego, naciśnij klawisze CTRL + SHIFT + Strzałka w dół lub CTRL + SHIFT + Strzałka w górę.  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ sterowania](index.md)
- [Struktury pętli](loop-structures.md)
- [Inne struktury sterujące](other-control-structures.md)
- [Zagnieżdżone struktury sterujące](nested-control-structures.md)
- [If, operator](../../../language-reference/operators/if-operator.md)
