---
title: 'Instrukcje: Wywoływanie procedury przeciążenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 8320bc550c818fd2bea53f75107709eab8456096
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706420"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Instrukcje: Wywoływanie procedury przeciążenia (Visual Basic)
Zaletą przeciążanie procedury trwa elastyczność wywołania. Kod wywołujący można uzyskać informacji potrzebnych do przekazania do procedury, a następnie wywołać nazwę samą procedurą, niezależnie od tego, jakie argumentów, go przechodzi.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Aby wywołać procedurę, który ma więcej niż jedna wersja zdefiniowane  
  
1.  W wywoływanym kodzie określają, jakie dane do przekazania do procedury.  
  
2.  Po wywołaniu procedury należy zapisać w normalny sposób prezentowania danych na liście argumentów. Upewnij się, że argumenty odpowiada liście parametrów, w wersjach zdefiniowane w procedurze.  
  
3.  Nie trzeba ustalić, która wersja procedury do wywołania. Visual Basic przekazuje sterowanie do wersji dopasowania listy argumentów.  
  
     Poniższy przykład wywołuje `post` procedury zadeklarowanych w [jak: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md). Uzyskuje identyfikator klienta, określa, czy jest `String` lub `Integer`, a następnie w obu przypadkach wywołuje tę samą procedurę.  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Przeciążanie procedury](./procedure-overloading.md)
- [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)
- [Instrukcje: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Instrukcje: Przeciążanie procedury wykorzystującej parametry opcjonalne](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Instrukcje: Przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)
- [Rozpoznanie przeciążenia](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
