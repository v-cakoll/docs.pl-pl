---
title: Inne struktury sterujące
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c6d80b237c7c3512c2904547842fdeb3c69bef68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402021"
---
# <a name="other-control-structures-visual-basic"></a>Inne struktury sterujące (Visual Basic)
Visual Basic zawiera struktury kontroli, które ułatwiają usuwanie zasobu lub zmniejszają liczbę przypadków powtarzania odwołania do obiektu.  
  
## <a name="usingend-using-construction"></a>Korzystanie z... Zakończ korzystanie z konstrukcji  
 `Using...End Using`Konstrukcja ustanawia blok instrukcji, w ramach którego używany jest zasób, taki jak połączenie SQL. Opcjonalnie możesz uzyskać zasób za pomocą `Using` instrukcji. Po zamknięciu `Using` bloku Visual Basic automatycznie usunąć zasób, aby był dostępny do użycia przez inny kod. Zasób musi być lokalny i jednorazowy. Aby uzyskać więcej informacji, zobacz [using instrukcji](../../../language-reference/statements/using-statement.md).  
  
## <a name="withend-with-construction"></a>Z... Zakończ z konstrukcją  
 `With...End With`Konstrukcja pozwala określić odwołanie do obiektu jeden raz, a następnie uruchomić serię instrukcji, które uzyskują dostęp do swoich elementów członkowskich. Może to uprościć kod i zwiększyć wydajność, ponieważ Visual Basic nie musi ponownie ustanowić odwołania dla każdej instrukcji, która uzyskuje do niej dostęp. Aby uzyskać więcej informacji, zobacz temat [with... End With — instrukcja](../../../language-reference/statements/with-end-with-statement.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ sterowania](index.md)
- [Struktury decyzji](decision-structures.md)
- [Struktury pętli](loop-structures.md)
- [Zagnieżdżone struktury sterujące](nested-control-structures.md)
- [Using, instrukcja](../../../language-reference/statements/using-statement.md)
- [With...End With, instrukcja](../../../language-reference/statements/with-end-with-statement.md)
