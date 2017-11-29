---
title: "Porady: tworzenie procedury, która zwraca wartość (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 787eddc1fd1cdb9dd6b655a8556b75044b2a49dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Porady: tworzenie procedury, która zwraca wartość (Visual Basic)
Możesz użyć `Function` procedury, aby zwrócić wartość do wywołującego kodu.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Aby utworzyć procedury zwracającej wartość  
  
1.  Poza innej procedury należy użyć `Function` instrukcji, a następnie `End Function` instrukcji.  
  
2.  W `Function` instrukcji, wykonaj `Function` — słowo kluczowe o nazwie procedury i listy parametrów w nawiasach.  
  
3.  Postępuj zgodnie z nawiasy `As` klauzuli, aby określić typ danych wartości zwróconej.  
  
4.  Umieść instrukcji kodu procedury między `Function` i `End Function` instrukcje.  
  
5.  Użyj `Return` instrukcji, aby zwrócić wartość do wywołującego kodu.  
  
     Następujące `Function` procedury oblicza najdłuższego boku lub przeciwprostokątnej trójkąta prawo podanych wartości dla obu stron.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     W poniższym przykładzie przedstawiono typowe wywołania `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Sub — procedury](./sub-procedures.md)  
 [Procedury własności](./property-procedures.md)  
 [Procedury operatorów](./operator-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Function — instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Porady: zwracanie wartości z procedury](./how-to-return-a-value-from-a-procedure.md)  
 [Porady: wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
