---
title: Struktury pętli
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: 3f60e9dc83dc7174e765903be13f2870ea40ce4c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403524"
---
# <a name="loop-structures-visual-basic"></a>Struktury pętli (Visual Basic)
Struktury pętli Visual Basic umożliwiają powtarzanie jednego lub kilku wierszy kodu. Można powtarzać instrukcje w strukturze pętli do momentu, aż do `True` osiągnięcia warunku `False` , określonej liczby razy lub jeden raz dla każdego elementu w kolekcji.  
  
 Poniższa ilustracja przedstawia strukturę pętli, która uruchamia zestaw instrukcji do momentu, gdy zostanie spełniony warunek:  
  
 ![Wykres przepływu, który zawiera element do... Do pętli.](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a>While — pętle  
 W `While` konstrukcji... `End While` konstrukcja działa zestaw instrukcji, o ile warunek określony w `While` instrukcji to `True` . Aby uzyskać więcej informacji, zobacz [while... Instrukcja End while](../../../language-reference/statements/while-end-while-statement.md).  
  
## <a name="do-loops"></a>Pętle do  
 `Do`Obiekt... `Loop` konstrukcja umożliwia przetestowanie warunku na początku lub na końcu struktury pętli. Można również określić, czy pętla ma być powtarzana, gdy warunek pozostanie, `True` lub dopóki się nie stanie `True` . Aby uzyskać więcej informacji, zobacz [... Loop — instrukcja](../../../language-reference/statements/do-loop-statement.md).  
  
## <a name="for-loops"></a>Pętle for  
 `For`... `Next` Konstrukcja wykonuje pętlę określoną liczbę razy. Używa zmiennej sterującej pętli, zwanej również *licznikiem*, do śledzenia powtórzeń. Należy określić wartości początkową i końcową dla tego licznika. Opcjonalnie możesz określić ilość, o którą wzrośnie od jednego powtórzenia do następnego. Aby uzyskać więcej informacji, zobacz [dla... Next — instrukcja](../../../language-reference/statements/for-next-statement.md).  
  
## <a name="for-each-loops"></a>Dla każdej pętli  
 W `For Each` konstrukcji... `Next` konstrukcja uruchamia zestaw instrukcji jeden raz dla każdego elementu w kolekcji. Należy określić zmienną sterującą pętli, ale nie trzeba określać jej wartości początkowej ani końcowej. Aby uzyskać więcej informacji, zobacz [dla każdej z nich... Next — instrukcja](../../../language-reference/statements/for-each-next-statement.md).  
  
## <a name="see-also"></a>Zobacz też

- [Przepływ sterowania](index.md)
- [Struktury decyzji](decision-structures.md)
- [Inne struktury sterujące](other-control-structures.md)
- [Zagnieżdżone struktury sterujące](nested-control-structures.md)
