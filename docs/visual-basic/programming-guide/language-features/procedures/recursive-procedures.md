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
ms.openlocfilehash: de9a2af9fc3cd78879b6525245727a6f52d51c63
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832388"
---
# <a name="recursive-procedures-visual-basic"></a>Procedury rekurencyjne (Visual Basic)
A *cyklicznego* procedura jest taki, który wywołuje sam siebie. Ogólnie rzecz biorąc to nie jest najbardziej skutecznym sposobem pisania kodu języka Visual Basic.  
  
 W poniższej procedurze użyto rekursji, aby obliczyć silnię, oryginalnym argumentu.  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a>Zagadnienia dotyczące z procedury rekurencyjne  
 **Ograniczanie warunki**. Należy projektować procedury cykliczne do testowania dla co najmniej jeden warunek, który może obsłużyć rekursji, a także musi obsłużyć przypadek, gdzie żaden taki warunek jest spełniony w ramach uzasadnioną liczbę wywołań rekurencyjnych. Bez co najmniej jeden warunek, które mogą zostać spełnione bez błędów procedura jest uruchamiana wysokiego ryzyka wykonywania w pętli nieskończonej.  
  
 **Użycie pamięci**. Twoja aplikacja ma ograniczoną ilość miejsca dla zmiennych lokalnych. Każdorazowo procedury wywołuje sam siebie, używa więcej miejsca dla dodatkowych kopii jego zmiennych lokalnych. Jeśli ten proces jest kontynuowany przez czas nieokreślony, ostatecznie powoduje <xref:System.StackOverflowException> błędu.  
  
 **Wydajność**. Prawie zawsze można zastąpić pętli rekursji. Pętli nie ma konieczności przekazywanie argumentów, inicjowanie dodatkowego miejsca do magazynowania i zwracanie wartości. Wydajność może być znacznie lepsze bez wywołania cykliczne.  
  
 **Rekursja wzajemna**. Bardzo niska wydajność lub nawet wejścia w nieskończoną pętlę, może obserwować, jeśli dwie procedury wywołują się wzajemnie. Taki projekt przedstawia informacje o tych samych problemów jako procedura pojedynczego cyklicznego, ale może być trudniejsze wykrycie i zdebugowanie.  
  
 **Wywoływanie za pomocą nawiasów**. Gdy `Function` procedury wywołuje cyklicznie, należy wykonać Nazwa procedury za pomocą nawiasów, nawet jeśli dostępny jest nie listy argumentów. W przeciwnym razie nazwa funkcji jest pobierana jako wartość zwracaną przez funkcję.  
  
 **Testowanie**. Jeśli piszesz procedury cykliczne, należy go przetestować dokładnie aby upewnić się, że spełnia on zawsze jakiegoś warunku ograniczającego. Należy upewnić się, że nie można uruchomić za mało pamięci z powodu konieczności zbyt wiele wywołań rekurencyjnych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.StackOverflowException>
- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury funkcji](./function-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Struktury pętli](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
