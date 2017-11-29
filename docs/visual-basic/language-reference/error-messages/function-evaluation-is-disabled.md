---
title: "Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie przekroczyło limit czasu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords: BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05067e730486b443b7a508adb499f34c060d5093
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie przekroczyło limit czasu
Szacowanie funkcji zostało wyłączone, ponieważ poprzednie szacowanie funkcji przekroczyło limit czasu. Aby ponownie włączyć Szacowanie funkcji, ponownie wykonaj krok lub uruchom ponownie debugowanie.  
  
 W debugerze programu Visual Studio wyrażenie określa wywołanie procedury, ale innej obliczania został przekroczony.  
  
 Możliwe przyczyny wywołania procedury limit czasu to nieskończoną pętlę lub *nieskończonej pętli*. Aby uzyskać więcej informacji, zobacz [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
 Specjalny przypadek nieskończoną pętlę jest *rekursji*. Aby uzyskać więcej informacji, zobacz [procedury rekurencyjne](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **Identyfikator błędu:** BC30957  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Jeśli to możliwe można określić, poprzednie Obliczanie funkcji zostało i przyczyn limitu czasu. W przeciwnym razie ten błąd może wystąpić ponownie.  
  
2.  Krok debuger ponownie, lub przerwanie i uruchom ponownie debugowanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
 [Nawigowanie po kodzie za pomocą debugera](/visualstudio/debugger/navigating-through-code-with-the-debugger)
