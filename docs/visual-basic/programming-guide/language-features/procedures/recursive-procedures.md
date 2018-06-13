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
ms.openlocfilehash: 8ea7741c943ea563fbd0c7649ac0ff85b2f9ebba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650218"
---
# <a name="recursive-procedures-visual-basic"></a>Procedury rekurencyjne (Visual Basic)
A *cykliczne* procedura jest taki, który wywołuje sam siebie. Ogólnie rzecz biorąc to nie jest najbardziej efektywny sposób pisania kodu języka Visual Basic.  
  
 W poniższej procedurze użyto rekursji do obliczania silni oryginalnego argumentu.  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a>Zagadnienia dotyczące z procedury cykliczne  
 **Warunki ograniczające**. Należy projektować procedury cykliczne do testowania dla co najmniej jeden warunek, który może obsłużyć rekursji i również musi obsługiwać case, gdzie nie taki warunek jest spełniony w rozsądnym liczbę wywołań cyklicznych. Bez co najmniej jeden warunek, który może zostać spełniony bez błędów procedura jest uruchamiana wysokiego ryzyka wykonywanych w pętli nieskończonej.  
  
 **Użycie pamięci**. Aplikacja ma ograniczoną ilość miejsca dla zmiennych lokalnych. Zawsze wywołania procedur, używa więcej miejsca dla dodatkowych kopii jego zmiennych lokalnych. Jeśli ten proces jest kontynuowany przez nieokreślony czas, po pewnym czasie powoduje <xref:System.StackOverflowException> błędu.  
  
 **Wydajność**. Prawie zawsze można zastąpić pętli rekursji. Pętla nie ma obciążenie przekazywanie argumentów, inicjowanie dodatkowego miejsca do magazynowania i zwracanie wartości. Wydajność może być znacznie poprawia bez wywołania cykliczne.  
  
 **Rekursja wzajemna**. Widoczny bardzo niską wydajnością, lub nawet nieskończoną pętlę, jeśli dwie procedury wywołać siebie nawzajem. Taki projekt przedstawia informacje o tej samej problemów jako procedura pojedynczego cykliczne, ale może być trudniejsza do wykrywania i debugowania.  
  
 **Wywoływanie z nawiasów**. Gdy `Function` procedury wywołuje cyklicznie, należy wykonać nazwę procedury w nawiasach, nawet jeśli nie są znane argumentu. W przeciwnym razie nazwa funkcji jest pobierana jako zwracana wartość funkcji.  
  
 **Testowanie**. Procedury cykliczne podczas pisania, należy przetestować go dokładnie aby upewnić się, że spełnia on zawsze spełnienia określonego warunku ograniczającego. Ponadto upewnij się, że nie można uruchomić za mało pamięci z powodu konieczności zbyt wiele wywołań cyklicznych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.StackOverflowException>  
 [Procedury](./index.md)  
 [Sub, procedury](./sub-procedures.md)  
 [Procedury funkcji](./function-procedures.md)  
 [Procedury właściwości](./property-procedures.md)  
 [Procedury operatorów](./operator-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)  
 [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Rozwiązywanie problemów z wyjątkami: System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
