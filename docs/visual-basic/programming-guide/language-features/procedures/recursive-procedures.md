---
title: Procedury rekurencyjne (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: b08a06a07f134b7c95251848862d39339e59fe61
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274344"
---
# <a name="recursive-procedures-visual-basic"></a>Procedury rekurencyjne (Visual Basic)

Procedura *cykliczna* to taka, która wywołuje sam siebie. Ogólnie rzecz biorąc, nie jest to najbardziej skuteczny sposób pisania kodu Visual Basic.  
  
 Poniższa procedura używa rekursji do obliczenia silni pierwotnego argumentu.  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a>Zagadnienia dotyczące procedur cyklicznych

 **Warunki ograniczające**. Należy zaprojektować procedurę cykliczną w celu przetestowania dla co najmniej jednego warunku, który może zakończyć rekursję, a także obsłużyć przypadek, w którym taki warunek nie jest spełniony w ramach rozsądnej liczby wywołań cyklicznych. Bez co najmniej jednego warunku, który może zostać spełniony bez niepowodzenia, procedura wykonuje wysokie ryzyko wykonania w pętli nieskończonej.

 **Użycie pamięci**. Twoja aplikacja ma ograniczoną ilość miejsca dla zmiennych lokalnych. Za każdym razem, gdy procedura wywołuje samą siebie, używa większej ilości miejsca, aby uzyskać dodatkowe kopie swoich zmiennych lokalnych. W przypadku kontynuowania <xref:System.StackOverflowException> tego procesu wystąpi błąd.

 **Wydajność**. Prawie zawsze można zastąpić pętlę do rekursji. Pętla nie ma nakładu na przekazywanie argumentów, inicjowanie dodatkowego magazynu i zwracanie wartości. Wydajność może być znacznie lepsza bez wywołań cyklicznych.

 **Wzajemna rekursja**. Można zaobserwować bardzo niską wydajność lub nawet nieskończoną pętlę, jeśli dwie procedury wywołują siebie nawzajem. Taki projekt przedstawia te same problemy co pojedyncza procedura cykliczna, ale może być trudniejszy do wykrycia i debugowania.

 **Wywoływanie za pomocą nawiasów**. `Function` Gdy procedura wywołuje samo cyklicznie, należy postępować zgodnie z nazwą procedury z nawiasami, nawet jeśli nie ma listy argumentów. W przeciwnym razie nazwa funkcji jest traktowana jak reprezentująca wartość zwracaną funkcji.

 **Testowanie**. Jeśli napiszesz procedurę cykliczną, należy dokładnie ją przetestować, aby upewnić się, że zawsze spełnia pewne warunki ograniczające. Należy również upewnić się, że nie można zalogować się za mało pamięci z powodu zbyt wielu wywołań cyklicznych.

## <a name="see-also"></a>Zobacz także

- <xref:System.StackOverflowException>
- [Procedury](index.md)
- [Sub, procedury](sub-procedures.md)
- [Procedury funkcji](function-procedures.md)
- [Procedury właściwości](property-procedures.md)
- [Procedury operatorów](operator-procedures.md)
- [Parametry i argumenty procedur](procedure-parameters-and-arguments.md)
- [Przeciążanie procedury](procedure-overloading.md)
- [Rozwiązywanie problemów z procedurami](troubleshooting-procedures.md)
- [Struktury pętli](../control-flow/loop-structures.md)
