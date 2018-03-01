---
title: "Oczekiwano końca instrukcji"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4934952015cb4871bcd90cef982eab5425b1617f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="end-of-statement-expected"></a>Oczekiwano końca instrukcji
Wykonywanie instrukcji zostało składniowo ukończone, ale dodatkowy element programowania zgodny element kończące instrukcję. Terminator wiersza jest wymagany na końcu każdej instrukcji.
  
 Terminator wiersza dzieli znaki plik źródłowy języka Visual Basic wierszy. Przykłady terminatory wiersza są Unicode karetki zwracanych znaków (& HD), Unicode wysuwu wiersza znak (& HA), a znak Unicode wysuwu wiersza znak powrotu karetki Unicode. Aby uzyskać więcej informacji o wierszu terminatory, zobacz [specyfikacja języka Visual Basic](../../../visual-basic/reference/language-specification/index.md).
  
 **Identyfikator błędu:** BC30205
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd
  
1.  Sprawdź, czy dwa różne instrukcje przypadkowo zostały wprowadzone w tym samym wierszu.
  
2.  Wstaw terminator wiersza po elemencie kończące instrukcję.
  
## <a name="see-also"></a>Zobacz też  
 [Porady: przerywanie i łączenie instrukcji w Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
