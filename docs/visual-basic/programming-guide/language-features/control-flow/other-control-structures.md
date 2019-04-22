---
title: Inne struktury sterujące (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c42070ce2ea866e59e1b2e190f7c05e1ee7cc922
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819323"
---
# <a name="other-control-structures-visual-basic"></a>Inne struktury sterujące (Visual Basic)
Visual Basic zapewnia struktury sterujące, które ułatwiają Usuwanie zasobu lub Zmniejsz liczbę razy, należy powtórzyć odwołanie do obiektu.  
  
## <a name="usingend-using-construction"></a>Za pomocą... Za pomocą konstrukcji końcowych  
 `Using...End Using` Konstrukcji ustanawia blok instrukcji, w którym możesz wprowadzić korzystanie z zasobów, takich jak połączenia SQL. Opcjonalnie można pobrać zasobu o `Using` instrukcji. Po zakończeniu `Using` bloku, Visual Basic automatycznie usuwa zasobu tak, że jest dostępny dla innego kodu do użycia. Zasób musi być lokalny i możliwe do likwidacji. Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="withend-with-construction"></a>Za pomocą... Kończy się konstrukcji  
 `With...End With` Konstrukcji pozwala określić odwołanie do obiektu tylko raz, a następnie uruchom serię instrukcji uzyskujących dostęp do jego członków. Może to uprościć kod i zwiększyć wydajność, ponieważ Visual Basic nie trzeba ponownie ustanowić odwołanie dla każdej instrukcji, która uzyskuje do niej dostęp. Aby uzyskać więcej informacji, zobacz [za pomocą... End With — instrukcja](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przepływ sterowania](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Struktury decyzji](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Zagnieżdżone struktury sterujące](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Using, instrukcja](../../../../visual-basic/language-reference/statements/using-statement.md)
- [With...End With, instrukcja](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
