---
title: Procedury rekurencyjne
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
ms.openlocfilehash: 646d4e29ed7a0b6367d4b35a7f8641bcf659e616
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352555"
---
# <a name="recursive-procedures-visual-basic"></a>Procedury rekurencyjne (Visual Basic)

Procedura *cykliczna* to taka, która wywołuje sam siebie. Ogólnie rzecz biorąc, nie jest to najbardziej skuteczny sposób pisania kodu Visual Basic.  
  
 Poniższa procedura używa rekursji do obliczenia silni pierwotnego argumentu.  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a>Zagadnienia dotyczące procedur cyklicznych

 **Warunki ograniczające**. Należy zaprojektować procedurę cykliczną w celu przetestowania dla co najmniej jednego warunku, który może zakończyć rekursję, a także obsłużyć przypadek, w którym taki warunek nie jest spełniony w ramach rozsądnej liczby wywołań cyklicznych. Bez co najmniej jednego warunku, który może zostać spełniony bez niepowodzenia, procedura wykonuje wysokie ryzyko wykonania w pętli nieskończonej.

 **Użycie pamięci**. Twoja aplikacja ma ograniczoną ilość miejsca dla zmiennych lokalnych. Za każdym razem, gdy procedura wywołuje samą siebie, używa większej ilości miejsca, aby uzyskać dodatkowe kopie swoich zmiennych lokalnych. Jeśli ten proces będzie kontynuowany w nieskończoność, spowoduje to, że wystąpił błąd <xref:System.StackOverflowException>.

 **Wydajność**. Prawie zawsze można zastąpić pętlę do rekursji. Pętla nie ma nakładu na przekazywanie argumentów, inicjowanie dodatkowego magazynu i zwracanie wartości. Wydajność może być znacznie lepsza bez wywołań cyklicznych.

 **Wzajemna rekursja**. Można zaobserwować bardzo niską wydajność lub nawet nieskończoną pętlę, jeśli dwie procedury wywołują siebie nawzajem. Taki projekt przedstawia te same problemy co pojedyncza procedura cykliczna, ale może być trudniejszy do wykrycia i debugowania.

 **Wywoływanie za pomocą nawiasów**. Gdy procedura `Function` wywołuje się w sposób cykliczny, należy postępować zgodnie z nazwą procedury z nawiasami, nawet jeśli nie ma listy argumentów. W przeciwnym razie nazwa funkcji jest traktowana jak reprezentująca wartość zwracaną funkcji.

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
