---
title: 'Instrukcje: Utwórz procedurę, która zwraca wartość (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 115c1df4bd49d5848d72c4cbd0242a49a12740c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335501"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Instrukcje: Utwórz procedurę, która zwraca wartość (Visual Basic)
Możesz użyć `Function` procedury w celu zwrócenia wartości do wywołującego kodu.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Aby utworzyć procedurę, która nie zwraca wartości  
  
1. Poza innej procedury, należy użyć `Function` instrukcji, następuje `End Function` instrukcji.  
  
2. W `Function` instrukcji, postępuj zgodnie z `Function` — słowo kluczowe o nazwie procedury oraz lista parametrów w nawiasach.  
  
3. Postępuj zgodnie z nawiasów za pomocą `As` klauzuli, aby określić typ danych zwróconej wartości.  
  
4. Umieść instrukcje kod procedury między `Function` i `End Function` instrukcji.  
  
5. Użyj `Return` instrukcji, aby zwrócić wartości do wywołującego kodu.  
  
     Następujące `Function` procedury oblicza najdłuższy bok lub przeciwprostokątnej trójkąta prostokątnego, biorąc pod uwagę wartości dla obu stron.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     W poniższym przykładzie przedstawiono typowe wywołanie `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrukcje: Zwracanie wartości z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Instrukcje: Wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
