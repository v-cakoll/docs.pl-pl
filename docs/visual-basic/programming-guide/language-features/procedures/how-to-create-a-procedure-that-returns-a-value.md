---
title: 'Porady: tworzenie procedury, która zwraca wartość'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 218dbb52abc0100724d38d10be91ef24252d5226
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349723"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Porady: tworzenie procedury, która zwraca wartość (Visual Basic)
Użyj procedury `Function`, aby zwrócić wartość do kodu wywołującego.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Aby utworzyć procedurę zwracającą wartość  
  
1. Poza każdą inną procedurę Użyj instrukcji `Function`, a po niej instrukcji `End Function`.  
  
2. W instrukcji `Function` postępuj według słowa kluczowego `Function` z nazwą procedury, a następnie listę parametrów w nawiasach.  
  
3. Użyj nawiasów z klauzulą `As`, aby określić typ danych zwracanej wartości.  
  
4. Umieść instrukcje kodu procedury między instrukcjami `Function` i `End Function`.  
  
5. Użyj instrukcji `Return`, aby zwrócić wartość do kodu wywołującego.  
  
     Poniższa procedura `Function` oblicza najdłuższy bok lub przeciwprostokątnej w prawym trójkątze, uwzględniając wartości pozostałych dwóch stron.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     Poniższy przykład przedstawia typowe wywołanie do `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Procedury właściwości](./property-procedures.md)
- [Procedury operatorów](./operator-procedures.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Function, instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrukcje: zwracanie wartości z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Instrukcje: wywoływanie procedury zwracającej wartość](./how-to-call-a-procedure-that-returns-a-value.md)
