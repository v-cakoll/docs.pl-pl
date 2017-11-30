---
title: "Porady: zwracanie wartości z procedury (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ce7aa0942be413986cb010963753447ea18cdf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Porady: zwracanie wartości z procedury (Visual Basic)
A `Function` procedury zwraca wartość do wywołującego kodu albo wykonując `Return` instrukcji lub napotkania `Exit Function` lub `End Function` instrukcji.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Aby zwrócić wartość przy użyciu instrukcji Return  
  
1.  Umieść `Return` instrukcji w momencie, gdy procedury zadanie zostało ukończone.  
  
2.  Wykonaj `Return` — słowo kluczowe z dowolne wyrażenie zwracające wartość ma być zwrócona do wywołującego kodu.  
  
3.  Może mieć więcej niż jeden `Return` instrukcji w tej samej procedury.  
  
     Następujące `Function` procedury oblicza najdłuższego boku lub przeciwprostokątnej trójkąta prostokątnego i zwraca go do wywołującego kodu.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     W poniższym przykładzie przedstawiono typowe wywołania `hypotenuse`, która przechowuje zwracanej wartości.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Aby zwrócić wartość przy użyciu funkcji zakończenia lub End  
  
1.  W co najmniej jednym miejscu `Function` procedury, przypisz wartość na nazwę procedury.  
  
2.  Podczas wykonywania `Exit Function` lub `End Function` instrukcji [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zwraca wartość ostatnio przypisana do Nazwa procedury.  
  
3.  Może mieć więcej niż jeden `Exit Function` można łączyć instrukcji w tej samej procedury, a `Return` i `Exit Function` instrukcje w tej samej procedury.  
  
4.  Może mieć tylko jeden `End Function` instrukcji w `Function` procedury.  
  
     Na przykład i więcej informacji, zobacz "Zwraca wartość" w [instrukcji Function](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Sub — procedury](./sub-procedures.md)  
 [Procedury własności](./property-procedures.md)  
 [Procedury operatorów](./operator-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Function — instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Return — instrukcja](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [Porady: Tworzenie procedury, która zwraca wartość](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Porady: wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
