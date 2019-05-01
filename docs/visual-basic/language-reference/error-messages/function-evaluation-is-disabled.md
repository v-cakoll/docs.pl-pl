---
title: Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie przekroczyło limit czasu
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: bc4d05e52434cf62fa90671d29b407c83114b5d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801949"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie przekroczyło limit czasu
Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie funkcji przekroczyło limit czasu. Aby ponownie włączyć funkcję oceny, krok ponownie, lub uruchom ponownie debugowanie.  
  
 W debugerze programu Visual Studio wyrażenie określa wywołania procedury, ale upłynął limit czasu oceny innego.  
  
 Możliwe przyczyny na przekroczenie limitu czasu wywołanie procedury to wejścia w nieskończoną pętlę lub *nieskończoną pętlę*. Aby uzyskać więcej informacji, zobacz [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
 Jest przypadkiem szczególnym wejścia w nieskończoną pętlę *rekursji*. Aby uzyskać więcej informacji, zobacz [procedury rekurencyjne](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **Identyfikator błędu:** BC30957  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Jeśli to możliwe Określ poprzednie szacowanie funkcji zostało i co spowodowało przekroczenie limitu czasu. W przeciwnym razie ten błąd może wystąpić ponownie.  
  
2. Krok debuger ponownie, lub przerwać i uruchom ponownie debugowanie.  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)
- [Nawigowanie po kodzie za pomocą debugera](/visualstudio/debugger/navigating-through-code-with-the-debugger)
