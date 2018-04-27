---
title: 'Porady: wywoływanie procedury przeciążenia (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5eca03de6b6dd2ca2b992196b1ae224f8fbf5068
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
