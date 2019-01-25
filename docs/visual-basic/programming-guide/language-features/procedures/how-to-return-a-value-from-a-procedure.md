---
title: 'Instrukcje: Zwracanie wartości z procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 38b0673f5725077eec9253021eec4216e66504a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615260"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Instrukcje: Zwracanie wartości z procedury (Visual Basic)
A `Function` procedury zwraca wartość do wywołującego kodu albo wykonując `Return` instrukcji lub napotkania `Exit Function` lub `End Function` instrukcji.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Zwraca wartość, przy użyciu instrukcji Return  
  
1.  Umieść `Return` instrukcji w punkcie, w której procedury zadanie zostało ukończone.  
  
2.  Postępuj zgodnie z `Return` — słowo kluczowe z wyrażeniem, które zwracają wartości mają być zwracane do kodu wywołującego.  
  
3.  Masz więcej niż jedną `Return` instrukcji w tej samej procedury.  
  
     Następujące `Function` procedury oblicza najdłuższy bok lub przeciwprostokątnej trójkąta prostokątnego i zwraca go do kodu wywołującego.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     W poniższym przykładzie przedstawiono typowe wywołanie `hypotenuse`, która przechowuje zwracanej wartości.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Zwraca wartość, przy użyciu funkcji Exit lub End  
  
1.  W co najmniej jednym miejscu `Function` procedury, przypisz wartość nazwy procedury.  
  
2.  Podczas wykonywania `Exit Function` lub `End Function` instrukcji, Visual Basic zwraca wartość ostatnio przypisana do nazwy procedury.  
  
3.  Masz więcej niż jedną `Exit Function` można łączyć instrukcji w tej samej procedury, a `Return` i `Exit Function` instrukcje w tej samej procedury.  
  
4.  Może mieć tylko jeden `End Function` instrukcji w `Function` procedury.  
  
     Aby uzyskać więcej informacji i obejrzeć przykład, zobacz "Zwraca wartość" w [Function — instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Zobacz także
- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Return, instrukcja](../../../../visual-basic/language-reference/statements/return-statement.md)
- [Instrukcje: Utwórz procedurę, która zwraca wartość](./how-to-create-a-procedure-that-returns-a-value.md)
- [Instrukcje: Wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
