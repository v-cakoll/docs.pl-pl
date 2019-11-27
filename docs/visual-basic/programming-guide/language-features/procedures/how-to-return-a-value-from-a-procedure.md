---
title: 'Porady: zwracanie wartości z procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 1371e4ed0ff28f9caf56eabf2a1bb9290edbe75c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346026"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Porady: zwracanie wartości z procedury (Visual Basic)
Procedura `Function` zwraca wartość do wywołującego kodu przez wykonanie instrukcji `Return` lub napotkanie instrukcji `Exit Function` lub `End Function`.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Aby zwrócić wartość przy użyciu instrukcji return  
  
1. Umieść instrukcję `Return` w punkcie, w którym wykonano zadanie procedury.  
  
2. Obserwuj `Return` słowo kluczowe z wyrażeniem, które zwraca wartość, która ma zostać zwrócona do kodu wywołującego.  
  
3. W tej samej procedurze można mieć więcej niż jedną instrukcję `Return`.  
  
     Poniższa procedura `Function` oblicza najdłuższy Trójkąt lub przeciwprostokątnej, z prawej strony, i zwraca go do kodu wywołującego.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     W poniższym przykładzie przedstawiono typowe wywołanie `hypotenuse`, w którym jest przechowywana zwrócona wartość.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Aby zwrócić wartość przy użyciu funkcji Exit lub End Function  
  
1. W co najmniej jednym miejscu procedury `Function` Przypisz wartość do nazwy procedury.  
  
2. Podczas wykonywania instrukcji `Exit Function` lub `End Function`, Visual Basic zwraca wartość ostatnio przypisaną do nazwy procedury.  
  
3. W tej samej procedurze można mieć więcej niż jedną instrukcję `Exit Function` i można mieszać instrukcje `Return` i `Exit Function` w tej samej procedurze.  
  
4. W procedurze `Function` można mieć tylko jedną instrukcję `End Function`.  
  
     Aby uzyskać więcej informacji i zapoznać się z przykładem, zobacz "wartość zwracana" w [instrukcji funkcji](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Return, instrukcja](../../../../visual-basic/language-reference/statements/return-statement.md)
- [Instrukcje: tworzenie procedury, która zwraca wartość](./how-to-create-a-procedure-that-returns-a-value.md)
- [Instrukcje: wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
