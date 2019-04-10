---
title: 'Instrukcje: Zwracanie wartości z procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 8b53df1634d2b9971bc44c968a17db81cac3924f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307889"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Instrukcje: Zwracanie wartości z procedury (Visual Basic)
A `Function` procedury zwraca wartość do wywołującego kodu albo wykonując `Return` instrukcji lub napotkania `Exit Function` lub `End Function` instrukcji.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Zwraca wartość, przy użyciu instrukcji Return  
  
1. Umieść `Return` instrukcji w punkcie, w której procedury zadanie zostało ukończone.  
  
2. Postępuj zgodnie z `Return` — słowo kluczowe z wyrażeniem, które zwracają wartości mają być zwracane do kodu wywołującego.  
  
3. Masz więcej niż jedną `Return` instrukcji w tej samej procedury.  
  
     Następujące `Function` procedury oblicza najdłuższy bok lub przeciwprostokątnej trójkąta prostokątnego i zwraca go do kodu wywołującego.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     W poniższym przykładzie przedstawiono typowe wywołanie `hypotenuse`, która przechowuje zwracanej wartości.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Zwraca wartość, przy użyciu funkcji Exit lub End  
  
1. W co najmniej jednym miejscu `Function` procedury, przypisz wartość nazwy procedury.  
  
2. Podczas wykonywania `Exit Function` lub `End Function` instrukcji, Visual Basic zwraca wartość ostatnio przypisana do nazwy procedury.  
  
3. Masz więcej niż jedną `Exit Function` można łączyć instrukcji w tej samej procedury, a `Return` i `Exit Function` instrukcje w tej samej procedury.  
  
4. Może mieć tylko jeden `End Function` instrukcji w `Function` procedury.  
  
     Aby uzyskać więcej informacji i obejrzeć przykład, zobacz "Zwraca wartość" w [Function — instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Function — Instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Return — Instrukcja](../../../../visual-basic/language-reference/statements/return-statement.md)
- [Instrukcje: Tworzenie procedury, która zwraca wartość](./how-to-create-a-procedure-that-returns-a-value.md)
- [Instrukcje: Wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
