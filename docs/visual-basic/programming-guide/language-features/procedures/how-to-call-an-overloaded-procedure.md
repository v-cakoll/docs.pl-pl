---
title: 'Porady: wywoływanie procedury przeciążenia'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: d983f5f6183c33141079ed35171f7a73f254450f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340209"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Porady: wywoływanie procedury przeciążenia (Visual Basic)
Zaletą przeładowania procedury jest elastyczność wywołania. Kod wywołujący może uzyskać informacje potrzebne do przekazania do procedury, a następnie wywołać pojedynczą nazwę procedury, niezależnie od tego, jakie argumenty są przekazywane.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Aby wywołać procedurę, która ma zdefiniowaną więcej niż jedną wersję  
  
1. W kodzie wywołującym Określ, które dane mają zostać przekazane do procedury.  
  
2. Napisz wywołanie procedury w zwykły sposób, prezentując dane na liście argumentów. Upewnij się, że argumenty pasują do listy parametrów w jednej z wersji zdefiniowanych dla procedury.  
  
3. Nie ma potrzeby określania, która wersja procedury ma być wywoływana. Visual Basic przekazuje kontrolę do wersji zgodnej z listą argumentów.  
  
     Poniższy przykład wywołuje procedurę `post` zadeklarowaną w [instrukcje: definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md). Uzyskuje identyfikację klienta, określa, czy jest to `String` czy `Integer`, a następnie w obu przypadkach wywołuje tę samą procedurę.  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Instrukcje: przeciążanie procedury korzystającej z nieokreślonej liczby parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
