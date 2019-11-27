---
title: Inne struktury sterujące
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 758df361f421684655147ae288af3f350e53c4d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348132"
---
# <a name="other-control-structures-visual-basic"></a>Inne struktury sterujące (Visual Basic)
Visual Basic zawiera struktury kontroli, które ułatwiają usuwanie zasobu lub zmniejszają liczbę przypadków powtarzania odwołania do obiektu.  
  
## <a name="usingend-using-construction"></a>Korzystanie z... Zakończ korzystanie z konstrukcji  
 Konstrukcja `Using...End Using` ustanawia blok instrukcji, w ramach którego używany jest zasób, taki jak połączenie SQL. Opcjonalnie możesz uzyskać zasób z instrukcją `Using`. Po zamknięciu bloku `Using` Visual Basic automatycznie usunąć zasób, aby był dostępny do użycia w innym kodzie. Zasób musi być lokalny i jednorazowy. Aby uzyskać więcej informacji, zobacz [using instrukcji](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="withend-with-construction"></a>Z... Zakończ z konstrukcją  
 Konstrukcja `With...End With` pozwala określić odwołanie do obiektu jeden raz, a następnie uruchomić serię instrukcji, które uzyskują dostęp do swoich elementów członkowskich. Może to uprościć kod i zwiększyć wydajność, ponieważ Visual Basic nie musi ponownie ustanowić odwołania dla każdej instrukcji, która uzyskuje do niej dostęp. Aby uzyskać więcej informacji, zobacz temat [with... End With — instrukcja](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury decyzji](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Zagnieżdżone struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using, instrukcja](../../../../visual-basic/language-reference/statements/using-statement.md)
- [With...End With, instrukcja](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
