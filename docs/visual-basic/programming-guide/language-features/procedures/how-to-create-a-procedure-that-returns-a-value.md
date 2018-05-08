---
title: 'Porady: tworzenie procedury, która zwraca wartość (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 472f55173a4897a23a82812a2b24bf1646c1a6ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
 [Sub, procedury](./sub-procedures.md)  
 [Procedury właściwości](./property-procedures.md)  
 [Procedury operatorów](./operator-procedures.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Instrukcje: zwracanie wartości z procedury](./how-to-return-a-value-from-a-procedure.md)  
 [Instrukcje: wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
