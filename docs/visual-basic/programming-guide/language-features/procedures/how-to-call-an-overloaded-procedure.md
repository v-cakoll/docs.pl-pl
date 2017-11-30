---
title: "Porady: wywoływanie procedury przeciążenia (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff5967c1b09ad59f249297b1cf0a4ed900faf4a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Porady: wywoływanie procedury przeciążenia (Visual Basic)
Zaletą przeciążanie procedury jest elastyczność wywołania. Kod wywołujący można uzyskać informacje potrzebne do przekazania do procedury, a następnie wywołać nazwa jednej procedury, niezależnie od tego, jakie argumentów jest przekazanie go.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Wywoływanie procedury, która ma więcej niż jedną wersję zdefiniowany  
  
1.  Kod wywołujący Określ, które dane do przekazania do procedury.  
  
2.  Wywołanie procedury należy zapisać w normalny sposób prezentowania danych na liście argumentów. Upewnij się, że argumenty odpowiada liście parametrów w wersjach zdefiniowane dla procedury.  
  
3.  Nie trzeba ustalić, która wersja procedury do wywołania. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]formant przechodzi do wersji dopasowania listy argumentów.  
  
     Następujące przykładowe wywołania `post` procedury zadeklarowany w [porady: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md). Uzyskuje identyfikator klienta, określa, czy jest `String` lub `Integer`, a następnie w obu przypadkach wywołuje tę samą procedurę.  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Procedury rozwiązywania problemów](./troubleshooting-procedures.md)  
 [Porady: Definiowanie wielu wersji procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Porady: przeciążanie procedury wykorzystującej parametry opcjonalne](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md)  
 [Rozpoznanie przeciążenia](./overload-resolution.md)  
 [Przeciążenia](../../../../visual-basic/language-reference/modifiers/overloads.md)
