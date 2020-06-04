---
title: 'Porady: zwracanie wartości z procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 917e52b711645fbf94a132216a3fa90b0dfc15b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414327"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Porady: zwracanie wartości z procedury (Visual Basic)
`Function`Procedura zwraca wartość do wywołującego kodu przez wykonanie `Return` instrukcji lub przez napotkanie `Exit Function` `End Function` instrukcji or.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Aby zwrócić wartość przy użyciu instrukcji return  
  
1. Umieść `Return` instrukcję w punkcie, w którym wykonano zadanie procedury.  
  
2. Użyj `Return` słowa kluczowego z wyrażeniem, które zwraca wartość, która ma zostać zwrócona do kodu wywołującego.  
  
3. W tej samej procedurze można mieć więcej niż jedną `Return` instrukcję.  
  
     Poniższa `Function` procedura oblicza dłuższy Trójkąt lub przeciwprostokątnej, z prawej strony i zwraca go do kodu wywołującego.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     Poniższy przykład przedstawia typowe wywołanie do `hypotenuse` , które przechowuje zwracaną wartość.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Aby zwrócić wartość przy użyciu funkcji Exit lub End Function  
  
1. W co najmniej jednym miejscu w `Function` procedurze Przypisz wartość do nazwy procedury.  
  
2. Podczas wykonywania `Exit Function` `End Function` instrukcji lub Visual Basic zwraca wartość ostatnio przypisaną do nazwy procedury.  
  
3. Można mieć więcej niż jedną `Exit Function` instrukcję w tej samej procedurze i można mieszać `Return` i `Exit Function` wypełniać instrukcje w tej samej procedurze.  
  
4. W procedurze można mieć tylko jedną `End Function` instrukcję `Function` .  
  
     Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz "wartość zwracana" w [instrukcji funkcji](../../../language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury własności](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Function, instrukcja](../../../language-reference/statements/function-statement.md)
- [Return — Instrukcja](../../../language-reference/statements/return-statement.md)
- [Instrukcje: tworzenie procedury, która zwraca wartość](./how-to-create-a-procedure-that-returns-a-value.md)
- [Instrukcje: wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
