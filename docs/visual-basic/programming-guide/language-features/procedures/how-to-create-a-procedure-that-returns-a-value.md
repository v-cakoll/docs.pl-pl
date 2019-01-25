---
title: 'Instrukcje: Utwórz procedurę, która zwraca wartość (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 18becfe05da27e538c5c294b26e0bb7aa19cad2b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506423"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Instrukcje: Utwórz procedurę, która zwraca wartość (Visual Basic)
Możesz użyć `Function` procedury w celu zwrócenia wartości do wywołującego kodu.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Aby utworzyć procedurę, która nie zwraca wartości  
  
1.  Poza innej procedury, należy użyć `Function` instrukcji, następuje `End Function` instrukcji.  
  
2.  W `Function` instrukcji, postępuj zgodnie z `Function` — słowo kluczowe o nazwie procedury oraz lista parametrów w nawiasach.  
  
3.  Postępuj zgodnie z nawiasów za pomocą `As` klauzuli, aby określić typ danych zwróconej wartości.  
  
4.  Umieść instrukcje kod procedury między `Function` i `End Function` instrukcji.  
  
5.  Użyj `Return` instrukcji, aby zwrócić wartości do wywołującego kodu.  
  
     Następujące `Function` procedury oblicza najdłuższy bok lub przeciwprostokątnej trójkąta prostokątnego, biorąc pod uwagę wartości dla obu stron.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     W poniższym przykładzie przedstawiono typowe wywołanie `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrukcje: Zwracanie wartości z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Instrukcje: Wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
