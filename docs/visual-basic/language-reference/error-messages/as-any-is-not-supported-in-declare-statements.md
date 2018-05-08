---
title: '&#39;Jako&#39; nie jest obsługiwany w &#39;Declare&#39; — instrukcje'
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: 34beaeb7178645d5a167d1b7b969bb3e4f500e1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a>&#39;Jako&#39; nie jest obsługiwany w &#39;Declare&#39; — instrukcje
`Any` — Typ danych została użyta z `Declare` instrukcje w Visual Basic 6.0 i starszych wersji, aby zezwolić na stosowanie argumentów zawierających dane dowolnego typu. Przeładowanie, jednak obsługuje Visual Basic i tak powoduje, że `Any` przestarzałe typu danych.  
  
 **Identyfikator błędu:** BC30828  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Deklarowanie parametrów określonego typu, który ma zostać użyty. na przykład.  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  Użyj <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby określić `As Any` podczas `Void*` jest oczekiwane przez procedury wywoływanej.  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Przewodnik: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Tworzenie prototypów w kodzie zarządzanym](../../../framework/interop/creating-prototypes-in-managed-code.md)
