---
title: 'Porady: wywoływanie procedury przeciążenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 802a312d6ec6640594f3c6b662202d1ffcf2376d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649129"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Porady: wywoływanie procedury przeciążenia (Visual Basic)
Zaletą przeciążanie procedury jest elastyczność wywołania. Kod wywołujący można uzyskać informacje potrzebne do przekazania do procedury, a następnie wywołać nazwa jednej procedury, niezależnie od tego, jakie argumentów jest przekazanie go.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Wywoływanie procedury, która ma więcej niż jedną wersję zdefiniowany  
  
1.  Kod wywołujący Określ, które dane do przekazania do procedury.  
  
2.  Wywołanie procedury należy zapisać w normalny sposób prezentowania danych na liście argumentów. Upewnij się, że argumenty odpowiada liście parametrów w wersjach zdefiniowane dla procedury.  
  
3.  Nie trzeba ustalić, która wersja procedury do wywołania. Visual Basic przejmuje kontrolę wersji dopasowania listy argumentów.  
  
     Następujące przykładowe wywołania `post` procedury zadeklarowany w [porady: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md). Uzyskuje identyfikator klienta, określa, czy jest `String` lub `Integer`, a następnie w obu przypadkach wywołuje tę samą procedurę.  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Rozwiązywanie problemów z procedurami](./troubleshooting-procedures.md)  
 [Instrukcje: definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Instrukcje: przeciążanie procedury korzystającej z nieokreślonej liczby parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)  
 [Rozpoznanie przeciążenia](./overload-resolution.md)  
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
